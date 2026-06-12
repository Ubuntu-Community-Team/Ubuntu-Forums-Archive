---
title: "No sound in Java"
date: 2010-06-21
forum: General Help
---

### Post by Xianath on 2010-06-21
I use a web-based teleconferencing tool that is Java-based (on Linux anyway). At the moment it is completely unusable because there's no sound. Apparently Java tries to open the device directly and this of course doesn't work with PulseAudio. I tried wrapping it in padsp but that didn't do anything. I'm using Sun Java SE 1.6.0_20 64-bit. Any of the so-called alternatives -- gcj, OpenJDK, Cacao, you name it -- won't even load the applet (or any other Java program I've used) so they're not an option. We have a heatwave coming, people will be working from home and I need to stay in touch with my teams. Any ideas how to get this working that don't involve wiping out Ubuntu and installing Windows (also not an option because sound input, i.e. skype, also doesn't work in Ubuntu under VirtualBox).

---

### Post by Mr_Bumpy on 2010-06-21
Hi, are you able to get sound from the following applet?: [http://javaboutique.internet.com/Guitar/]("http://javaboutique.internet.com/Guitar/")

I was able to get the padsp wrapper to work just fine under Lucid (32-bit w/ sun-java6).  I had the problem under Ubuntu Lucid where the sound output from Java apps would conflict with the sound output from other programs.  In other words, I couldn't play an MP3 and get sound output from the Runescape login screen simultaneously.  I did it by following these steps:

1. First, you will need to rename the java executable, and put another command in its place.  Enter the following commands using the terminal:
```
cd /usr/lib/jvm/java-6-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java
```
2. Now, copy and paste the following into the nano editor window, then press CTRL-X to exit and Y to save changes:
```
#!/bin/bash
padsp /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"
```
3. Restart Firefox if it is open, then test the sound.  An easy way is to visit this page: [http://javaboutique.internet.com/Guitar/]("http://javaboutique.internet.com/Guitar/").  Play around with the sounds, and then try to play an MP3 or something on your computer.  While the MP3 is playing, see if you can still hear the guitar sounds when you click on the buttons.

If it works, you may want to lock all of the sun-java6* packages at their current version in Synaptic, otherwise a future Java update may break this hack, and you'll have to do it all over again.

---

### Post by matt-fender on 2010-06-21
> **Mr_Bumpy said:**
> Hi, are you able to get sound from the following applet?: [http://javaboutique.internet.com/Guitar/](http://javaboutique.internet.com/Guitar/)

I was able to get the padsp wrapper to work just fine under Lucid (32-bit w/ sun-java6).  I had the problem under Ubuntu Lucid where the sound output from Java apps would conflict with the sound output from other programs.  In other words, I couldn't play an MP3 and get sound output from the Runescape login screen simultaneously.  I did it by following these steps:

1. First, you will need to rename the java executable, and put another command in its place.  Enter the following commands using the terminal:
```
cd usr/lib/jvm/java-6-sun/jre/bin
sudo mv java java.bin
sudo touch java
sudo chmod +x java
sudo nano java
```2. Now, copy and paste the following into the nano editor window, then press CTRL-X to exit and Y to save changes:
```
#!/bin/bash
padsp /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"
```3. Restart Firefox if it is open, then test the sound.  An easy way is to visit this page: [http://javaboutique.internet.com/Guitar/](http://javaboutique.internet.com/Guitar/).  Play around with the sounds, and then try to play an MP3 or something on your computer.  While the MP3 is playing, see if you can still hear the guitar sounds when you click on the buttons.

If it works, you may want to lock all of the sun-java6* packages at their current version in Synaptic, otherwise a future Java update may break this hack, and you'll have to do it all over again.


Having same problem as topic starter , im on 10.04, when i enter the first terminal command i am receiving an error could not find directory, any ideas on what im doing wrong? lol

---

### Post by Mr_Bumpy on 2010-06-22
Whoops!  I forgot the initial slash in the path name.  Sorry about that!  I have corrected the code in my post.

---

### Post by Xianath on 2010-06-22
I actually used update-alternatives to redirect java to my script before I posted here and web conferencing still didn't work. The applet posted earlier does work, however. In retrospect, I now realize the webconf is an app and not an applet. I'll wrap javaws in padsp and see if that works.

---

### Post by matt-fender on 2010-06-22
Still not having any luck :(

---

### Post by Mr_Bumpy on 2010-06-22
> **matt-fender said:**
> Still not having any luck :(
Matt, my commands only work if you are using sun-java6 instead of openjdk.  Which java version are you using?

---

### Post by matt-fender on 2010-06-22
> **Mr_Bumpy said:**
> Matt, my commands only work if you are using sun-java6 instead of openjdk.  Which java version are you using?


Using sun-java6, seems to be working ok now funnily enough, i think a restart after your commands did the trick! Thanks Mr Bumpy!

---

### Post by Xianath on 2010-06-23
Still no luck, though I did find a workaround (Skype call to the 1-888 number provided). My laptop should be here any time, too, so this issue has lost its urgency for me.

---

### Post by jebradley on 2011-02-25
I was having similar problems with no sound in java. I'd fooled around with it for several months, and thought that I'd look at it again today. I found this article:
[http://www.dh1tw.de/websdr-java-ubuntu-linux-how-to-make-it-work](http://www.dh1tw.de/websdr-java-ubuntu-linux-how-to-make-it-work)
which solved my problem with sound in java.
Hope it helps someone. Good luck.

---

