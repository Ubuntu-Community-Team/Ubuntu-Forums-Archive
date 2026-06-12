---
title: "Lost Ubunto boot option after windows cleanup"
date: 2010-07-29
forum: General Help
---

### Post by Reallyold on 2010-07-29
A Microsoft anti virus program (Security Essentials) cleaned out a bunch of problems in Windows XP and now I don't have the double boot option any more. What do I change to get Ubuntu option back?
OH, I also had to do a checkpoint restore prior to that but it was after I had installed Ubunto (I think). Which leads me to ask....how do I identify the Ubuntu disk space I allocated at install time? I can't seem to find it.
Thanks,
Bill K

---

### Post by aeiah on 2010-07-29
the antivirus software probably cleaned out (ie replaced) your master boot record. rootkits can live in there, but its also where grub goes. try either a super grub disk or tutorials for how to restore grub or grub2. what version of ubuntu have you got? you'll need to identify whether it used grub or grub2 as they are quite different.

i dont really understand your other question. in a gparted livecd or any other linux livecd you should be able to get a clear idea of your hard drive layout by using gparted

---

### Post by Reallyold on 2010-07-29
Well I am very new to Linux...about a week or so now since I installed 10.04. I put it on a USB drive, and this is what I am referring to when I say I can't find the Ubutnu space allocated on it (when I look at the disk in Windows Explorer).

Where do I find the "Grub" I need? I used Wubi to do the install. Can I just download Wubi again and run that? And...excuse the supreme ignorance.. once I get Grub what are the next steps? I don't see the relationship between all these pieces, and I don't know the Linux command language at all. 
Thanks for the response.....

---

### Post by Joker1134 on 2010-07-29
do [COLOR=Red]NOT[/COLOR] run wubi again.[COLOR=Black] it will delete your current ubuntu. this is what happened to me not to long ago.[/COLOR]

---

### Post by bcbc on 2010-07-29
> **Reallyold said:**
> A Microsoft anti virus program (Security Essentials) cleaned out a bunch of problems in Windows XP and now I don't have the double boot option any more. What do I change to get Ubuntu option back?
OH, I also had to do a checkpoint restore prior to that but it was after I had installed Ubunto (I think). Which leads me to ask....how do I identify the Ubuntu disk space I allocated at install time? I can't seem to find it.
Thanks,
Bill K
+1 on what Joker1134 said.

With wubi installs, there is a virtual disk that is the size you selected when you installed. It's called root.disk and it's in the \ubuntu\disks folder wherever you installed it. e.g. c:\ubuntu\disks\root.disk

You'll also need a wubildr file somewhere to boot into it. It's basically grub4dos (grub being the grand unified bootloader or something like that). Basically a bootloader boots an operating system.

What I would do is boot into an ubuntu live cd or usb (boot from an Ubuntu CD or USB and select "try without installing"), then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back. That way I should be able to see what's there and what's missing.

Also for future reference, here is the [wubi guide]("https://wiki.ubuntu.com/WubiGuide"). It has a lot of information that might be useful.

---

### Post by Reallyold on 2010-07-31
OK I've been searching documentation to see how I boot from the ubuntu live CD. I have the CD from which I installed Ubunto but is that what you call a "live CD"? If so how do I boot from it, and if not where do I download a live CD?
Thanks,
Bill

---

### Post by bcbc on 2010-08-01
> **Reallyold said:**
> OK I've been searching documentation to see how I boot from the ubuntu live CD. I have the CD from which I installed Ubunto but is that what you call a "live CD"? If so how do I boot from it, and if not where do I download a live CD?
Thanks,
Bill

Boot from the Ubuntu CD, and there'll be a screen with two options. The first is to try ubuntu without making any changes to your system.

---

### Post by Reallyold on 2010-08-05
I cannot see how to boot from the CD. I am including a snapshot of my screen showing the files on the CD. Which file do I go to for booting *_while running_* Windows XP? It will not boot at startup time or even TRY to read the CD while booting windows. 
Thanks,
Bill

---

### Post by sydbat on 2010-08-05
> **Reallyold said:**
> I cannot see how to boot from the CD. I am including a snapshot of my screen showing the files on the CD. Which file do I go to for booting *_while running_* Windows XP? It will not boot at startup time or even TRY to read the CD while booting windows. 
Thanks,
BillYou have to change your BIOS settings to make sure CD is first boot option. Reboot your box, then as it begins to start hit Delete to get into BIOS (might be another key that is normally listed in the initial boot screen).

Also, wubi is horrible. Because it relies on the Windows file system, it can become corrupted very easily. It is a good way to play with Ubuntu and try it out, but never a long term solution. Creating a separate partition for Ubuntu is always the best choice if you are planning on really using it.

---

### Post by bcbc on 2010-08-05
You need to tell the computer to boot from cd. You can do this either by changing the boot order in the BIOS or by hitting a boot options key at startup. What those keys are depends on your computer. e.g. on my computer the boot option key is F12.

---

### Post by Reallyold on 2010-08-05
OK I did that F12 at boot and I got the list of choices. Picked the one that said IDE CD drive and ....... the drive whirred and clicked and I still got Windows. 
So then I tried again and chose "Setup" and had the CD drive be the first place to go at boot time. Got the same results. 
Getting pretty discouraging trying to just get back into Ubunto.  I like it, I want it, but it's getting too time consuming. I just don't have weeks to spend on trying out a new operating system.
Plus, even if I DO get it to work, I'm really afraid that the next time my anti-virus program cleans out stuff I'll have to go through this whole exercise again.
There has to be a better way.....

