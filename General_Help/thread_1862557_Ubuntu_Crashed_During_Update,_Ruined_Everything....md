---
title: "Ubuntu Crashed During Update, Ruined Everything..."
date: 2011-10-16
forum: General Help
---

### Post by sKRiBEL on 2011-10-16
going to reinstall ubuntu I suppose...

---

### Post by sKRiBEL on 2011-10-16
Bump

---

### Post by Dremel70 on 2011-10-18
HELP!!! My computer power source was interupted during update to 11.10.  Now it won't boot up properly. I have created a USB install but I can't get it to install.

---

### Post by mörgæs on 2011-10-18
Is it easier to help you if you provide a complete and detailed description of what happens.

---

### Post by Dremel70 on 2011-10-18
I finally got it to go into recovery mode (I think).  I'm not the sharpest pencil in the box with Ubunutu. RIght now it is saying 
 
[EMAIL="root@dennis-eM250"]root@dennis-eM250[/EMAIL]:~#
 
I do not know what to do now

---

### Post by Dremel70 on 2011-10-18
When I boot without the USB attached I get the following...
 
Rather than invoking init scripts through /etc/init.d, use the service(8) utility, e.g. service s90binfmt-support start
 
Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the start(8) utility, e.g. start S90binfmt-support start: Unknown job: S90binfmt-support
 
* Stopping cold plug [OK]
                              [OK] * Stopping log inititial device creation 
                              [OK] * Starting configure network device security
                              [OK] * Stopping anac(h)ronistic cron
                              [OK]
 
Then there is no command line nor can I make it do anything. It is just frozen

---

### Post by Dremel70 on 2011-10-18
Where is shows a smiley face should have the number 8 in ()
 
 
Can someone tell me how to reformat my hard drive and reinstall 11.04? 
 
Is there anyway I can get access to my pictures in recovery mode and save them to an external hard drive. If not I accept I loose everything because I didn't back it up. But I really need my computer back in working condition.

---

### Post by mörgæs on 2011-10-18
Again, exactly what happens when you try to boot the USB stick? 
How did you create it?
Have you changed/checked boot settings in BIOS?

---

### Post by Dremel70 on 2011-10-19
I have the boot settings to boot from USB. 
 
I followed the directions to making the USB from the Ubuntu download page. I used the pendrivelinux that is talked about.

---

### Post by mörgæs on 2011-10-19
As a first step we should just focus on getting a live boot to work. Later comes the install.

Which kind of error messages do you get when booting?

During the boot process you should see an option for self-testing the USB stick ('test media for defects' or similar). Have you tried this?

---

### Post by Dremel70 on 2011-10-19
I haven't seen anything like that. 
 
I've tried a usb boot with 11.10 and 11.04
 
I get  
 
* Checking battery state...  [OK]
* Stopping System V runlevel compatibility   [OK]

---

### Post by mörgæs on 2011-10-19
Don't you get to see a screen (more or less) like this one?
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Might be necessary to 'push any key' when you see the keyboard-man symbol.

---

### Post by Dremel70 on 2011-10-20
No, I believe it is because where I am located the internet is so slow and goes down so often I am unable to get a good download of Ubunutu. 
 
I'm getting a "squash" file error message. 
 
I've taken the hard drive out of the netbook and connected it to a set up that some of my IT guys here have. They told me I could then hook it up to another computer to use as an external hard drive and that I could get my photos and documents off of it then and back them up. 
 
When I connect it to a windows computer is says that I have connected a drive but I can't access it. It doesn't show up in windows explorer. Any idea how to access the drive?

---

### Post by mörgæs on 2011-10-20
This error message could indicate that the ISO is damaged. An unsteady internet connection might be the reason for this.

If you still have the ISO, you could check it with MD5 sum:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

This will tell if you need to download again.

I can't help with the Windows questions, sorry.

---

