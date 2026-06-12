---
title: "Problem running the commands in the terminal."
date: 2010-04-11
forum: General Help
---

### Post by austin8868 on 2010-04-11
Hello, i am trying to boot debian on my nexus one the guide i am using is telling me to run these commands

$ adb remount

$ adb install vnc.apk

$ adb install swapper.apk

$ adb shell

# cd /sdcard/debian

# su

# sh ./debian.sh

# exit (repeat until out of adb)

I am getting to the point where i type the command # cd /sdcard/debian but it tells me cd: can't cd to /sdcard/debian. Anyone know what i am doing wrong? Thanks...

---

### Post by akakingess on 2010-04-11
Are you running Debian or Ubuntu??? Let me know that and maybe I can assist.

---

### Post by Skidbladnir on 2010-04-11
* Points at "[ubuntu] Problem running the commands in the terminal." *

---

### Post by lisati on 2010-04-11
From [http://ubuntuforums.org/showthread.php?t=1413313](http://ubuntuforums.org/showthread.php?t=1413313) :

> Copy bootdeb, debian.img, debian.sh, mountonly, fsrw, uninonfs to /sdcard/debian/ on the phone (make the directory if needed)
It sounds like there was a problem with this step that you might have missed.

---

### Post by austin8868 on 2010-04-11
> **lisati said:**
> From [http://ubuntuforums.org/showthread.php?t=1413313](http://ubuntuforums.org/showthread.php?t=1413313) :


It sounds like there was a problem with this step that you might have missed.
I made the folder named Debian on the sd card and put the correct files in it.... I am running ubuntu

---

### Post by akakingess on 2010-04-11
> **austin8868 said:**
> I made the folder named Debian on the sd card and put the correct files in it.... I am running ubuntu

I am just shooting in the dark here, but could it have something to do with the mount point for the SD Card (haven't used one within Ubuntu, yet), so maybe you need to include the entire path for the mount point of the Card? Just a guess, and trying to help all brainstorm a little.

---

### Post by renkinjutsu on 2010-04-11
you made the directory Debian, but your command was to sh into /sdcard/debian.. try changing the name from Debian to debian.. i'm not really sure if case matters in this case since the sdcard is formated with FAT

---

### Post by austin8868 on 2010-04-11
> **akakingess said:**
> I am just shooting in the dark here, but could it have something to do with the mount point for the SD Card (haven't used one within Ubuntu, yet), so maybe you need to include the entire path for the mount point of the Card? Just a guess, and trying to help all brainstorm a little.
I am new to ubuntu, so could you tell me how to do that? i just click mount usd on my phone and it mounts for me...

---

### Post by austin8868 on 2010-04-11
> **renkinjutsu said:**
> you made the directory Debian, but your command was to sh into /sdcard/debian.. try changing the name from Debian to debian.. i'm not really sure if case matters in this case since the sdcard is formated with FAT
I think ubuntu is case sensitive so that might be the problem, let me try that...

Nope i tried that and it still give me the same problem

---

### Post by austin8868 on 2010-04-11
Anyone? I am leaving for vacation tomorrow and would really like to get this working before i leave.

---

### Post by akakingess on 2010-04-11
> **austin8868 said:**
> I am new to ubuntu, so could you tell me how to do that? i just click mount usd on my phone and it mounts for me...

Linux/Ubuntu mounts everything via a mount point, be it a CD, drive, etc. These are located within the filesystem under the 'mnt' directory I believe (I hope someone corrects me if/when I am wrong), so you could create a folder (need to be root to do this, either with sudo, or use gksu nautilus to launch file browser with root privileges, but be careful) within the mnt directory and have your SD Card mount to that point everytime and maybe that will straighten some things out. I am short on time otherwise I would find the link within Ubuntu's online help for you, or you could do a 'mount man' to see what options it gives you. I will check back in when done shuffling kids around to 2 different birthday parties and a music/singing lesson. Good Luck!!!

Sorry, here is 1 link that may help you out, so check [here]("http://manpages.ubuntu.com/manpages/hardy/man1/fs_mkmount.1.html") and see if that sheds some light on the subject.

---

### Post by austin8868 on 2010-04-11
> **akakingess said:**
> Linux/Ubuntu mounts everything via a mount point, be it a CD, drive, etc. These are located within the filesystem under the 'mnt' directory I believe (I hope someone corrects me if/when I am wrong), so you could create a folder (need to be root to do this, either with sudo, or use gksu nautilus to launch file browser with root privileges, but be careful) within the mnt directory and have your SD Card mount to that point everytime and maybe that will straighten some things out. I am short on time otherwise I would find the link within Ubuntu's online help for you, or you could do a 'mount man' to see what options it gives you. I will check back in when done shuffling kids around to 2 different birthday parties and a music/singing lesson. Good Luck!!!

Sorry, here is 1 link that may help you out, so check [here]("http://manpages.ubuntu.com/manpages/hardy/man1/fs_mkmount.1.html") and see if that sheds some light on the subject.
Oh alright thank you, i have logged in as root but im not so sure on how to get the sdcard to mount to the mnt directory. So if someone could give me the command or tell me how that would be great. Sorry for all the noob questions here...

---

### Post by akakingess on 2010-04-11
Check out the link that I put at the very end and that should help you to figure it out.

---

### Post by austin8868 on 2010-04-11
> **akakingess said:**
> Check out the link that I put at the very end and that should help you to figure it out.
Im reading it but its not making alot of sense to me, i will mess around with it some and see if i can get it to work.

---

### Post by akakingess on 2010-04-11
When I get more time I will try to walk you through it unless someone else would be kind enough to do so :)

---

### Post by austin8868 on 2010-04-11
> **akakingess said:**
> When I get more time I will try to walk you through it unless someone else would be kind enough to do so :)
:) thank you

---

### Post by austin8868 on 2010-04-11
I have been messing around with it and trying to figure out how to do it from the tutorial that the guy above me posted with no luck :confused:

---

### Post by 3rdalbum on 2010-04-11
Rather than try to get the card mounted at the specific location /sdcard/, why don't you go into /media with your file browser, and find exactly where it is mounted, and put that into the command?

---

### Post by akakingess on 2010-04-11
Thanks 3rdalbum, apparently I was on a different wavelength altogether, I knew I could count on you to correct/help me out ;)

---

### Post by austin8868 on 2010-04-11
> **3rdalbum said:**
> Rather than try to get the card mounted at the specific location /sdcard/, why don't you go into /media with your file browser, and find exactly where it is mounted, and put that into the command?
I did that and it mounts at DF50-5AEF where ever that is, but i put it into the terminal as cd /DF50-5AEF/debian and got the same results as before... This wouldn't happen to be using fastboot would it?

---

### Post by austin8868 on 2010-04-11
I don't know what to do guys, i have tried everything i can think of and everything you all have recommended. Looks like im going to have give up on this one. Thanks for helping me everyone...

---

