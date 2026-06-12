---
title: "compiz and ATI"
date: 2010-06-14
forum: General Help
---

### Post by hotnikkelz on 2010-06-14
I have an AMD x3 720 with an HD 4870 card nad i experience lag when i use compiz. Especially with maximising and minimising windows. I've searched and tried a few of the workarounds, but they didn't work for me, I'm still getting the lag. Can anyone help me with this?

---

### Post by Talon2 on 2010-06-14
What version of Ubuntu are you using?

I have an ATI 4350 card that works well with Ubuntu 10.04 using the included open source driver.

---

### Post by TheDesertDragon on 2010-06-14
If you use the open source drivers then that's understandable.
If you use FGLRX, it really isn't, as it's actually the best driver for doing it, so I absolutely recommend you get 10.5. (As weird/amazing as it may sound)

Installing is rather simple:

Remove your current driver from Hardware Drivers.

Download from ati.amd.com

sudo sh "insertfilenamehere"

Follow the on-screen instructions.

Open the terminal again and type:

aticonfig --initial -f

---

### Post by hotnikkelz on 2010-06-14
using lucid lynx

desertdragon, by 10.5 you're referring ATI's catalyst 10.5? If so I will attempt to install and report if it worked. Thanks for the help :)

---

### Post by TheDesertDragon on 2010-06-14
I am.

Phoronix recently released test results showing that games running on ATi hardware loses at most 1 FPS in nearly every game, and I experience roughly the same. With Compiz-Fusion and Emerald, I have 4 hours of batterylife. (Barely 3 hours on Windows 7)

Doesn't really need more explanation than that! :P Great driver at this point, though sometimes a bit buggy. I hope it works for you.

---

### Post by hotnikkelz on 2010-06-14
That's impressive. I'm uninstalling ubuntu 32 bit, so i can install the 64 bit version instead.
You experience no lagging in compiz with these drivers? THat's good news. I'm still struggling to learn this OS, the commands make my head spin.

---

### Post by TheDesertDragon on 2010-06-14
A quick correction:
Remember to type 
sudo aticonfig --initial -f
or it won't do anything! :P

Really commands are only needed in Linux when you need something done as admin which you unfortunately do quite a bit still, which is a shame. Windows is really great at prompting you to enter your admin password. Linux will instead just throw an exception and the program won't run, so you have to use commands. It's not really that nice! =(

I can give you a quick introduction to some useful features of this:
sudo stands for super user do. It makes you a superuser (ie. prompts you to enter a password after which it allows you to make changes outside your home folder). sudo can be used with any command.
gksu is a contraction of gtk superuser, which basically, rather than putting a terminal in your face with a password prompt, asks you with a nice graphical overlay much like in Windows 7.
sudo -i makes you admin for all commands coming in the terminal after the sudo -i command. If you need to do a series of commands that normally require admin priviliges you can use sudo -i instead of writing sudo for every command.
Hitting F2, then 'gksu nautilus' allows you to get a filebrowser with admin rights after entering a password promps, allowing you to move files and folders around without the use of cp, rm, mv, ls, cd etc. etc.

---

### Post by techunit on 2010-06-14
HI Installed the Driver Hoping To Avoid the Unplessentries of the ATI driver found in the Hardware Drivers App but found it cause the same problems I can't go into standby and my boot splash is at a low resolution! Can anyone help it is a tough question I know but it would help.

---

### Post by hotnikkelz on 2010-06-14
hmm desertdragon i thhnk you lost me there lol, i'm really really newb at this.

I downloaded the package, it has a run extension, but i can't actually install it cuz i need to sudo it, but...where do i type the command you mentioned? I know it's in terminal, i mean how wil the command know that i want to install that particular file, am i not supposed to mention the file somewhere in the command? i'm not sure how that works

techunit:
I had that low res boot splash as well with the 32 bit, and when i installed 64 bit, i don't get it anymore. Strange.

---

### Post by hotnikkelz on 2010-06-15
I was able to install the drivers by browsing to teh direction of the run file, and typing sudo sh 'name of file'

However i got some errors, and it basically didn't work lol. It's weird though, ubuntu prompts me to install proprietary drivers and recommened to install their option. I ignored them and installed the version i downloaded = fail. Their drivers work, but i get lag. So i uninstalled ubuntu to try and start from fresh. I'm wondering if i should download the 'restricted' package first before i install my version of catalyst. *sigh* so much stress
Thank the heavens for wubi :)

---

### Post by TheDesertDragon on 2010-06-16
> **techunit said:**
> HI Installed the Driver Hoping To Avoid the Unplessentries of the ATI driver found in the Hardware Drivers App but found it cause the same problems I can't go into standby and my boot splash is at a low resolution! Can anyone help it is a tough question I know but it would help.

Plymouth goes low res. There is a solution, but it doesn't really matter.

For the standby... I really don't know, that sounds weird! :|

> hmm desertdragon i thhnk you lost me there lol, i'm really really newb at this.

I downloaded the package, it has a run extension, but i can't actually install it cuz i need to sudo it, but...where do i type the command you mentioned? I know it's in terminal, i mean how wil the command know that i want to install that particular file, am i not supposed to mention the file somewhere in the command? i'm not sure how that works

techunit:
I had that low res boot splash as well with the 32 bit, and when i installed 64 bit, i don't get it anymore. Strange.

Open a terminal.
cd to the folder you downloaded it to (normally ~/Downloads )

Now type ls.
You'll get a list of the files. Find the ATi driver.

Type sudo sh name-of-the-driver-file.run

Note: You can get away with only typing the first few letters of the installer and then typing * at the end. (Like the Windows wildcard)

After the installation done, close the installer. DO NOT RESTART.
Type in the same terminal as before (it should now be avaible for use again):

sudo aticonfig --initial -f

Reboot.
If it doesn't work, I have no idea what's going on.

See, the second post you made (which I am not going to bother to quote) is a CLEAR evidence you forgot to type sudo aticonfig --initial -f

Do the whole thing again but...

REMEMBER AFTER INSTALLATION, BUT BEFORE REBOOTING, TO TYPE:
```
sudo aticonfig --initial -f
```

If you don't, it'll become really jaggy and slow, and it won't work, and at some point might even break down entirely.

---

