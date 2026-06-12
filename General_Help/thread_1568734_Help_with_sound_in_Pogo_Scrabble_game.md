---
title: "Help with sound in Pogo Scrabble game"
date: 2010-09-05
forum: General Help
---

### Post by jondecker76 on 2010-09-05
Hello. I am running Ubuntu 10.04 32 bit.
Sound was not working while playing Scrabble on Pogo.com. I did some searching, and uninstalled the iced-tea plugin and installed Java 6.

Now, when I go to the game, only the first sound of every screen works.  I'd really like to get all of the sounds to work as they should (before my wife drives me crazy about it). Again, by moving from Iced-tea plugin to the real java plugin, I did gain "some" sound - but once the first sound plays from each screen of the game, no other sounds in the game work after that.

Any ideas?

thanks

---

### Post by lykeion on 2010-09-06
Yes, there are problems with sound in Java applets in Ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/415614](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/415614)

I found this work-around (haven't tested it myself):
[http://www.tuxyturvy.com/blog/index.php?/archives/66-Making-Sun-Java-1.6-play-via-PulseAudio.html](http://www.tuxyturvy.com/blog/index.php?/archives/66-Making-Sun-Java-1.6-play-via-PulseAudio.html)

If you want to have a go and report if it works it'd be great.

EDIT:
Just tested this and it didn't work for me.
Tried to open a Java applet and Java freezed, so I can't recommend this solution.

If anyone else have some fixes to resolve sound issues for Java applets please post.

---

### Post by jondecker76 on 2010-09-12
I finally got it working and figured I would post it here so others can get their sound working correctly on Pogo! (With Ubuntu 10.04)

1) Uninstall IcedTea, and install Java 6 (there are plenty of tutorials out there on this)

2) Navigate to /usr/lib/jvm/java-6-sun/jre/bin
   rename the java executable to java.bin:
   ```

   cd /usr/lib/jvm/java-6-sun/jre/bin
   sudo mv java java.bin
   
```
3) Make a new "dummy" java binary, and make it an executable script:
   ```

   sudo touch java
   sudo gedit java
   
```
   At this point, enter the following into the text editor (NOT the terminal!) and save it:
   > 
   #!/bin/bash
   padsp /usr/lib/jvm/java-6-sun/jre/bin/java.bin "$@"
   
   then, make sure to make it executable:
```

   sudo chmod +x java

```
4) Now for this to work, you have to remove a certain sound library. We will simply rename it so that you could restore it later if you need to:
   ```

   cd /usr/lib/jvm/java-6-sun/jre/lib/i386
   sudo mv libjsoundalsa.so libjsoundalsa.so.rename
   
```
5) All done!  Your pogo games should now have working sound!

---

### Post by claven123 on 2010-10-20
I'm a bit confused on some of your directions.

I too have the same issue, but I do get some sound in the pogo games.  Sometimes I get the background noise and no 'action' noise.  Other time I get the action noise and no background.  And other times different  noises....

Will this work with ubuntu 10.10?

#3
Do I type each of these commands in terminal one at a time then hit enter and then the next line and hit enter?

Once I enter the text into the text editor and save it, what do I do with it?

Will this affect the pogo games play, I had to do a bit of work to get the pogo games to work in the first place.

Thanks for any and all help

---

### Post by fastcrab on 2010-10-20
Confirmed! Using the pulse audio wrapper as described by jondecker76 makes pogo sound work on Firefox on maverick.

Thank you for the details.

---

### Post by oboedad55 on 2010-10-23
> **fastcrab said:**
> Confirmed! Using the pulse audio wrapper as described by jondecker76 makes pogo sound work on Firefox on maverick.

Thank you for the details.

I have to add my thanks as well. I'm running Maverick amd64 and fixed the java sound problem with the above fix. One minor note; the jre lib directory for 64 bit systems is /adm64 and not /i386.

---

### Post by ggordon on 2011-11-30
This worked for me on Natty.  However, I am using 64 bit, so I had to go to the /amd64 directory instead of /i386 to remove the sound library.

Sound had been working for me in Lucid, but then I upgraded directly to Natty and lost my sound.  I was about to give up on Pogo, but now I'm back to my fun.  \\:D/

Thank you jondecker76

---

