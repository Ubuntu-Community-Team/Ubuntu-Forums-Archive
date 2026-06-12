---
title: "&quot;CD ROM Won't Boot With Windows Installation CD&quot;"
date: 2009-10-16
forum: General Help
---

### Post by LinuXGo on 2009-10-16
Hi, I've recently try to install windows back into my computer but my computer won't boot from the installation CD?!! My problems now dealt with my computer unable to mount the CD inserted and I'm having problems with mounting process in which my computer unable mount the CD because its write protected, with read only option.  Currently I'm running an Linux (Ubuntu) Operating System using the SCII (SDA) Hard Drive, and you can post back whenever you think you need more information on this issue!!

---

### Post by MaindotC on 2009-10-16
Sorry but this has nothing to do with Ubuntu.

---

### Post by RandomP on 2009-10-16
Yup, this is not a problem with Ubuntu.

Did you try to  put the CD into the PC when it is starting up? If that did not work, then I think that you need to go into bios and configure it so it will boot from a CD if there is a CD in the the optical drive.

---

### Post by wojox on 2009-10-16
Can't you edit your bios to boot from cd first?

Or depending on your system you can press certain keys or key to do that. For example my Medion I press F8 after it boots and can choose " Boot from Hard Drive or CD-Rom "

---

### Post by mike555 on 2009-10-16
What are you trying to do? remove Ubuntu and install Windows? or dual boot? well anyway you might need to format whatever partition you want to install Windows on to NTSF , then hopefully your cd will see it.


 you should use a "live" cd to do that, Ubuntu or Parted magic .

---

### Post by LinuXGo on 2009-10-17
Well I'm running a Sony VAIO computer and I've tried to boot the CD with my computer. It didn't tell me what key to press or &quot;press any key to start setup&quot; option. So I see that Ubuntu OS had nothing to do with the Booting Process and someone told me that GRUB don't monitor CD drives so that eliminate things already..... they suspect that its a &quot;bad&quot; burn or a &quot;bad&quot; copy. But since I have another laptop in my disposal, I start the computer and insert the disc when the Os is loaded and the autorun command activates. So then the setup window appear, I wondering if there's something wrong with the Drive or the partition....either way, thanks for the reply and I hope someone post another soon....

---

### Post by Gizenshya on 2009-10-17
it could be any one of several problems.  Since the autorun works, that means that the iso was burned correctly.  Whether or not it was a bad burn would depend on a disk check.  I'm pretty sure at least some versions of windows has an option to check the disk, but I could be wrong.  I'd try to check it if there is such an option for your version.

It could be your CD drive.  Stick in a burned ISO from another bootable disk, such as the one you used to install Ubuntu.  If it starts to boot, then your drive is working properly.  I have a few (several) old (not so old... they only last a year or two) that work for some things, and not others.  A few of them work normally... but have somehow lost the ability to boot at computer startup.  If I want to boot from a CD or DVD... I have to use another drive.  Yours could have possibly gone bad in this way.

You have implied that you have made no changes to your BIOS.  I think this is the most likely culprit for your problem.  I'll save you the conspiracy theories as to why, but many computer manufacturers have stopped putting CD-ROM's (and other non-HDD drives) before the HDD's in the default BIOS boot order.  It is stupid and only causes problems, IMO... but that's the way they do it now.  You have to find out how to access the BIOS.

When your computer starts up there should be a screen for a second or two.  It will say Press (some button) for (something).  It may have several buttons and an option for each one.  Look for "to enter BIOS," "to select temporary boot device," "to enter setup," or anything that sounds similar to those, or anything that has the word "boot" in it.  Just press that button and you should probably be able to figure out how to set your CD-ROM to a higher boot priority than your hard drive.  If you can't, post the options here and we can help.

If there is no such screen, you'll have to guess at the keys (or google with BIOS access and your computer model number).  Some common keys are delete, F2, F12, F1, delete, F8, space bar, and tab.  I've seen Delete and F2 the most often I think.. but try them all until you find one that works.

Whatever button it is, just keep tapping it as soon as you hit the power button to turn on your computer.  The screen should appear.  If grub (or another boot manager menu) comes up, or an OS starts booting... then you weren't hitting the right button... so try another one.  All somputers have a BIOS, and all are accessed in the same way.  you just have to find the right button.

---

### Post by LinuXGo on 2009-10-17
Yeah okay, I see that I can access the BIOS setup utility by pressing the F2 button and view the boot order using the esc button. So I try some experiment with my DELL computer, first I pop the CD in and while its starting I press CTRL+ALT+DEL to reboot....but then the computer didn't list any message that notifies me that I had to press a button.....So then I went to My Computer, open the CD/DVD drive and it listed all the files inside the CD. The setup installation works only when you don't boot the computer....And so the CD/DVD drive turned to the name VRMPFPP_EN (F)... But then I saw the GRUB iso. file so I delete it since I don't know how it was there before.. So then I open up my VAIO computer and insert the CD while its started. Still nothing happens and so the operating system is loaded and can't seem to recognized my CD at all.... I don't know what happened but it seemed that the windows installation CD files can't be view due to some issues....  Also my BIOS has very little power over my computer so I can't seem to access my HDD in depth so.....And my model is an VGN series that was manufacture in the year 2004....

---

### Post by LinuXGo on 2009-10-17
All basically I want to do is that I need install a application that only windows are compatible with.... So I want to reinstall windows back to my computer (dual boot), someone implied that I should use VMware or Vbox as an alternative to this issue....but I only have 512MB of RAM which is not sufficient at all..... During the past I went to Ubuntu because my windows is screwed up like "always" and so I totally deleted the partition and roam totally with Ubuntu partition. Sadly I was not conceived that I need some applications that I needed, but soon enough I discover WINE, I thought this program could resolve my application issue. Ironically its still in development and most game window based application works best in wine due to high popularity, also as an alternative to my program people suggest that I utilize programs. Specifically, I brought an ipod touch and I hadn't foreseen this  problem..... itunes weren't available to Linux :( and then someone suggest that i use ifuse, that literally makes problems more or less problematic. All seemed lost but I find a petition online that urges apple developers to make a itunes that is available for linux, so far I hope that the WINE developers will make further changes to this applications......

---

