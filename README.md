- 👋 import speech_recognition as sr
import pyttsx3
import datetime

# Initialize the speech recognizer
recognizer = sr.Recognizer()

# Initialize the text-to-speech engine
engine = pyttsx3.init()

# Function to speak text
def speak(text):
    engine.say(text)
    engine.runAndWait()

# Function to listen for commands
def listen():
    with sr.Microphone() as source:
        print("Listening...")
        recognizer.adjust_for_ambient_noise(source)
        audio = recognizer.listen(source)

        try:
            print("Recognizing...")
            command = recognizer.recognize_google(audio).lower()
            print("You said:", command)
            return command
        except sr.UnknownValueError:
            print("Sorry, I didn't get that.")
            return ""
        except sr.RequestError:
            print("Sorry, I couldn't request results at the moment.")
            return ""

# Function to execute commands
def execute_command(command):
    if "time" in command:
        current_time = datetime.datetime.now().strftime("%I:%M %p")
        speak(f"The current time is {current_time}")
    elif "date" in command:
        current_date = datetime.datetime.now().strftime("%B %d, %Y")
        speak(f"Today's date is {current_date}")
    elif "joke" in command:
        speak("Why don't scientists trust atoms? Because they make up everything!")
    elif "stop" in command:
        speak("Goodbye!")
        exit()
    else:
        speak("Sorry, I don't understand that command.")

# Main loop
speak("Hello! How can I help you today?")
while True:
    command = listen()
    execute_command(command)Hi, I’m @nurnuhash
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
nurnuhash/nurnuhash is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