---

### Post by bcbc on 2010-08-05
> **Reallyold said:**
> OK I did that F12 at boot and I got the list of choices. Picked the one that said IDE CD drive and ....... the drive whirred and clicked and I still got Windows. 
So then I tried again and chose "Setup" and had the CD drive be the first place to go at boot time. Got the same results. 
Getting pretty discouraging trying to just get back into Ubunto.  I like it, I want it, but it's getting too time consuming. I just don't have weeks to spend on trying out a new operating system.
Plus, even if I DO get it to work, I'm really afraid that the next time my anti-virus program cleans out stuff I'll have to go through this whole exercise again.
There has to be a better way.....

It sounds like the computer is trying to boot the CD, but finding it non-bootable, then going to the hard drive (based on the boot order). Therefore, the CD is probably a bad burn or some other issue, perhaps with the cd drive.

If you still have the root.disk (e.g. c:\ubuntu\disks\root.disk) you could just back that up, reinstall wubi, and copy the backup over the new root.disk. But make sure you backup the root.disk OUTSIDE the c:\ubuntu directory or it will be deleted when you reinstall.

---

### Post by Reallyold on 2010-08-05
I'm in the process of doing just that.....copying the backed up root disk before I reboot. 
Thanks for the suggestion. 

Guess I still have to figure out why my CD drive doesn't do what it's supposed to. I have tried burning 3 disks so far and none of them boots properly so it looks like the drive could be the problem.

---

### Post by JKyleOKC on 2010-08-05
When you burn the CD, use the slowest speed that your burner provides. Most default to maximum speed, and when creating boot CDs that's a great way to create a collection of coasters!

It's also possible that your Windows burner program is copying the ISO file itself to the CD, rather than burning the image. You can check for this possibility from Windows by using Explorer to view the CD. If you see a single ISO file there, it did NOT burn the image but merely copied it. I had to use NERO rather than the native WinXP burner to create true boot CDs; other third-party programs probably have similar capability. Look for "burn image" or words to that effect in the options, rather than "create DATA CD"...

---

### Post by Reallyold on 2010-08-05
OK, HELP again!!! The boot now becomes a Ubuntu/Windows option.......thank you thank you. Unfortunately I can't get past the grub command line to get into Ubuntu. What is grub looking for? I type EXIT or BOOT and go into the reboot loop. How do I get into Ubuntu desktop?

---

### Post by Reallyold on 2010-08-05
> **JKyleOKC said:**
> When you burn the CD, use the slowest speed that your burner provides. Most default to maximum speed, and when creating boot CDs that's a great way to create a collection of coasters!

It's also possible that your Windows burner program is copying the ISO file itself to the CD, rather than burning the image. You can check for this possibility from Windows by using Explorer to view the CD. If you see a single ISO file there, it did NOT burn the image but merely copied it. I had to use NERO rather than the native WinXP burner to create true boot CDs; other third-party programs probably have similar capability. Look for "burn image" or words to that effect in the options, rather than "create DATA CD"...

Could be true...in fact I did try to change the speed of the last CD I burned but the program choked and spit and gave me messages culminating in something like "sorry, that didn't work out" but the CD got partly written on (yup, coaster). I used a community-recommended burner program called InfraRecorder. Both times it went just fine at maximum speed but wouldn't work at lower speeds. But then, there were other options which I knew nothing about so it could well be my own ignorance about this software. 

The resulting CD had files in it which you may see on a screenshot in a previous post.

---

### Post by bcbc on 2010-08-05
> **Reallyold said:**
> OK, HELP again!!! The boot now becomes a Ubuntu/Windows option.......thank you thank you. Unfortunately I can't get past the grub command line to get into Ubuntu. What is grub looking for? I type EXIT or BOOT and go into the reboot loop. How do I get into Ubuntu desktop?

Maybe something happened to the root.disk. This is why I asked for the bootinfoscript. Not really sure what you can do here. Did you install to the same windows drive as before? If not, it's possible you could manually load wubi.

---

### Post by Reallyold on 2010-08-06
> **bcbc said:**
> Maybe something happened to the root.disk. This is why I asked for the bootinfoscript. Not really sure what you can do here. Did you install to the same windows drive as before? If not, it's possible you could manually load wubi.

Yeah, sorry about the bootinfoscript....I was so unable to even start Ubuntu (which was necessary to run bootinfoscript) that when I was finally able to start Ubuntu yesterday I had totally forgotten all about running bootinfoscript). So now that I CAN start Ubuntu from the CD I'll try it and post the results here. I'm still reading about how to run bootinfoscript.

---

### Post by Reallyold on 2010-08-06
Ya know, I'm about ready to give up here. I start Ubuntu from the CD and then start the browser to find bootinfoscript. Start to download it and after a minute or so Firefox just goes away and I get several messages telling me that this that and the other "thing" has had an error and must close, and do I want to send an error report. 

I say yes to all of them and after another while I get a screen asking me to join a user group and please register. Nuts! So I close all the little error screens which are still hanging there. I had also tried to start the file manager but that too went away leaving another error message. Seems like not much works. 

I WAS able to open a terminal to get the command line but didn't have much I could say to it.

---

