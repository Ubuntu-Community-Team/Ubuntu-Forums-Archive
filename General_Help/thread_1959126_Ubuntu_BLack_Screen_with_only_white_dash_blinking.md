---
title: "Ubuntu BLack Screen with only white dash blinking"
date: 2012-04-15
forum: General Help
---

### Post by H4wkBlaster on 2012-04-15
Hello I am new to Linux  , after getting sick of Microsoft crashes and bugs I decided to install Ubuntu . I did everything requested, iso in  USB , installed and removed vista , which was my previous OS , everything went fine , so when I do my first reboot required in the installation all I get is a black screen with a white dash , it does not go anywhere , can someone please help me?

Thanks in advance.

---

### Post by H4wkBlaster on 2012-04-15
Need help ](*,)

---

### Post by phosphide on 2012-04-15
Couple pieces of information would helpful. What version of Ubuntu are you trying to install? What kind of hardware does your computer have? etc. 

Did you successfully go through the installation screen and then try the first reboot?

The more you provide the easier it is for us to help.

---

### Post by H4wkBlaster on 2012-04-15
Oh okay , I installed Ubuntu 11.10 , everything went fine just until rebooting which all that shows up is a black screen , can only boot Ubuntu from USB. Computer specs E1200 dual core 1.6 Ghz
3Gb Ram  32 bits , intel 82495g express chipset family 
HDD 250 GB

---

### Post by H4wkBlaster on 2012-04-15
No one has a clue?

:(

---

### Post by H4wkBlaster on 2012-04-15
I can run Ubuntu from the USB but not from HDD as it gets the black screen with the white dash , but Vista was running fine so I don t think the problem is of the HDD .

---

### Post by phosphide on 2012-04-15
Have you tried re-installing? Also, did you reformat everything on the hard drive during the install process?

---

### Post by Eirreann on 2012-04-15
Is your computer trying to boot from the USB?  Make sure in the BIOS that it is set to boot from the hard drive and not your USB ports (and I'm sorry that you had to experience VIsta; Microsoft's worst creation!)

---

### Post by H4wkBlaster on 2012-04-16
> **phosphide said:**
> Have you tried re-installing? Also, did you reformat everything on the hard drive during the install process?

Yes , several times, I tried the Upgrade Ubuntu from version 11.10 to 11.10 option aswell nothing seems to work.

---

### Post by H4wkBlaster on 2012-04-16
> **Eirreann said:**
> Is your computer trying to boot from the USB?  Make sure in the BIOS that it is set to boot from the hard drive and not your USB ports (and I'm sorry that you had to experience VIsta; Microsoft's worst creation!)

Haha yeah the difference between Ubuntu and Vista s speed is remarkable really enjoying it , and yes I have the HDD as the first booting device in Bios .

---

### Post by Eirreann on 2012-04-16
> **H4wkBlaster said:**
> Haha yeah the difference between Ubuntu and Vista s speed is remarkable really enjoying it , and yes I have the HDD as the first booting device in Bios .

Okay, then try to get a hold of a blank disc, put the Ubuntu ISO on it (follow the instructions on ubuntu.com) and try re-installing it with that; back when I installed Ubuntu, I had some partitioning issues as well (my HDD wasn't letting the partition be created) so I tried installing it via USB rather than disc, which seemed to work... maybe the ISO file just had trouble writing onto your USB.

---

### Post by H4wkBlaster on 2012-04-16
> **Eirreann said:**
> Okay, then try to get a hold of a blank disc, put the Ubuntu ISO on it (follow the instructions on ubuntu.com) and try re-installing it with that; back when I installed Ubuntu, I had some partitioning issues as well (my HDD wasn't letting the partition be created) so I tried installing it via USB rather than disc, which seemed to work... maybe the ISO file just had trouble writing onto your USB.


Tried with CD and got the same thing , but when I went to reinstall Ubuntu  with USB it only showed up the Erase Disk and install Ubuntu so I selected that option and now it's on "Please Wait" for 2 hours so far . Is it formatting the disk? I thought it was doing that on previous installations but they only took about half an hour so could it be that it skipped that step in the other ones? Have my fingers crossed :popcorn:

---

### Post by gordintoronto on 2012-04-16
Have a look at this: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The important information you provided was this:  intel 82495g

---

### Post by CottonCandy on 2012-04-16
You may want to take a look at this:  [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
> **MAFoElffen said:**
> <b>Are you having these problems?  <br />
</b>   - Error- &quot;Cannot display this grahics mode&quot;  <br />
  - GRUB_GXFMODE-auto results in Blank screen problems on Startup?   (this includes purple or black screen, flashing cursor, stuck at splash  screen...) <br />
  - No Grub Menu?  <br />


---

### Post by sdowney717 on 2012-04-16
I have seen this before when the video driver is wrong.
If you can boot the usb and get a normal screen then nothing is wrong with the hardware.
you can try after booting from usb, deleting, if it exists, a file  called xorg.conf
It is located in folder /etc/X11/ 
When that file does not exist, ubuntu loads its own builtin video driver.
I dont remember if booting a usb lets you get to it with delete privileges.
But you can do it if you get the grub boot menu and select the one under the normal selection, recovery or something it is called. boot to root prompt. Then you have to navigate manually to the folder using dos like commands. It will dump you at a root prompt so you have to back out of root to get to the '/' highest level of the partition using 'cd ..'etc and then you can see the folders with the 'ls' command.
'rm' deletes the file

following is showing the folder structure
```
scott@scott-P5QC:~$ cd ..
scott@scott-P5QC:/home$ cd ..
scott@scott-P5QC:/$ ls
bin    etc             lib         opt   sbin     tmp      vmlinuz.old
boot   home            lost+found  proc  selinux  usr
cdrom  initrd.img      media       root  srv      var
dev    initrd.img.old  mnt         run   sys      vmlinuz
scott@scott-P5QC:/$ cd etc
scott@scott-P5QC:/etc$ cd X11
scott@scott-P5QC:/etc/X11$ ls xorg.cong
ls: cannot access xorg.cong: No such file or directory
scott@scott-P5QC:/etc/X11$ ls xorg.conf
xorg.conf
scott@scott-P5QC:/etc/X11$ rm xorg.conf


```

anyway if you cant figure it out try it, it wont hurt anything to remove that file, or you can just rename it something else instead. I did not let 'rm' command finish as mine is working with the nvidia driver.

---

### Post by H4wkBlaster on 2012-04-21
Forgot to mention one thing it might be important on the installation I remember I got an error as following "an attempt to configure apt to install additional packages from the cd failed" I clicked OK and then a "Installation needs reboot to be complete " message pop'd up so  , so I didn't think the error had anything to do with my problem , could it be connected or be the cause of my problem? Thanks for all the help guys btw

---

### Post by H4wkBlaster on 2012-04-23
It's working now , reinstalled the iso on the usb and now installed it's fine except for one thing , Ubuntu is running extremely slow don't know what to do , gonna start a new thread . Thanks for everyone who helped :p:p:p:p

---

