---
title: "Updating Ubuntu, sh:grub, and loss of Windows XP"
date: 2010-02-08
forum: General Help
---

### Post by arkage82 on 2010-02-08
I only began using Ubuntu around Christmas time. I don't have any programming experience, but was looking for a way to get away from Windows. The dreaded update hit me and upon reboot, Ubuntu would only return the sh:grub prompt.

As a double whammy, Windows XP won't boot up either. The logo screen begins and before the status bar reaches its halfway point, I get the dreaded Blue Screen of Death. 

I've read alot of this forum of others problems and possible fixes (actually understanding very little of it). I will try to type some of the suggested code in in the morning, but don't have any idea of what I am attempting to accomplish, other than get my puter to load something so I can salvage any of the 5 years worth of data stored on it.

A fix was offered to install the wubilder file from Windows, but I can't even try that (no Windows). I originally loaded Ubuntu from downloading it and image burning it to a CD, but 1) I can't find the CD and 2)I cant get my computer to boot from either of my optical drives. 

I've run extensive diagnostics on my computer by F12-ing on start and booting from the Utility Partition. Everything passes, with no errors. 

I could really use some help here. And forgive me for asking, but I need it put in terms and directions I can understand, not just pages of code. 

I was very happy with Ubuntu, to the point I was ready to go to it 100%. Then the crash. Now finding out it was a bad update. And now seeing that most of the help is beyond my understanding and ability to do. I guess I should have done some more research before I initially took the plunge. Maybe I'm destined to be a Windows drone for life.

Thanks for any help. At this point I'm willing to try anything, even if I can only access my files once to get out whatever I can. Thanks.

---

### Post by meierfra. on 2010-02-08
Do you have  a Wubi install (that  is you run the Ubuntu CD inside Windows and chose "install Ubuntu inside Wubi"?  Or do you have a regular install on an separate  partition?

It sounds more like a regular install, so the "wubildr" is of no use.

Try this: at the "sh: grub" prompt at boot up type

```
search -f --set /vmlinuz

probe -u --set=uuid $root

linux /vmlinuz root=UUID=$uuid ro

initrd /initrd.img

boot
```


**If this did not boot you into Ubuntu**

Post the output of all those command and also the output of
```
ls

set

```

**If you did boot into Ubuntu**

Run the [boot info script ]("http://bootinfoscript.sourceforge.net")and the post the RESULTS.txt

---

### Post by meierfra. on 2010-02-08
I  reread your post and you might have  a Wubi install after all.

So if the above commands don't boot you into Ubuntu, try this at the "sh:grub" prompt:

```

set root=(loop0)

linux  /vmlinuz root=[COLOR="Red"]/dev/sda1[/COLOR] loop=/ubuntu/disks/root.disk ro

initrd /initrd.img

boot

```
You  might have to replace /dev/sda1 by /dev/sda2 or some other device name. It needs to be the device name of the partition containing Wubi.

Did you have any hard shutdowns lately, which might have caused your double trouble?

---

### Post by arkage82 on 2010-02-09
I typed in the first set of commands. On the line with the probe command, I got an Unknown Command error.

When typing in "ls", this was returned:
(loop0) (hd0) (hd0,3) (hd0,2) (hd0,1) (fd0)

error- cannot get C/H/S values


Results from the "set" command:
?=0
color_highlight=
color_normal=
loop=loop0
pager=
prefix=(hd0,2)/boot/grub
root=loop0
show_panic_message=false


I tried the 2nd set of commands as well, but upon entering boot, it took me back to selection between Ubuntu and XP for OS, and then back the sh:grub prompt.

I'm not sure what Wubi is. I had to download a program to burn an image onto a CD and that is what I used to install Ubuntu the first time. 

When the update ran, and the sh:grub appeared the first time, I did a Google search for remedy and found I was to run CHKDSK /r which was said to be a fix. I ran it, and it took forever. When it was done, so was my computer. Windows was hung on restart and the system was shut down (via the power button) and then on restart, sh:grub on one side, and BSOD on the Widow (sic) side.

Thanks for the reply. As long as you want to keep trying, I'm willing to, as well.

---

### Post by CrusaderAD on 2010-02-09
Hey arkage82, I'll be following this thread since it's technically a different topic now. Any luck with the live cd or usb desktop?

---

### Post by arkage82 on 2010-02-09
I'm trying to make the USB drive, but when it gets to Creating Folder, it just seems to sit and do nothing (?) Will let it run and see what happens.

I can't boot off of my CD drive, tried with several disks and no luck, and I don't know where the CD is that I originally made. So..... kinda in a holding pattern right now. 

Will post results and updates as they become available.

---

### Post by CrusaderAD on 2010-02-09
Which desktop are you trying to use? Slax is the fastest and easiest I've used so far. You can install it right from windows onto the usb drive. It's literally designed to be ran on a usb stick.

---

### Post by arkage82 on 2010-02-09
Oh, I wasn't sure what Slax was, so I just picked the Ubuntu 9.10.... (I'm familiar with the devil on this side of the bridge.......)

Can I stop what I have going here and go to something else. I'm really getting gun shy on alot of this stuff.

---

### Post by CrusaderAD on 2010-02-09
Yeah, you can just format the usb drive and use slax. It's extremely user friendly and basic. Plus I think it mounts the partitions automatically without doing it from the command line. All you do is follow the instructions on pendrivelinux.com for slax and boot into it. You should be able to find your stuff from there.

---

