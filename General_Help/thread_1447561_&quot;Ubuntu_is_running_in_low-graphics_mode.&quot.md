---
title: "&quot;Ubuntu is running in low-graphics mode.&quot;"
date: 2010-04-05
forum: General Help
---

### Post by !!?? on 2010-04-05
Yesterday, before I went to sleep I tried to put the computer in Suspend, but it froze up in the process. So I just manually shut the computer off, and went to sleep. Today went I booted it back up, I get this error, and can only log in through low-graphics mode. I'm still quite new to Ubuntu, so I have absolutely no idea how to fix it. Here is the first page I get. I also tried copying my "xorg" log through this screen, as it is too big to write down, but when I log in, it doesn't seem to be copied and I cannot paste it. 

> Ubuntu is running in low-graphics mode.
The following error was encountered. You may need to update your configuration to solve this.

(EE) Apr 05 14:20:38 NVIDIA(0): Failed to initialize the Nvidia kernel module. Please see the system's kernel log for additional error messages and consult the Nvidia readme for details.
(EE)NVIDIA(0): ***Aborting***
(EE)Screen(s) found, but none have a usable configuration. 

I have Ubuntu 64 bit 9.10, and my GPU is a Nvidia 9500gt, of which has been working fine for the past month. Thank you very much for any help.

---

### Post by mickObrian on 2010-04-05
You may have to re-configure the xorg, I had to do this when I first installed my NVIDIA drivers, go to System > Administration > NVIDIA X Server Settings, see if it pops up asking you to run something like "nvidia-xconfig" if it does you'll have to go to the terminal and type it in as as "sudo nvidia-xconfig" (or whatever it asked you to type, I can't quite remember) and then restart your system, see how that goes.

---

### Post by !!?? on 2010-04-05
> **mickObrian said:**
> You may have to re-configure the xorg, I had to do this when I first installed my NVIDIA drivers, go to System > Administration > NVIDIA X Server Settings, see if it pops up asking you to run something like "nvidia-xconfig" if it does you'll have to go to the terminal and type it in as as "sudo nvidia-xconfig" (or whatever it asked you to type, I can't quite remember) and then restart your system, see how that goes.

I get

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

So I run it in terminal and get this. 

> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

What should I do next?

---

### Post by mickObrian on 2010-04-05
Now restart your system and you should be good to go.

---

### Post by !!?? on 2010-04-05
> **mickObrian said:**
> Now restart your system and you should be good to go.

Nope, I still have the problem.

---

### Post by mickObrian on 2010-04-05
Hmm, I'm not very knowledgeable on this subject and perhaps this is not the good way of doing this, but what I just tested was copying the xorg.conf.failsafe and used it as the xorg.conf, logged out and found myself in log graphics mode, I logged back in and reconfigured xorg using 'sudo nvidia-xconfig' as you did before, gave me the same message you got "New X configuration file written to '/etc/X11/xorg.conf'", I logged out (resetting Xorg) and I was back in full screen mode, I'm not sure if your xorg.conf file is corrupt or not. My current configured xorg.conf file has 54 lines, and my xorg.conf.backup and xorg.conf.failsafe both contain the same 14 lines, would you mind telling me how many lines your files have?

cd /etc/X11/
cat xorg.conf | wc -l
cat xorg.conf.backup | wc -l
cat xorg.conf.failsafe | wc -l

---

### Post by !!?? on 2010-04-05
> **mickObrian said:**
> Hmm, I'm not very knowledgeable on this subject and perhaps this is not the good way of doing this, but what I just tested was copying the xorg.conf.failsafe and used it as the xorg.conf, logged out and found myself in log graphics mode, I logged back in and reconfigured xorg using 'sudo nvidia-xconfig' as you did before, gave me the same message you got "New X configuration file written to '/etc/X11/xorg.conf'", I logged out (resetting Xorg) and I was back in full screen mode, I'm not sure if your xorg.conf file is corrupt or not. My current configured xorg.conf file has 54 lines, and my xorg.conf.backup and xorg.conf.failsafe both contain the same 14 lines, would you mind telling me how many lines your files have?

cd /etc/X11/
cat xorg.conf | wc -l
cat xorg.conf.backup | wc -l
cat xorg.conf.failsafe | wc -l

