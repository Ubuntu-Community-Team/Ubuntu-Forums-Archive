---
title: "M3U Playlist generator using LS"
date: 2010-07-18
forum: General Help
---

### Post by aeronotix on 2010-07-18
I am trying to emulate a .bat file I have on Windows.

The script turns all the mp3 files into a m3u file.

So far I have found the command "ls -1 >playlist.m3u *.mp3" this works great but what I want is to drag a file into the folder an album is in and then double click and it will run the command. 

I tried making a launcher and put that command on it, it seems to open up a terminal window but no playlist.m3u is generated.

Could you tell me what I am doing wrong?

---

### Post by lkjoel on 2010-07-18
> **aeronotix said:**
> I am trying to emulate a .bat file I have on Windows.

The script turns all the mp3 files into a m3u file.

So far I have found the command "ls -1 >playlist.m3u *.mp3" this works great but what I want is to drag a file into the folder an album is in and then double click and it will run the command. 

I tried making a launcher and put that command on it, it seems to open up a terminal window but no playlist.m3u is generated.

Could you tell me what I am doing wrong?
```
ls -1 *.mp3 > playlist.m3u
```
It was in the wrong order.

---

### Post by aeronotix on 2010-07-18
Nope that doesn't do it.

Maybe I'm making the launcher wrong?

I right-click the desktop and hit create Launcher and then add ls -1 *.mp3 > playlist.m3u to the command line, check "Run in terminal" and then hit create. That's right, no?

---

### Post by lkjoel on 2010-07-18
> **aeronotix said:**
> Nope that doesn't do it.

Maybe I'm making the launcher wrong?

I right-click the desktop and hit create Launcher and then add ls -1 *.mp3 > playlist.m3u to the command line, check "Run in terminal" and then hit create. That's right, no?
Nope!
Well I don't think so.
Try instead of adding ls -1 *.mp3 > playlist.m3u, try adding "ls -1 *.mp3 > playlist.m3u" (with quotes)
And if that doesn't work, make a file named m3uize.sh, and add the contents of:
```
#!/bin/bash
ls -1 *.mp3 > playlist.m3u
```

---

### Post by aeronotix on 2010-07-20
How do I create the .sh file?

I'm really sorry for all this :(

---

### Post by lkjoel on 2010-07-20
Simple!
Open up a text editor (such as gedit) then copy and paste this code in it:
```
#!/bin/bash
ls -1 *.mp3 > playlist.m3u
```Then click on save, and in the filename part, say: "m3uize.sh", and click on save.
Then in a Terminal (Applications->Accessories->Terminal) window type:
```
chmod +x ./m3uize.sh
./m3uize.sh
```
And with Terminal Enhancements installed, you only need to type:
```
chmod +x m3uize.sh
m3uize.sh
```

---

