---
title: "Ubuntu 11.10 not booting but showing Purple Screen"
date: 2011-10-14
forum: General Help
---

### Post by therealankit on 2011-10-14
I upgraded Ubuntu 11.04 to 11.10 yesterday, upgradation went fine. It even restarted properly and i liked what i briefly saw in the new Ubuntu. After that i shut it down. Next day when i started my Laptop, Ubuntu didn't boot and showed only a Purple Screen of death :(. I restarted it many times but with no success. As nothing is on the screen, i can't do anything. Hope someone provide me any idea what to do about it.

Details-
Laptop- Dell N5010 15R
Processor- Intel Core i5 64bit
On dual boot with Windows 7 Ultimate

---

### Post by effenberg0x0 on 2011-10-14
Reboot your PC
Hold the shift key, in order to reveal the Grub boot menu
In Grub, select the recovery option (generally the second one)
In a few moments, recovery will ask you what to do. Select a root shell.
when you are the console prompt, type the following command
```

mount -o rw,remount /
nano /etc/default/grub
```Inside the nano editor, use the keyboard arrow keys to navigate and locate this line. Edit it to make it look like this. Remove any instance of the word "quiet" and "splash" from this or other line in this file.

```
GRUB_CMDLINE_LINUX_DEFAULT="text"

```Press Ctrl+X, Y and <Enter> when you're done editing, to save the file and exit.
Now update grub with this command:

```
update-grub
```And reboot your system
```
reboot now

```You *should* have no purple screen, as we have disabled plymouth. That means we will be able to see text messages that will let us know what is going on with your setup. 

This system *will not* boot up to a desktop yet, unfortunately. You'll be again at a console prompt. 

If the system is not asking for your user/password, switch to another VT using Ctrl+Alt+F1 to F6

```
sudo service lightdm start
```
See if the command above does get you to lightdm and to a graphical session.
Use Ctrl+Alt+F1 to F6 to get back to the VT you were using in case all you see is a text screen after the command above.

I'll soon ask you what Video Card you have. If you don't know the answer to that, take the opportunity to run this command:
```
lspci | grep -i vga
```

If you are not presented with the option of using your user/password to login at the console, take note of the last text messages you see on your screen and please report them back here, so we can continue.

Regards,
Effenberg

---

### Post by bilodeau on 2011-10-15
I was having similar problems after I did a fresh install of Ubuntu 11.10 today.  During the install, running from the CD, everything was great.  I reboot, and after selecting the default boot option during GRUB, I get nothing but a flashing light purple screen.

I rebooted a couple of times after this, but got the same problem - flashing light purple screen.

I rebooted into "safe mode" and edited the file /etc/default/grub, commenting out the line with "quiet splash" and adding a replacement with "text" instead.  I rebooted, selected the normal default, and now have an operational system with graphical login and full desktop environment. I didn't have to do anything else.

I have rebooted a few times since changing the file, and get the same fully functional behavior, so it appears that the tweak to the /etc/default/grub file was all I needed.

Is there any more information I should post to better enable people to track down the source of this strange error?

---

### Post by quiela on 2011-10-21
Hi, I modified the grub , and I reboot my system, when I use the code 

sudo service lightdm star

I got that service is already running. 

I also cannot boot in the older version.

Thanks for the help

---

