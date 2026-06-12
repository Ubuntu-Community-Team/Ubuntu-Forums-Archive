---
title: "Change the BIOS?"
date: 2011-05-28
forum: General Help
---

### Post by MRoeDesigns on 2011-05-28
I used the USB Creator to mount my Windows ISO to a usb drive, which worked perfectly. However I cant figure out how to get it to actually boot. I'm using Ununtu 11.04. I tried using grub, but apparently I'm doing something wrong.

---

### Post by Quackers on 2011-05-28
You will need to change your bios boot priority so that the USB stick/drive boots before the internal hard drive.

---

### Post by MRoeDesigns on 2011-05-28
Right, hence the title of the thread. But I cant figure out how to do that.

---

### Post by linuxinstalledfromhdd on 2011-05-28
Are you looking for something on how to do this?

[http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/step2/Changing-BIOS-Boot-Order/](http://www.instructables.com/id/Boot-and-Run-Ubuntu-from-a-Flash-Drive/step2/Changing-BIOS-Boot-Order/)

---

### Post by Quackers on 2011-05-28
There will be a key to press (or tap) during the boot process that will enter you into the bios. The key depends on your system. It is often F2 or the del key but it can also be others. Sometimes there is a one boot only key which is often the F12 key.This one does not permanently change the boot priority.
The key for your system should be in your pc's documentation or sometimes appears on the screen very early in the boot process.

---

### Post by MRoeDesigns on 2011-05-29
Thanks! I thought it was something I had to change through grub xD

Fixed that, but apparently the iso is mounted wrong? I used the USB boot creator that came with my installation of Ubuntu, thinking that would work, but apparently it didn't. It tries to boot off of the usb, and then proceeds to crash.

---

### Post by Irihapeti on 2011-05-29
You may have better luck using unetbootin to make bootable USBs. Install from the Software Center or through synaptic.

---

### Post by MRoeDesigns on 2011-05-30
I downloaded UNET like you said, and I also downloaded GParted partition editor to make sure I could reformat the USB drive if needed. I've tried with multiple different format optioons, and two or three different ISO files as well, but to no avail. And my BIOS is set to auto-boot from USB if it's available.

When I try to boot off the USB, it loads up a list of some sort, but the only option is Default. And theres a countdown that says 'Automatic boot in 10 seconds", but as soon as it hits 0 it just resets to 10.

---

### Post by Irihapeti on 2011-05-30
I have had unetbootin do that to me, very occasionally - just keep on reloading the boot screen over and over again. I know that I was able to fix it. The problem is, it happened so long ago that I've forgotten exactly what I did.

I do remember that there were two different files with the name syslinux.cfg. One was in the top directory, the other was buried in a folder two or three layers down. The USB was booting off the top directory one, which wasn't pointing to the actual kernel etc needed to boot the system. I recall that the other one had the commands that were needed.

Probably, if I had your USB drive in front of me, or were able to see the actual layout of the directories, I would be able to work out a solution. As I don't have that, I hope that someone else will be able to help, based on what I've remembered.

Sorry I can't be of more help.

---

### Post by MRoeDesigns on 2011-05-30
Hmm. I don't even seem to have a syslinux file. It's an iso file for windows 7, mounted with UNET. I did a search on the filesystem for sys, and got a few results but nothing by that name. I do, however, have a sysmain file and a sysmain32 file, but those are both .SDB's, not config files.

---

### Post by Irihapeti on 2011-05-30
Sorry, I'm definitely out of my depth here. :( I'm not even sure if unetbootin works with Windows iso files.

You might need to find a Windows forum to ask your question, unfortunately.

---

### Post by linuxinstalledfromhdd on 2011-05-30
If you need to flash BIOS, you need to start trouble ticket the manufacture of your desktop or laptop computer.  If you get advice from somebody here, you have no recourse if you mess up your BIOS Rom chip and your system is dead.   Most companies will provide support and even a way of flashing the BIOS that is non-OS specific, at least to get that done for the end-user.

---

### Post by MRoeDesigns on 2011-05-30
Why would I need to flash the bios?

---

### Post by linuxinstalledfromhdd on 2011-05-30
Why is this titled "Change the BIOS"? Is this off topic or what?

---

### Post by MRoeDesigns on 2011-05-30
Please read the topic before trying to give advice lol, it makes life much easier.

---

### Post by linuxinstalledfromhdd on 2011-05-30
no no no..  You title it correctly, and then maybe we can understand what you need help with.   Horse before the cart my friends.

---

### Post by MRoeDesigns on 2011-05-30
It is entitled correctly. Read the topic and you would know that. I had to change the BIOS to boot from a USB, hence the title "CHANGE THE BIOS". Read the topic.

---

### Post by jerrrys on 2011-05-30
unetbootin will not work with windows

---

### Post by MRoeDesigns on 2011-05-30
Is there any bootloader that would? Or is there some other way I can copy the ISO files and make the USB bootable?

---

### Post by linuxinstalledfromhdd on 2011-05-30
> **MRoeDesigns said:**
> It is entitled correctly. Read the topic and you would know that. I had to change the BIOS to boot from a USB, hence the title "CHANGE THE BIOS". Read the topic.

Every time some user starts using that word "hence" it makes my back hurt.  You seem to know enough to complain about your situation, but not enough to actually fix it when you mess it up.  Am I right?  You used the word hence twice in this thread might I add.  My back is really sore now.:D

If nobody knows windows in a ubuntu help group, that's it.  There is no hence about it I'm afraid. :)

