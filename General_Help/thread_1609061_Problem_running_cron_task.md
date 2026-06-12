---
title: "Problem running cron task"
date: 2010-10-29
forum: General Help
---

### Post by rmcellig on 2010-10-29
I am using the GUI app Scheduled Tasks to run my jobs. For some reason, my task doesn't run at all.

arecord -t wav -f cd -d 123 /home/randy2/Desktop/filename.wav. I also have problems when I press the Add button. Nothing happens.

Looks OK to me. I am running 10.10

---

### Post by trikster_x on 2010-10-30
Hmm, the syntax is definitely correct.  Maybe have it output to a log file by adding:
```
> /path/to/file.log
```

to the end of your command, then post the results.  Also, just because you didn't mention it, did you run the command from terminal to make sure it works correctly?  

This may also be a problem with the GUI program.  Have you tried using crontab through the terminal?

---

### Post by rmcellig on 2010-10-30
This is the error I get from the command line:

randy2@ubuntu:~$ arecord -t wav -f cd -d 123 /home/randy2/Desktop/filename.wav/path/to/file.log
Recording WAVE '/home/randy2/Desktop/filename.wav/path/to/file.log' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
/home/randy2/Desktop/filename.wav/path/to/file.log: Not a directory
randy2@ubuntu:~$

---

### Post by matt_symes on 2010-10-30
Hi

No he meant...

arecord -t wav -f cd -d 123 /home/randy2/Desktop/filename.wav > /home/randy2/Desktop/file.log

redirecting any output to the log file on your Desktop called file.log.

Open a terminal and type

arecord -t wav -f cd -d 123 /home/randy2/Desktop/filename.wav

and see if it returns any errors. Post the results here.

Kind regards

---

### Post by trikster_x on 2010-10-30
> **rmcellig said:**
> This is the error I get from the command line:

randy2@ubuntu:~$ arecord -t wav -f cd -d 123 /home/randy2/Desktop/filename.wav/path/to/file.log
Recording WAVE '/home/randy2/Desktop/filename.wav/path/to/file.log' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
/home/randy2/Desktop/filename.wav/path/to/file.log: Not a directory
randy2@ubuntu:~$

Sorry, I should have made it clear that there should be a single space before the ">", my fault.

I ran the command in my own terminal, and didn't run into any problems.  When I put it into crontab the program worked fine.  I think your problem is stemming from the GUI you are using messing up while inputing a long string into crontab.  

You can use crontab directly by typing in a terminal:
```
crontab -e
```
The first time you use this, you may have to select a text editor.  I use nano, but you can use whatever you like.

[http://www.crontabrocks.org/]("http://www.crontabrocks.org/") Check this out for a rundown of how crontab is used.  I'll show you two methods for doing what you want. The first is a basic method to just get the program going:
```
crontab -e
```
opens the crontab editor
```
30 * * * * arecord -t wav -f cd -d 123 /home/randy2/Desktop/filename.wav
```
is the code you enter into the crontab editor.

This runs your crontab on minute 30 of every hour.  Simple and effective, but if an error occurs, you have no idea when or for what reason.  That is where the second method comes in.

Start by creating a text file.  Name it whatever you think is appropriate, I am using test.sh for this example.  The ".sh" extension just makes it easier to see that it is a shell script.  In the file, add this line of text:
```
date && arecord -t wav -f cd -d 12 /home/randy2/Desktop/filename.wav
```
Now make the file executable by doing right-click>>properties>>permissions and check the make executable box.  Open crontab again:
```
crontab -e
```
Then use this for the command in crontab:
```
29 13 * * * /path/to/test.sh >> /home/randy2/Desktop/test.sh.log 2>&1
```
Make sure that it isn't line wrapped, then exit and save.  Now your command runs on minute 30 every hour, and  adds a time-stamp and any stdout or stderr to the file "test.sh.log".  The end of the log file will simply be amended to add the newest date and info, while preserving any other entries.  

If you want the log file to be over-written every time the crontab runs, then remove one of the ">" before the log file-path.  You can work some other magic with it using a script with various commands and another crontab entry, but I'll leave that for you to explore :P  Half the fun of linux is learning how to manipulate your system with the command line rather than a GUI:D

Change any file path to suit your needs, and you should be good to go.  And if you want the sound file to display the date/time in the filename, insert this before the .wav file extension in the arecord command:
```
`date +%Y-%m-%d--%k:%M`
```
There are tick marks at the beginning and end that are very hard to see, but they do need to be included for the code to work.  

I'll sub to this thread, so if you get any errors or have a question, post and I'll see if I can help you get it figured out.

---

