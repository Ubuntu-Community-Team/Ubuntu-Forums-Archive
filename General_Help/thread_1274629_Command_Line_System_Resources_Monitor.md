---
title: "Command Line System Resources Monitor?"
date: 2009-09-24
forum: General Help
---

### Post by Swift_gti on 2009-09-24
Hi All,
 
First post here, just getting into Linux - been playing with Ubuntu for a few weeks and loving it so far! :)
 
I am a little stuck with one thing I'm trying to do though, basically I want to remotely monitor the following resources for the Ubuntu box from another PC running Windows;
CPU Usage (Total), Memory Usage (Total), Disk Free/Used Space, Network Interface Total In / Out.
 
Now after a little googling I see I can get the various info via top, iftop etc.. but I would like to automate this so that the readings are updated every 10 seconds or so.
If I can get the data to output to a simple text file then I could access this over the network and make a small program to parse and display this on the Windows PC.
 
So my question is, how to automate it and output just the bits I need ?
OR
Is there a better app / way of getting this info out to a file ?
 
Cheers!

---

### Post by bboston7 on 2009-09-24
```
top -d 10.00
```
This will refresh top every 10 seconds.

As far as logging this to a file, you could try
```
top -d 10.00 > top_log
```

However, this will get long fast.

for use with Windows, you'll want to log to something.txt rather than leave out the .txt

---

### Post by redmk2 on 2009-09-24
> **Swift_gti said:**
> ...
Is there a better app / way of getting this info out to a file ? 

Run htop in Putty (ssh for windows).

---

### Post by Swift_gti on 2009-09-25
Thanks for the suggestions.
Something like the top -d command would work if there is anything that will do CPU, Mem, Disk and Network.
I don't need any log as such so if there is a way to have it pipe the output to a file (overwriting the contents) each time then that would rock.
 
htop looks pretty cool but doesn't include network or disk as far as i can see.. 
 
I should mention I don't run any X11 on this machine so it will have to be something that works from cli.
Conky looks good if I could put the output to a file, but that appears to require X..
 
Edit - Oooh just found a packge named conky-cli.. looks interesting :D

---

### Post by Swift_gti on 2009-09-25
The conky package does the job, just compiled the latest version which has options in the config to support output to command line without any dependency on x11.
 
I can output this to a file fine by launcing 'conky -d > outfile.txt'
But obviously it appends at each update.. is there any way to overwrite in this situation instead of append ?

---