### Post by arkage82 on 2010-02-09
OK gonna give this a try, have 30 minutes left on the download, then I need to get to work. I didn't really plan on taking a half day off today...... ugh. LOL.

I do appreciate the help though and as long as I have a direction to go in, I have to try to salvage what I can.

---

### Post by CrusaderAD on 2010-02-09
Cool. Post how it goes. A wubi (installation within windows) shouldn't have messed up your windows boot loader or, for that matter, the partition itself. It could be a million things, but we'll try and narrow it down.

---

### Post by meierfra. on 2010-02-09
You are using Wubi, otherwise you would not have a "(loop0):
> root=loop0

> CHKDSK /r which was said to be a fix. I ran it, and it took forever.
"chkdsk /r" always runs for a very long time.  Did it  fix any errors?


> then on restart, sh:grub on one side, and BSOD on the Widow (sic) side.

Did you boot into Windows after  "sh:grub" and  before running "chkdsk /r"?  I'm asking, since I'm trying to figure out whether your BSOD  is caused by "chkdsk"

> As long as you want to keep trying, I'm willing to, as well. 

I'll keep trying until I run out  of ideas.

Once you get the LiveUSB going (Slax or Ubuntu, should not really matter) post the RESULTS.txt so that we can see what is going on.

---

### Post by arkage82 on 2010-02-09
chkdsk didn't find or fix any errors

I know I was running XP after I had the sh:grub issue. I think the BSOD appeared right after chkdsk was finished. (It's a STOP 00...024x, with some other numbers after it).

Local guy slaved my drive to his computer and wasn't able to see anything on the drive. He ran chkdsk and said it took all of 30 seconds to finish. He put his hard drive in my unit and it booted up fine. Also, he swapped out the optical drives and the power supply but nothing seemed to make a difference. So, he charged me $50 and said to buy a new computer....... (that didn't impress the wife over all the pix she lost, hence I'm sitting here today.....)

---

### Post by arkage82 on 2010-02-09
I followed the instructions for making the bootable USB device with Slax and everything went fine. I installed it in the problem computer, and during boot up, the USB stick flashes, but I'm stuck with a black screen and flashing cursor. Nothing else.

If I press F2 for set up I can set the Drive sequence for USB device first then Hard drive BIOS (which is how I have it now). The only options I have for Boot sequence is CD and Hard Drive.

Any ideas from here?

---

### Post by meierfra. on 2010-02-09
> but I'm stuck with a black screen and flashing cursor.

Try the Slax USB on a different computer and see whether it works.

---

### Post by arkage82 on 2010-02-09
The only computer I can try it on is the old Win 98SE machine ( I can't risk running it on this laptop b/c this is my wife's complete work life). I set the Boot to read removable devices first, but it still goes right to Windows. The USB drive does not flash like it is trying to be read. 

After I downloaded the Slax file, I copied it to the USB device, then I extracted the files. They were all created in a Slax folder. I opened the folder, found the boot folder, ran the bootinst.bat and then answered Y to make it bootable. 

I don't know if Win 98SE is capable of booting this up or not? I will check the settings again and see if it will boot from the USB device.

---

### Post by arkage82 on 2010-02-09
grrrrr further inquiry into Win98, does not support USB boot. The removable device is a floppy drive, no USB things are even listed.

---

### Post by CrusaderAD on 2010-02-09
Hmm... we got to get one of the operating systems working, or boot into a live cd. You could use any distro's live cd. You just need something to get you into the file systems. I think I read back that you have a slave drive installed? Have you any experiencing rearranging the internal components to the machine? You could take out all "important" drives... use an old drive (or buy a cheap new one), install linux to that one, run the old important drive as a slave and see if you can pick up the old data. That would be the hard way, but another suggestion.

---

### Post by meierfra. on 2010-02-09
> I can't risk running it on this laptop b/c this is my wife's complete work life).
I hope you have backups.

I don't think there is anyway how booting from the flash drive could hurt the laptop.


Other options: 

Try creating a Ubuntu LiveUSB and see whether it works any better.

Get a USB enclosure for your hard drive and  then attached it to your wife's laptop.


> ```
set root=(loop0)

linux  /vmlinuz root=[COLOR="Red"]/dev/sda1[/COLOR] loop=/ubuntu/disks/root.disk ro

initrd /initrd.img

boot
```


... but upon entering boot, it took me back to selection between Ubuntu and XP for OS, 

Did you try /dev/sda1, /dev/sda2 and /dev/sda3?

---

### Post by arkage82 on 2010-02-09
The slave drive is what the guy at the local shop tried when he ran out of ideas. I don't have any way of doing that.

I have the files backed up on this laptop, but this is the last "functioning" computer we have at the moment and usually the one she takes on the road everyday. It was left home for me to "fix" the problem I caused by not being happy with Windows. :-(

I tried every sda1, sda2...., sdb1, sdb2.,.. up to 5 with no luck on any of em. 

I couldnt get the Ubuntu to work on the USB, it got to the point it was Create Folder H: and then just sat there for 20 mins. 

I don't know. I appreciate all the help you guys are giving, but I don't see much hope in my case.

---

### Post by CrusaderAD on 2010-02-09
> **meierfra. said:**
> Get a USB enclosure for your hard drive and  then attached it to your wife's laptop.

This is another great suggestion. It's worked for me in the past.

---

### Post by CrusaderAD on 2010-02-09
> **arkage82 said:**
> I don't know. I appreciate all the help you guys are giving, but I don't see much hope in my case.

Depending on how important the files are and how comfortable you are... you can mail it to me and I'll save the data. I wouldn't charge you or anything.

---

