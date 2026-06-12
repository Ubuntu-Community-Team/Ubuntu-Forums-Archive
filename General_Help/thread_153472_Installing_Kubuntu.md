---
title: "Installing Kubuntu"
date: 2006-04-01
forum: General Help
---

### Post by FrustratedGuy on 2006-04-01
Hello, everyone.

I am currently using Microsoft Windows XP Service Pack 2. I have partitioned my 200 GB hard drive; My second, empty drive is 90 GB. I have downloaded an .iso kubuntu installation and extracted the files. However, I cannot see a way to install the OS. How do I do this if there's no .exe files?

---

### Post by niviche on 2006-04-01
The .iso file is a perfect image to be burned onto CD-Rom. You should not extract it.

Refer to the wiki page [How to burn an iso](https://wiki.ubuntu.com/BurningIsoHowto) to use it. You might have to download a free program such as ISOrecorder.

Once this CDR is burned, you are ready to install Kubuntu. I would however recommend you to read [this guide](http://www.mrbass.org/linux/ubuntu/install/) to see what is expecting you, and what to do during the installation.

Good luck and have fun with Kubuntu.

---

### Post by FrustratedGuy on 2006-04-01
Hello,

I've downloaded ISO Recorder, but when I execute the program, nothing happens. Did I do something wrong? I've repaired the installation and all several times.

---

### Post by niviche on 2006-04-01
Weird.

What program do you use to burn CDs? If you have Nero, you can use it as well.

According to [this Wikipedia entry](http://en.wikipedia.org/wiki/Iso_file), you could also use UltraISO to burn this CDR.

---

### Post by nickle on 2006-04-01
you simply put the ISO disk in you machine and boot from there. If the ISO is ok it should start the install dailogue....

---

### Post by FrustratedGuy on 2006-04-02
I used DeepBurner to burn the ISO onto the disk. After that, I booted from the CD. I got a screen that says KUBUNTU, and it said, "for a base install, type 'server' and press ENTER. For a full install, press ENTER". Basically, anyway. I hit enter, but nothing happened. I waited about 5 minutes. Then I realized the prompt wasn't flashing.

This happens every time. I've tried this for about 6 attempts. I'm getting much more frustrated, and I'm already tired (It's 10:20 PM in my time zone), so I just gotta ask: What am I doing wrong?

---

### Post by Barrakketh on 2006-04-02
You may want to try asking [here](http://www.ubuntuforums.org/forumdisplay.php?f=94).

---

### Post by niviche on 2006-04-02
There are a few things that might have gone wrong.

First, the iso might not have been burned right. What burning speed did you use? You might want to burn another CDR, slowly, and see if it helps.

Then, which installation files did you download? The ones for i386, for 64bits, or yet another one?
On which machine are you trying to install Kubuntu? Is it a desktop computer or a laptop?

I am sorry that it didn't work the first time. Another thing to do would be to download the live CD and use it on your machine. It would not install Kubuntu on your hard drive, but test if everything works, and shows you what's awaiting you. :)

---

### Post by FrustratedGuy on 2006-04-02
I burned at 10x.

I downloaded the i386. I do have a AMD Athlon 64 processor - should I download for it?

I am using a custom-built desktop.

---

### Post by niviche on 2006-04-02
[QUOTE=FrustratedGuy]I downloaded the i386. I do have a AMD Athlon 64 processor[/QUOTE]

This might be the problem.
Go back to [the download page](http://www.ubuntu.com/download), click on your location, and download the ISO for "64-bit PC (AMD64)". The one for i386 is made for other kinds of processor.

---

### Post by FrustratedGuy on 2006-04-02
I am downloading it. But it's late; I need to get to my bed. I'll let the compy download while I sleep. :)

---

### Post by niviche on 2006-04-02
Good night, and good luck (wow, advertising for movies on the Ubuntu forums, who would have thought of this?:)).

---

### Post by FrustratedGuy on 2006-04-02
Hello, anyone awake out there? ;)

Unable to leave a problem, I've gone without sleep downloading this. I finally got it, and... I'm stuck in the same location. Has this happened to anyone else? I mean, no amout of patience causes progress on this thing. =/

---

### Post by FrustratedGuy on 2006-04-02
I'm sorry to bump this thread; I don't want to be a pest. But I finished downloading the 64-bit Kubuntu Linux. I opened DeepBurn, selected "Burn an ISO image" and changed the speed from "Max" to 10x. Under Additional Parameters I was able to choose Simulation, Write, or both. I chose only Write. I then burned it. Is there a fault in my methods?

I am installing the Nero OEM suite, if it helps anything.

OK, I'm going to test to see if it's me or if I have a faulty download. I'm downloading a copy of VectorLinux. If the install begins to work, I'll know what the culprit is. If it doesn't... same thing. But I do really really want Kubuntu. :D

---

### Post by FrustratedGuy on 2006-04-02
OK. I tried to install VectorLinux and it froze at the same place. At this point, I know it cannot be the download. It's me. Maybe I am breaking some rule about burning these image files, or something, but I'm getting rather frustrated...

---

### Post by gingermark on 2006-04-02
When you say you've got stuck at the same point, do you mean during the actual installation of the OS, or during the burn process in Windows?

Without making you go "Arrrgh" I should also add that you CAN use the x86 version on AMD64 architecture - I do so myself. I'd recommend it in fact as at this point it is problematic getting some proprietary stuff to work for the 64 bit version (like Flash, Windows media stuff etc).

I'm not really sure what could be wrong. If you've checked the md5 sum matches then there was nothing wrong with your download. And burning at the lowest possible speed should ensure the disc is copied properly.

Worst case scenario maybe you can use a friend's computer to burn the install disc. Sorry I can't be more help, but helpiing people in Windows is no longer one of my strong points! :)

---

### Post by FrustratedGuy on 2006-04-02
Alright, I got the setup to get going. Kind of. I am installing the AMD64 version. I read that I need the ext3 journal... thing... file system, so I set my 90GB partition to that file system and formatted it. I'm getting this error:

No root file system is defined.

Please correct this from the partitioning menu.

OK, I'm on my sister's compy typing this; how do I correct this?

EDIT: I deleted the (empty) partition and it's installing the base system now. I'll let you know if anything happens. :)

EDIT AGAIN: Something did happen; I successfully installed Kubuntu Linux AMD64. I guess I'll take the rest of my questions (they will abound, I'm sure) into the AMD forum.

---

