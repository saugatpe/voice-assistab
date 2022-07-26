# voice-assistab
this helps to your daily work 


import ctypes.wintypes
import time
import winsound
import ecapture
import pyautogui
import pyttsx3
import psutil
import win32
import sys
import operator
import pywhatkit as kit
import pyjokes
import pyaudio
import VideoCapture
import cv2
import speech_recognition as sr
import webbrowser
import wikipedia
import datetime
import requests
import subprocess
import smtplib
import subprocess
import os

engine = pyttsx3.init()

voices = engine.getProperty('voices')
engine.setProperty('voice', voices[3].id)

rate = engine.getProperty('rate')
engine.setProperty('rate', 120)

volume = engine.getProperty('volume')
engine.setProperty('volume', 1.0)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def takecommand():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        speak("Listening....")
        r.pause_threshold = 1
        audio = r.listen(source)
    try:
        print("Recognizing...")
        speak("Recognizing...")
        query = r.recognize_google(audio, language="en_in")
        print(f"You said: {query}\n")
        speak(f"you said: {query}\n")

    except Exception as exception:
        speak("i could not understand.. please say again\n")
        print("i could not understand.. please say again\n")
        return "None"
    return query


if __name__ == "__main__":

    while True:

        query = takecommand().lower()

        if 'open command prompt' in query:
            speak("opening command prompt")
            os.system("start cmd")

        elif 'shutdown' in query:
            speak("i am shut down my self")
            os.system("shutdown /s")

        elif 'restart' in query:
            speak("i am restarting myself")
            os.system("restart /r")

        elif 'logout' in query:
            speak("I am log out myself")
            os.system("logout -l")

        elif 'empty recycle bin' in query:
            winshell.recycle_bin().empty(confirm=False, show_progress=False, sound=True)
            speak("Recycle Bin Recycled")

        elif 'switch the window' in query:
            pyautogui.keyDown("alt")
            pyautogui.press("tab")
            pyautogui.sleep(1)
            pyautogui.keyUp("alt")

        elif 'sleep' in query:
            speak("okay, i am going to sleep you can call me any time")
            sys.exit()

        elif 'open camera' in query:
            speak("opening camera")
            cap = cv2.VideoCapture(0)
            while True:
                ret, img = cap.read()
                cv2.imshow('webcam', img)
                k = cv2.waitKey(50)
                if k == 27:
                    break;
                cap.release()
                cv2.destoryAllWindow()

        elif 'close camera' in query:
            speak("closing camera")
            os.system("Taskkill  /T  /F /IM python.exe")

        elif 'wikipedia' in query:
            speak("searching wikipedia")
            query = query.replace("wikipedia", " ")
            result = wikipedia.summary("query", sentences=2)
            speak("According to wikipedia")
            speak(result)

        elif 'close wikipedia' in query:
            speak("closing the wikipedia")
            os.system("TASKKILL /F /T /IM msedge.exe")

        elif 'search' in query or 'play' in query:

            query = query.replace("search", "")
            query = query.replace("play", "")
            webbrowser.open(query)

        elif 'close search' in query:
            speak("closing the search")
            os.system("TASKKILL /T /F /IM msedge.exe")

            # web application in the voice command:
        elif 'open google' in query:
            speak("Opening google")
            cm = takecommand().lower()
            webbrowser.open(f"{cm}")

        elif 'close google' in query:
            speak("closing google")
            os.system("TASKKILL /F /T /IM msedge.exe")

        elif 'open facebook' in query:
            speak("opening facebook")
            webbrowser.open("facebook.com")

        elif 'close facebook' in query:
            speak("closing facebook")
            os.system("TASKKILL /F /T /IM msedge.exe")

        elif 'open youtube' in query:
            speak("opening youtube")
            webbrowser.open("youtube.com")

        elif 'close youtube' in query:
            speak("closing youtube")
            os.system("TASKKILL /F /T /IM msedge.exe")

        elif 'open stackoverflow' in query:
            speak("opening stackoverflow")
            webbrowser.open("stackoverflow.com")

        elif 'close stackoverflow' in query:
            speak("closing stackoverflow")
            os.system("TASKKILL /F /T /IM msedge.exe")

        elif 'song on youtube' in query:
            speak("what do you want to listen")
            kit.playonyt("metallica")

        elif 'close song' in query:
            speak("closing song on youtube")
            os.system("TASKKILL /F /T /IM msedge.exe")

        elif 'joke' in query:
            joke = pyjokes.get_joke()
            speak(joke)

        elif 'open code' in query:
            speak("opening visual stdio code")
            path = r"C:\Users\sauga\Downloads\Programs\VSCodeUserSetup-x64-1.68.1.exe"
            os.startfile(path)

        elif 'close path' in query:
            speak("closing visual code")
            os.system("TASKKILL /F /T /IM Code.exe")

        elif 'open chrome' in query:
            speak("opening chrome")
            path = r"C:\Program Files\Google\Chrome\Application\chrome.exe"
            os.system(path)

        elif 'close chrome' in query:
            speak("closing chrome")
            os.system("TASKILL /F /T /IM chrome.exe")

        elif 'open dev' in query:
            speak("opening dev c++")
            path = r"C:\Users\sauga\Desktop\c program\Dev-Cpp\devcpp.exe"
            os.system(path)

        elif 'close dev' in query:
            speak("closing dev c++")
            os.system("TASKKILL /F /T /IM devcpp.exe")

        elif 'open cisco' in query:
            speak("opening cisco")
            path = r"C:\Program Files\Cisco Packet Tracer 8.1.1\bin\PacketTracer.exe"
            os.system(path)

        elif 'close cisco' in query:
            speak("closing cisco")
            os.system("TASKKILL /F /T /IM PacketTracer.exe")

        elif 'open nmap' in query:
            speak("opening nmap")
            path = r"C:\Program Files (x86)\Nmap\zenmap.exe"
            os.system(path)

        elif 'close nmap' in query:
            speak("closing nmap")
            os.system("TASKKILL /F /T /IM zenmap.exe")

        elif "send email to saugat" in query:

                speak("What should i say?")
                query = takecommand().lower()
                if "send file" in query:
                    email = "your@gamil.com"
                    password = "your_password"
                    send_to_email = "your person@gmail.com"
                    speak("what is the subject for this email")
                    query = takecommand().lower()
                    subject = query
                    speak("what is the message for this email")
                    query2 = takecommand().lower()
                    speak("please enter the correct path for this email from shell")
                    file_location = input("enter the path here: ")

                    speak("please wait, i am sending the email")

                    msg = MIMEMultipart()
                    msg['from'] = email
                    mgs['to'] = send_to_email
                    msg['subject'] = subject

                    msg.attach(MIMEText(message, 'plain'))

                    file_name = os.path.basename(file_location)
                    attachment = open(file_location, "rb")
                    part = MIMEBase('application', 'octet-stream')
                    part.set_payload(attachment.read())
                    encoders.encode_base64(part)
                    part.add_header('content-Disposition', "attachment; filename= %s" % filename)

                    msg.attach(part)

                    server = smtplib.SMTP("smtp.gmail.com", 587)
                    server.ehlo()
                    server.login(email, password)
                    text = msg.as_string()
                    server.sendmail(email, send_to_email, text)
                    server.quit()
                    speak("email has been send to saugat")

                else:
                    email = "your@gmail.com"
                    password = "your_password"
                    send_to_email = "person@gmail.com"
                    message = query

                    server = smtplib.SMTP("smtp.gmail.com", 587)
                    server.starttls()
                    server.login(email, password)
                    server.sendmail(email, send_to_email, password)
                    server.quit()

                    speak("email has been send to saugat")

        elif 'hello' in query:
            speak("hi,how can i help you")

        elif 'hi' in query:
            speak("hello,how can i help you")






               

