This isn't really a BIOS issue is it?

---

### Post by MRoeDesigns on 2011-05-30
I'm not going to argue with somebody whose logic is as sound as a twelve year olds. If you're going to help me, then help. If not, **** off.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Why don't you simply contact Microsoft and start a trouble ticket with them about it?  They can help you with a live stick of Windows and data migration, right?  

Did you backup your data like everyone -knows- they need to do on a regular basis?  Isn't that common sense? You have a very rare configuration that nobody knows anything about. It would be a good idea to put that data someplace in case all heck breaks loose eventually. Right?

---

### Post by MRoeDesigns on 2011-05-30
Because Microsoft isn't going to be able to help with a problem with linux software. Again, if you read the topic, you'd realise that the problem is that UNET doesn't support windows iso's, which i did not know. That's where the problem came from originally.

And yes, my data is backed up. I hope you weren't trying to insult me with that one. I'm not as stupid as you apparently seem to think I am.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Okay, let me get this straight. You used Ubuntu Disc Creator to make a Windows Live USB?  It worked. But for some reason you are having trouble mounting it? Correct?  :) 

I'm pretty sure I understand what you are attempting to do here. 

Doesn't windows have it's own USB creation applications for "their" ms operating system?  Isn't that the right procedure for creating a live windows USB?  Isn't that what they would have told you on the phone with MS support? 

How do you mount a Windows USB created in Ubuntu to a Ubuntu system?

Install Virtualbox 4. Install Windows XP since you obviously have it to install to a USB with Ubuntu .  And do whatever you need to do with it?

---

### Post by jerrrys on 2011-05-30
usb creator will not work with windows

[http://www.google.com/search?client=ubuntu&channel=fs&q=install+windows+usb&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=install+windows+usb&ie=utf-8&oe=utf-8)

---

### Post by MRoeDesigns on 2011-05-30
Well you're half right, getting closer. Mounting it was not the problem. It was mounted fine, but yes like I just said the problem is that UNET doesnt support windows, so it wouldn't boot.

So yes, what you suggested was, for the first time so far, correct. Too bad I realised this about twenty minutes ago when I was told UNET wouldnt work.

---

### Post by linuxinstalledfromhdd on 2011-05-30
Does it really need to be done though?

---

### Post by athenroy on 2011-05-30
Gees, Crimany! this degenerated quickly!  What the guy wanted to do was change his BIOS so he could boot from a USB stick, which he did, that is why the title.  Let me ask you, did you just copy the ISO file to the USB stick and not the contents of the ISO file?  Maybe that is the problem.  I'm not that familiar with USB boot, but I know on a CD or DVD you have to burn the contents of the ISO, not the ISO itself.  I would think a USB stick would be not different.

---

### Post by Irihapeti on 2011-05-30
Apologies that I didn't pick up on the fact that it was a Windows iso sooner. :(

Anyway, I've found a few links that might help point one in the right direction.

[http://serverfault.com/questions/2952/boot-and-install-windows-from-a-usb-thumb-drive](http://serverfault.com/questions/2952/boot-and-install-windows-from-a-usb-thumb-drive)
[http://serverfault.com/questions/10025/how-to-make-a-bootable-usb-drive-out-of-a-bootable-dvd-or-cd](http://serverfault.com/questions/10025/how-to-make-a-bootable-usb-drive-out-of-a-bootable-dvd-or-cd)
[http://www.bootdisk.com/pendrive.htm](http://www.bootdisk.com/pendrive.htm)

None of them seem to be very recent, though. It might be worth looking around further at serverfault.com to find something newer.

---

### Post by linuxinstalledfromhdd on 2011-05-30
That's not your fault. It my fault that i didn't just call them out on the fact that this is a windows USB live stick created with Ubuntu, which is something honestly, we don't support people doing.  I feel bad just supporting users putting windows on a virtualbox.  Just so you know where I am coming from here.  Wine is fine.  But my whole idea behind Ubuntu is so we can stick to helping people with Ubuntu problems. If someone has windows problems and MS issues, they already know they need to be contacting MS support and starting a trouble ticket.  Maybe, just maybe we have a solution for them, but this is Ubuntu help forums.  Not windows.

---

### Post by Rocket2DMn on 2011-05-30
Given the state of this thread, I'm closing it.  If you're still having issues, please start a new support thread and keep it clean from pointless banter like we have here. Thanks.

---