> @-desktop:/etc/X11$ cat xorg.conf | wc -l
57
@-desktop:/etc/X11$ cat xorg.conf.backup | wc -l
54
@-desktop:/etc/X11$ cat xorg.conf.failsafe | wc -l
14

Seems to be the same.

---

### Post by mickObrian on 2010-04-05
> **!!?? said:**
> @-desktop:/etc/X11$ cat xorg.conf | wc -l
57
@-desktop:/etc/X11$ cat xorg.conf.backup | wc -l
54
@-desktop:/etc/X11$ cat xorg.conf.failsafe | wc -l
14 			 		
For some reason your current xorg.conf file contains 3 more lines than the previous one (xorg.conf.backup) that you used before the problem, and it still isn't working, seeing as how my current working file and your previous(ly working) file both have 54 lines, I'll assume that is the correct number (my limited knowledge is becoming obvious), so you could do what I did and use copy your failsafe file to your current xorg.conf file and re-configure xorg using nvidia-xconfig as I did (which worked), other than that I don't know what the problem is but I feel it's safe to assume that 54 lines is the correct number for a default configured xorg.conf file.

---

### Post by !!?? on 2010-04-05
> **mickObrian said:**
>  so you could do what I did and use copy your failsafe file to your current xorg.conf file and re-configure xorg using nvidia-xconfig as I did (which worked)

How exactly would I do that? Thanks a lot for the help by the way.

---

### Post by mickObrian on 2010-04-05
cd /etc/X11
sudo cp xorg.conf.backup xorg.conf.backupOld (I recommend saving this file as it worked before, it'll be writted over when you re-configure xorg.)
sudo cp xorg.conf.failsafe xorg.conf

Also I wouldn't mind posting my Xorg files if you wanted to take a look.

---

### Post by quadproc on 2010-04-05
> **!!?? said:**
> Yesterday, before I went to sleep I tried to put the computer in Suspend, but it froze up in the process. So I just manually shut the computer off, and went to sleep.
Usually, when you are thrown into "low graphics mode", it means that either your xorg.conf file is damaged or that your driver has been damaged.  You can look into your xorg.conf file this way:```
more /etc/X11/xorg.conf
``` and see if anything is obviously incorrect.  ("more" displays one page then waits for a space to display the next page.)

A damaged driver probably requires removal and reinstallation.  I don't use nvidia myself so I don't know the details of their procedure but usually you can get removal and installation information from the support category in their web site.

I recently had to remove and reinstall my graphics driver because I upgraded from Ubuntu 9.04 to 9.10; the kernel and the driver did not get along with each other after the upgrade for some reason.  But completely removing the driver and then installing the same driver took care of the problem.

quadproc

---

### Post by !!?? on 2010-04-05
> **mickObrian said:**
> cd /etc/X11
sudo cp xorg.conf.backup xorg.conf.backupOld (I recommend saving this file as it worked before, it'll be writted over when you re-configure xorg.)
sudo cp xorg.conf.failsafe xorg.conf

Also I wouldn't mind posting my Xorg files if you wanted to take a look.

Alright after doing that and rebooting, I don't get the error screen, but I think it is still booting in 'low-graphics mode' without me even choosing for it to do so. I go to my Nvidia X server settings and I still get the error about not using a Nvidia driver. 

Here is the amount of lines I have now. 

> @-desktop:/etc/X11$ cat xorg.conf | wc -l
14
@-desktop:/etc/X11$ cat xorg.conf.backup | wc -l
54
@-desktop:/etc/X11$ cat xorg.conf.failsafe | wc -l
14

---

### Post by mickObrian on 2010-04-05
I don't think you re-configured Xorg, you have to go to System > Administration > NVIDIA X Server Settings and type that in again, then you can just log out, you shouldn't have to reboot to restart Xorg, if that doesn't work you may just have to reinstall the driver all together.

---

### Post by !!?? on 2010-04-05
> **mickObrian said:**
> I don't think you re-configured Xorg, you have to go to System > Administration > NVIDIA X Server Settings and type that in again, then you can just log out, you shouldn't have to reboot to restart Xorg, if that doesn't work you may just have to reinstall the driver all together.

I ended up reinstalling the proprietary drivers that ubuntu offers, for a temporary solution. It isn't in low-graphic mode anymore. I'll just reinstall the driver I was using, and I think it should work as it was again. Thanks a lot for the help.

---

