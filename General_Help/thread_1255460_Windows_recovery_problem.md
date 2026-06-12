---
title: "Windows recovery problem"
date: 2009-09-01
forum: General Help
---

### Post by salingova on 2009-09-01
The problem is that I was extending a windows partition and now it does not boot. I wanted to recover the partition, but it asks for admin password that I don't think I used. How do I type in a blank password (if I just hit enter it exits)? There is a possibility that there was some password that I did not use on login so I tried to use ophcrack livecd to get the password, but it did not work - it said that there were no tables found and the encryption software didn't start. 
Please help me here if you can.

---

### Post by Niko Johnson on 2009-09-01
Alright a hacking post! it is pretty easy to change a windows password with a linux distrubution called trinity rescue kit (TRK) just do a google search and download the iso. once you do that just burn the iso to a disk and boot off it. it will boot up just like most linux live cd's but this has no GUI.. when you get to the shell here are your commands...

1. winpass -u administrator [or the name of the admin]

#Output should follow something like this...

Windows installations found in:
1: /hda1/Windows
make your choice or q to quit [1]:

# you should be safe with the default values depending on disk partitions
#or the O.S, so hit enter beacuse the default is already [1] or you can hit 1 then enter
#It should output with a new password for user prompt just like the "passwd" command
#now its time to change the password.... use a * for a blank password
#beacuse it has the least chances of erros. then y for yes and then reboot
#you can use the reboot command or telinit 0 or init 0 i forget witch one ; )
#take the cd out and there you go! new admin password

---

### Post by P4man on 2009-09-01
+1 for TRK
Saved a while ago when I did an install on 20 PCs with XP, and couldnt log in to any of them. Silly me. I had installed french XP and didn't realize the default administrator account on a french windows is called "administrateur" LOL.

---

### Post by salingova on 2009-09-02
Thanks for the tip, but I have some problems here. If I set the password blank I don't know how to type it in when Im doing the windows recovery because when nothing is typed in pressing enter exits the recovery console. Then when I use TRK to change the password to something I could type it sais: "Sorry, unable to edit since password seems blank already (thus no space for it)"
Do you know what I should do, or do I have to reinstall?

---

### Post by cariboo on 2009-09-02
You can change the Windows admin password from the Live CD.

```
sudo apt-get install chntpw
```

then you will now need to mount the windows partition read/write permission then navigate to %systemroot%/system32/config
Once your located in the config directory issue this command to change the password

```
chntpw -u administrator SAM
```

use * to blank

---

### Post by salingova on 2009-09-02
> **cariboo907 said:**
> You can change the Windows admin password from the Live CD.

```
sudo apt-get install chntpw
```

then you will now need to mount the windows partition read/write permission then navigate to %systemroot%/system32/config
Once your located in the config directory issue this command to change the password

```
chntpw -u administrator SAM
```

use * to blank

I am not sure whether I understand you correctly. I think that this doesn't work on the TRK live cd, but I tried it on the ubuntu that I have on the other partition. I installed the chntpw and then I used cd command to get into media/disk/windows/system32/config; then I used the chntpw -u administrator SAM. Then I get just to the same problem as I described abowe.

---

### Post by Cato2 on 2009-09-02
The problem is Windows Recovery Console - either you need to find another administrator userid on that PC and change its password to something non-blank, or maybe try to use a non Recovery Console way of recovering the PC.

If that doesn't work, a Windows repair install (google for that exact phrase) is non-destructive - all your apps and registry remain installed, it just re-installs the core Windows files.  Of course, a complete backup of registry and user files would be a good idea just in case.

---

### Post by nikhilbhardwaj on 2009-09-02
> **cariboo907 said:**
> You can change the Windows admin password from the Live CD.

```
sudo apt-get install chntpw
```then you will now need to mount the windows partition read/write permission then navigate to %systemroot%/system32/config
Once your located in the config directory issue this command to change the password

```
chntpw -u administrator SAM
```use * to blank

it's funny you know
the double standards athe these forums

this thread was closed
the user isn't asking for too much 
[http://ubuntuforums.org/showthread.php?t=1256280](http://ubuntuforums.org/showthread.php?t=1256280)

and so is any thread that'll tell you how easy it is to reset ubuntu's root password
but when it comes to xp or vista 
you don't seem to have any of these rules

---

