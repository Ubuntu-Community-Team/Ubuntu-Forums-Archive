---
title: "Use of PeToUSB+PeBuilder to perform a windows .exe bios update on ubuntu netbook?"
date: 2009-07-27
forum: General Help
---

### Post by artshark on 2009-07-27
Hey guys, I have a HP Mini 1000 with Ubuntu MIE on it, and theres an issue that can only be fixed with a firmware update. issue? the update is only available from HP as a windows exe. The solution my forum recommended is the following:
  		 							
[LIST]
[*][Report this post]("http://myhpmini.com/forum/report.php?f=6&p=9527")
[*][Reply with quote]("http://myhpmini.com/forum/posting.php?mode=quote&f=6&p=9527")
[/LIST]
 			 			**[Flash your bios  without Windows installed]("http://myhpmini.com/forum/viewtopic.php?f=6&t=1446&start=0#p9527")**

 			[[IMG]http://myhpmini.com/forum/styles/Blue-Crush/imageset/icon_post_target.gif[/IMG]]("http://myhpmini.com/forum/viewtopic.php?p=9527#p9527")by **[Masou007]("http://myhpmini.com/forum/memberlist.php?mode=viewprofile&u=1535")** » Fri May 29, 2009 11:27 pm 
  			 			Disclaimer: this worked for me, I don't know if it'll work for others.

On a Windows computer copy the contents of a Windows XP cd to a folder on your hdd

Download the latest BIOS for your mini, don't run the file.
Extract the contents of the file to a folder with WinRAR 

Download PE Builder [http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/) and PE to Usb [http://gocoding.com/page.php?al=petousb](http://gocoding.com/page.php?al=petousb) (if you wish to make a bootable usb key)

Run PE Builder
Set "Source" to the folder your Windows XP cd files are in
Set "Custom" to the folder your extracted BIOS files are

Leave media output to none if you're just doing USB
or
Change media output to CD/DVD if you prefer to burn a CD

Make your CD or use PeToUsb to make a bootable usb key

Boot up the PE environment from whichever media

Bring up the command line
cd \ to the root of the media and you will find your .EXE bios updater file. Run it and tada your BIOS will update

Again, do this at your own risk, make sure you're plugged into the charger.

It worked for me on a Mini 1110NR (Mi edition), with BIOS F.13

I am following these instructions to a T, and recieving an error upon boot with the drive as primary selected, I recive the following image,
"could not find kernel image: linux"
any pointers? were his directions faulty? are there other utilities i can use to achieve the same results? perhaps the disk of XP i downloaded was bad. i mean the back up cd i used :P
Thanks!

---

### Post by t4thfavor on 2009-07-27
I would use the freedos method, there are instructions everywhere how to make a bootable CD, or floppy. If that does not work (do some reasearch) There are prebuilt peIso's If you can get one from a 'reputable' source.


I have made them before, but its been so long, I cannot rememeber how to do it.


I think your kernel error is due to your SSD grub install, remove the internal hdd from the netbook, and try again.

---

### Post by artshark on 2009-07-27
> **t4thfavor said:**
> I would use the freedos method, there are instructions everywhere how to make a bootable CD, or floppy. If that does not work (do some reasearch) There are prebuilt peIso's If you can get one from a 'reputable' source.


I have made them before, but its been so long, I cannot rememeber how to do it.
thanks so much!

---

### Post by t4thfavor on 2009-07-27
Are you fixed? If so, what was the issue?

---

### Post by artshark on 2009-07-27
no, didn't try it yet. will post results when i do :)

---