### Post by techvish81 on 2011-10-21
[http://ubuntuforums.org/showthread.php?t=1866512](http://ubuntuforums.org/showthread.php?t=1866512)

---

### Post by Jon1001 on 2011-10-21
I had the same problem. Here's my fix:

- Hold shift while it's booting up to access the GRUB menu
- Press e to edit the boot options
- Where it says "quiet splash", add noapic so it looks like this: "quiet splash noapic"
- Press Ctrl+x to boot

If this works, let me know and I'll tell you how to make it permanent. Otherwise you'll have to do that every time you boot.

Jon

---

### Post by wchigdon on 2011-10-30
Thank you!

This is my first Ubuntu load and I am loving it.(very new)  I tried the suggestions and it works to a point. when I reboot, the system wants to hang up after this text:

[43.070429] sr 1:0:1:0 Attached scsi generic sg3 type 5


I then type in exit at the prompt

it then takes me to an 8 bit screen where I can select reboot system.

I then can get into the Ubuntu 11.10 and I LOVE IT!

Be so kind as to help me with this process.

Thank you for your efforts.

---

### Post by oggyjac on 2011-12-03
Hi there,
yesterday i installed ubuntu 11.10 32bit within windows 7 using wubi. it went very well. also used it for a day.next day when i started laptop ubuntu started showing purple screen on bootin. it shows grub boot menu but nothing happens on selectin any option.only purple screen appears. 
i tried above mentioned steps of editin boot options but didnt work for me :(. also when i open it in recovery mode it shows message sumthin lik "loading initial ramdisk.." but nothin happens then. 
Plz provide hlp..

details
dell inspiron 1545 n series    
intel core 2 duo
dual boot with windows 7 32bit

---

### Post by RyanDM1776 on 2012-01-27
[QUOTE]Reboot your PC
Hold the shift key, in order to reveal the Grub boot menu
In Grub, select the recovery option (generally the second one)
In a few moments, recovery will ask you what to do. Select a root shell.
when you are the console prompt, type the following command[QUOTE]

I found this forum hopefully just in time!
I recently built a new PC,
Intel core i5 processor
8GB DDR3 ram
Asus P8z68-v lx mobo
older Nvidia Quadro FX video card with 512mb ram

I wanted to install the 64bit Ubuntu 11.10 on it so that I can run vmware workstation and be able to run various vm's that are W7, etc.

Secondly, I want to be able to run GNS3 on it.

Well, the install went fine, but it did hang and get that Purple screen, which sat for more than 15 minutes. I had to reboot 6 times before I could get a logon screen, and then when it wanted to download more drivers, it froze.

Is it incompatable, or what is happening? I need a way out because class starts in 2 days!
I finally got to the grub editor. When it began the reboot, I get one fail:

initctl: Even failed
*Starting load fallback graphics devices [fail]  -----------> does that mean the graphics card is shot?
otherwise, all is [ok]
it appears to be ckecking slowly for each subsequent device.

---

### Post by Antonio Oliva on 2012-02-08
> **effenberg0x0 said:**
> Reboot your PC
Hold the shift key, in order to reveal the Grub boot menu
In Grub, select the recovery option (generally the second one)
In a few moments, recovery will ask you what to do. Select a root shell.
when you are the console prompt, type the following command
```

mount -o rw,remount /
nano /etc/default/grub
```Inside the nano editor, use the keyboard arrow keys to navigate and locate this line. Edit it to make it look like this. Remove any instance of the word "quiet" and "splash" from this or other line in this file.

```
GRUB_CMDLINE_LINUX_DEFAULT="text"

```Press Ctrl+X, Y and <Enter> when you're done editing, to save the file and exit.
Now update grub with this command:

```
update-grub
```And reboot your system
```
reboot now

```You *should* have no purple screen, as we have disabled plymouth. That means we will be able to see text messages that will let us know what is going on with your setup. 

This system *will not* boot up to a desktop yet, unfortunately. You'll be again at a console prompt. 

If the system is not asking for your user/password, switch to another VT using Ctrl+Alt+F1 to F6

```
sudo service lightdm start
```
See if the command above does get you to lightdm and to a graphical session.
Use Ctrl+Alt+F1 to F6 to get back to the VT you were using in case all you see is a text screen after the command above.

I'll soon ask you what Video Card you have. If you don't know the answer to that, take the opportunity to run this command:
```
lspci | grep -i vga
```

If you are not presented with the option of using your user/password to login at the console, take note of the last text messages you see on your screen and please report them back here, so we can continue.

Regards,
Effenberg
Hi Effenberg
I followed your instructions but now I am in a worse situation than before. 
After following all your steps without problems, I got up to "reboot now" and then nothing happened.
Now when I try to enter to the Grub boot menu, the SHIFT key does not work as before, I just go straight to the purple dead screen.

---

### Post by Antonio Oliva on 2012-02-08
Hi Effenberg
I followed your instructions but now I am in a worse situation than before.
After following all your steps without problems, I got up to "reboot now" and then nothing happened.
Now when I try to enter to the Grub boot menu, the SHIFT key does not work as before, I just go straight to the purple dead screen.
I have Windows7 64bit
Thanks
Antonio

---

### Post by curmudgeon38 on 2012-03-09
I have the same problem. I hold the shift key, but nothing happens.
Sometimes its purple, sometimes its black with white lines at the top.

I've been working on this all day, trying to get Ubuntu to boot into safe mode so I can see what I'm doing and install the drivers. I'm frustrated. I thought Ubuntu was supposed to be user friendly. After 11 versions they can't make it easy to boot into safe mode? I don't want to have to use Windows 7, but I have things I'd rather do than spend all my time these forums for hours trying to figure out how to install a driver.

I'm sure there's an answer but I've been chasing them around all over Google for the past 2 days and my eyes are tired from reading all of it.

Slowly losing an Ubuntu newbie to Windows 7...sigh

---

### Post by salterlee on 2012-04-17
Mate, just go to Windows 7. Ubuntu just doesn't work. It is rubbish. I have been trying to use it exclusively for two years now, and it just keeps dying on my desktop. My latest one (after weeks of the screen flicking on and off and removing the video drivers to solve it) is that it stops booting with a distorted screen. I can't log on, nothing to see on screen, and I don't know enough about the coding to sort it, so I'm stuck (again) and don't want to spend another three weeks of my life trying to sort out something that stopped working for no reason. I'll be with you on Windows as soon as I can back up and remove this rubbish!

---

