---
title: "&quot;Error: no such device&quot; - PC won't boot! PANIC!! HELP!!!"
date: 2010-06-14
forum: General Help
---

### Post by blehmeco on 2010-06-14
Guys!
 
i'm so sorry 4 my lack of serenity right now, but i'm really in panic about this situation i got myself into...and i desperately need your help!!...so let me try 2 explain...
 
I'm a rookie on this Linux stuff, but i wanted 2 give it a go so, having a Vista laptop full of stuff i burned couple DVD's 2 make way 4 Linux and i started with installing Wubi.
It installed Ubuntu 10.04 on a partition of my hard drive ( d: ) and everything was going as planned 4 a few hours.
I started 2 play with it and feeling comfortable...but then, after installing the updated nVidia drivers i realised i got the problem with ubuntu's low resolution boot screen (plymouth, right?) reported on this forum, so i tried some of the workarounds available, which meant messing around with GRUB...(grrrrrr!!!if only i had known!)...eventually i got myself into a black screen freeze after windows boot loader and GRUB loader, so i decided 2 unistall Ubuntu via Windows and then re-install via Wubi again, since i was enjoying the Ubuntu experience...
I re-installed and faced the same problem of the low res boot screen, so i tried a couple more solutions (again involving GRUB)...and then...
 
In one of that last workarounds, i belive i was supposed to delete GRUB to make way 4 GRUB2, though, apparently, judging by what i read on the terminal nothing was erased or installed...then, i restarted the PC, to see if the changes i had performed had any effect...
and to my utter terror after only the initial Asus screen, i didn't even saw windows bootloader and it went immediately 2 a black screen saying:
 
Error: no such device: 3ce6d759-47fa-
grub rescue>
 
after "device: " the numbers would continue, and i can post them entirely if any1 finds them useful!
 
right now, i'm desperate because as you probably might guess all my hard-work stuff is in that PC (in the Windows Vista bit), and i can't even start vista or boot the PC right now...
 
Don't know if it helps, but i tried putting a Windows Vista Recovery CD and restarting but it didn't even boot from the CD...
 
So i don't really know what's safe 2 do now and not safe...so...
Really appreciate your help out of this hole!
 
 
Lots of thanks in advance!
 
 
P.S. - Performed a search on the forums b4 posting, but didn't find a similar problem with the peculiarities of mine, but anyways, sorry if i posted wrongly here...

---

### Post by Timmer1240 on 2010-06-14
[http://www.ehow.com/how_5901191_fix-mbr-windows-vista.html](http://www.ehow.com/how_5901191_fix-mbr-windows-vista.html)  this may or may not help you depending on if you have a vista cd

---

### Post by Timmer1240 on 2010-06-14
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)   this is how to reinstall grub from a live ubuntu cd

---

### Post by Timmer1240 on 2010-06-14
This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:
find /boot/grub/stage1
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:
root (hd?,?)
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:
setup (hd0)
Finally exit the grub shell
Code:
quit
That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

---

### Post by blehmeco on 2010-06-15
1st of all huge thanks 4 listening and helping me out with this Timmer1240 ! Really!
 
 
> [COLOR=#000000][[COLOR=#000000]http://www.ehow.com/how_5901191_fix-...ows-vista.html[/COLOR]]("http://www.ehow.com/how_5901191_fix-mbr-windows-vista.html")[URL="http://www.ehow.com/how_5901191_fix-mbr-windows-vista.html"] this may or may not help you depending on if you have a vista cd 
[/URL][/COLOR]
 
I do have a Windows Vista Recovery CD that I got from the net some time ago (no, I didn't get a recovery cd along with my PC when I bought it), and I tried restarting and putting it in, but it didn't boot from the CD...that's one of the things that got me seriously worried!...
 
I am now downloading and burning a Ubuntu Live CD to see if it'll boot from there so that i get access to a terminal or something that can get me 2 the point where I can restore Windows bootloader, to start windows and unistall Ubuntu (at least 4 now!)...
 
What I'm fearing is that the PC won't boot from that CD either!...is that possible?... what'll I do then? (you see, that was what really got me worried!...)
 
Report back my results with Ubuntu's Live CD just as soon as i get them!
 
 
Thanks again!

---

### Post by blehmeco on 2010-06-15
So i managed 2 get into the motherboard's options, and checked that i had the system primarily booting from the CD, however restarting the PC with Ubntu's Live CD in, resulted in the same behaviour as for the Vista Recovery CD...meaning: right after the initial Asus screen (2 seconds) I got 2 the same "Error: no such device" message...
 
i'm now wondering if this might b related 2 my CD/DVD drive, since I've had recurrent failed DVD recordings with it...hmmm...i don't think it's likely, but do you think I should try changing the primary boot to Pen drive and then boot from a pen drive or do you have any idea what might b the problem here?...i mean, am I doing anything wrong? Or do you have any better ideas?
 
By the way, I would prefer to recover Windows Vista 1st, so that I could uninstall Wubi (and therefore Ubuntu) and start clean again...writing Grub over MBR, won't I be erasing the possibility 2 start the PC with Windows, and that way not being able to access my data and subsequentely not correcting the problem with the uninstall of Wubi in Windows?

---

### Post by blehmeco on 2010-06-15
No luck...YIKES!...guess the CD/DVD drive isn't the problem since I couldn't boot Windows Recovery or Ubuntu Live from the pen drive either... man I'm screwed... really don't know what 2 do now...
 
just one thing, after that "Error: no such devide: blah-blah-bah" i get a new line in a command-line fashion, saying "grub rescue>", is that the same as "grub>"?
I mean, should I enter the codes you've showed me here?

---

### Post by dnguyen1963 on 2010-06-15
> **blehmeco said:**
> No luck...YIKES!...guess the CD/DVD drive isn't the problem since I couldn't boot Windows Recovery or Ubuntu Live from the pen drive either... man I'm screwed... really don't know what 2 do now...
 
just one thing, after that "Error: no such devide: blah-blah-bah" i get a new line in a command-line fashion, saying "grub rescue>", is that the same as "grub>"?
I mean, should I enter the codes you've showed me here?

Use the instructions by Timmer1240 to re-install Grub.  You should be fine.

---

### Post by blehmeco on 2010-06-15
> **dnguyen1963 said:**
> Use the instructions by Timmer1240 to re-install Grub. You should be fine.
 
But you mean these instructions?
 
> **Timmer1240 said:**
> This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands
 
Code:
find /boot/grub/stage1
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
 
Code:
root (hd?,?)
Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)
 
Next enter the command to install grub to the mbr
 
Code:
setup (hd0)
Finally exit the grub shell
Code:
quit
That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.
 
Or these?
 
> **Timmer1240 said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) this is how to reinstall grub from a live ubuntu cd
 
Because as I have explained before I can't seem to boot from Ubuntu Live CD, so I can't perfrom the instructions on quote no.2!

---

### Post by Timmer1240 on 2010-06-15
If you get to the grub rescue prompt which you said it did you should be able to run the commands in my 3rd post!

---

### Post by blehmeco on 2010-06-15
It's saying "Unknown command 'find'"!

---

### Post by wilee-nilee on 2010-06-15
You will need to post the script in my sig in code tags to see whats really going in in one fell swoop. Relax a few serenity nows might help.;)

---

### Post by blehmeco on 2010-06-15
Ok!...and thanks for the chill out mood! I'm definately needing it...that and solving this thing! ;D
 
Sorry for the rookiness, I've just downloaded your Boot Info Script, but since I can't start a Ubuntu Live CD on my PC, how can I run it?...i mean, should I put it on a pen drive? But then what would the path 2 to it be?

---

### Post by wilee-nilee on 2010-06-15
> **blehmeco said:**
> Ok!...and thanks for the chill out mood! I'm definately needing it...that and solving this thing! ;D
 
Sorry for the rookiness, I've just downloaded your Boot Info Script, but since I can't start a Ubuntu Live CD on my PC, how can I run it?...i mean, should I put it on a pen drive? But then what would the path 2 to it be?

So not knowing how you downloaded it, the script can be run from a running Ubuntu which you don't seem to have or a live cd or a thumb that boots Ubuntu or a Linux variant. You just need terminal access in a Linux environment.

So why can't you boot a cd?

---

### Post by blehmeco on 2010-06-15
It's like I explained on the 1st post:
 
When I start the PC with a CD inside (be it Ubuntu Live CD or Windows Vista Recovery CD) I get an Asus splash screen and after a brief couple of seconds the message "Error: no such device: blah-blah-blah" on line 1 and on a 2nd line "grub rescue>_" just like a command-line prompt...
 
Note: if I start the PC without a CD the only difference is that there is no couple of seconds between Asus' splash screen and the error message.
 
Note 2: apparently I was able 2 get into the motherboard definitions (pressing F2 on Asus' splash screen) and was able 2 make sure that it was set 2 primarily boot from CD/DVD.
 
Note 3: I have also tried putting the contents of Vista Recovery CD and then Ubuntu Live CD onto a Pen drive, changing the boot order to pen drive 1st, and then rebooting, but the result was the same: after a brief couple of secs reading the pen (I believe it was reading the pen because the light on the pen blinked) the error message showed up...

---

### Post by wilee-nilee on 2010-06-15
I think your relying on the computer having the cd in the bios settings. You will like accessing bios a key prompt to choose the booting device mine is f12 here are others mentioned on a quick asus search F2, F8, F12. Most any computer has this option, a key prompt after hitting the power button for bios and another for a choice of boot devices. Your computer unless the firmware in bios is borked will boot from a cd with the right key prompt, or the disc reader not working..

---

### Post by wilee-nilee on 2010-06-15
From this link it appears some use esc as the boot choice menu prompt.
[http://forum.notebookreview.com/asus/191231-how-can-i-boot-cd-first.html](http://forum.notebookreview.com/asus/191231-how-can-i-boot-cd-first.html)
Once you know this prompt you will never have to use the bios to organize the boot order.

---

### Post by blehmeco on 2010-06-15
You are right! Pressing Esc brings up a boot option screen...however when I select boot from the CD/DVD drive it shows the same "error: no such device"...

---

### Post by wilee-nilee on 2010-06-15
> **blehmeco said:**
> You are right! Pressing Esc brings up a boot option screen...however when I select boot from the CD/DVD drive it shows the same "error: no such device"...

Is this a ubuntu cd that has booted before? and are making sure that the cd is being picked?

---

### Post by blehmeco on 2010-06-15
Sorry I took a bit longer there!
 
I restarted this desktop I'm writing to you on with the Ubuntu Live CD I've got, and I can confirm it is in fact working well! (I only have XP on this Desktop and i was able to go all the way and open Terminal in Ubuntu using the Live try option! So, yeah, it's working!)
 
And yeah! I'm sure I picked the CD as the boot option (pressing Esc on Asus' splash screen I get the option of the HDD and the CD/DVD drive, which is the screen you told me about)!
 
Strangely enough now, I thought it could well be a problem with the CD/DVD drive, so:
i copied the files in Ubuntu's Live CD to a Pen drive and tried booting from the Pen drive by pressing Esc at Asus' splash screen and choosing the Pen drive, and i got a different message: "Missing Operating system"
 
Oh boy...should I be worried now? Or did I do anything wrong when building the Pen wih Ubuntu's Live CD?

---

### Post by wilee-nilee on 2010-06-15
> **blehmeco said:**
> Sorry I took a bit longer there!
I restarted this desktop I'm writing to you on, with the Ubuntu Live CD I've got and I can confirm it is in fact working well! (I only have XP on this Desktop and i was able to go all the way and open Terminal in Ubuntu using the Live try option! So, yeah, it's working!)

Excellent, so post the script so we can make sure XP is in good shape to proceed. You have learned a couple of key things here, that will be of great help in the future, good job sticking with it. ;)

You can just come to the UF on the live cd to post the script in code tags. I may not even have an answer but the script is important in the detail that it has in it.

---

### Post by blehmeco on 2010-06-15
Hmmm... I believe you may have misunderstood me, my PC is a laptop, whereas the PC from where I am writing to you is a desktop.
 
What I intended to say was that I was able to check on this _desktop_ (that's working just fine, and where I have only XP installed, not Ubuntu) that the Live CD I burned earlier today is working as it should.
However, it is not working as a bootabloe Live CD on my other PC, which is a _laptop_ (and is not working properly since I messed up its GRUB after installing Ubutu with Wubi 4 the 1st time ever!)
 
So, on that _laptop_ I tried to boot from the Live CD and it didn't work, returning the same "error: device not found etc" error as it did without booting from the HDD.
 
Suspecting that I could be having a problem with the DVD/CD drive I then tried copying the files in that Ubunu Live CD I created, onto a USB Pen Drive and booting from there, and so, this time, on the laptop I got a different error message: "Missing Operating system"...

---

### Post by wilee-nilee on 2010-06-15
So use unetbootin to load the thumb or pendrive and see if it boots with a key prompt on the laptop.

So you have a working desktop and a broken laptop is this correct?

It is hard for me to remember every single thing at times, also when we are incorporating new learning for you with the process, I have to keep track of a lot of information and my brain is about the size of a walnut.;)

---

### Post by blehmeco on 2010-06-15
Ok, sorry, again, 4 my rookiness... that's not the way to build a bootable Ubuntu Live USB Drive!... my mistake!
 
So i'm going to build a Ubuntu Live USB properly, try it out and report back to you as soon as I get results!
 
BTW, I suspect the CD/DVD drive on my laptop isn't working as it should! That's why I'm trying this b4 looking out 4 other solutions!

---

### Post by blehmeco on 2010-06-15
That is correct, i own a Desktop that's working properly and a Laptop that's broken which triggered this thread!
 
Be back with the results from the boot from the Pen drive as soon as I get them!
 
Oh! And I don't mind explaining everything in detail as many times as necessary since you are helping me out with my problem and in the process even managing to enlighten me on some new stuff that I'm actually interested in learning!
I can't help but thanking you!
 
Surely, walnuts must be getting bigger these days! ;-)

---

### Post by wilee-nilee on 2010-06-15
> **blehmeco said:**
> That is correct, i own a Desktop that's working properly and a Laptop that's broken which triggered this thread!
 
Be back with the results from the boot from the Pen drive as soon as I get them!
 
Oh! And I don't mind explaining everything in detail as many times as necessary since you are helping me out with my problem and in the process even managing to enlighten me on some new stuff that I'm actually interested in learning!
I can't help but thanking you!
 
**Surely, walnuts must be getting bigger these days!** ;-)

Sometimes there cracked .;)

---

### Post by wilee-nilee on 2010-06-15
So even if we get the thumb to boot the laptop and get the script posted and all you need is the MS bootloader installed, it needs to be done with the recovery cd. 

So you may have a recovery partition, but this will overwrite windows erasing your data we don't want this obviously. But worse case scenario the bootable thumb of Ubuntu can be used to pull stuff out if it comes to a recovery from the partition.

Do you have a extra cd drive you can plug into the laptop, or are the problems with the cd part of knowing the key prompt to boot from a cd? Or does the cd/dvd drive just need a little shot of air to clean the lens? So tell me the model at some point as well.

Also what is the desktop running as a operating system?

Edit now I have used this link to load a XP ISO to a thumb and I think it will probably work with the neosmart recovery ISO so we maybe able to get that recovery onto a thumb that boots to fix the laptop.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/](http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/)

I am assuming though that the laptop can boot from a usb to begin with.

The good thing though is that in the end if the cd reader in the laptop can be gotten to work, there is a program called plop that will enable a computer, to old to boot from a thumb, to do so, but it has to be burned to a cd to work. This could just be useful if needed. If the cd/dvd reader can be gotten to work on the laptop the recovery cd can be used as recovery.

---

### Post by dnguyen1963 on 2010-06-16
> **blehmeco said:**
> You are right! Pressing Esc brings up a boot option screen...however when I select boot from the CD/DVD drive it shows the same "error: no such device"...

Did you somehow disable your CD-ROM?  Go to your computer Bios and make sure that the CD-Rom is still enabled.  If you are able to boot the live CD on your desktop then the disk is fine.

---

### Post by blehmeco on 2010-06-16
Ok, so the Desktop that's working ok is running Win XP.
The Laptop that's not working right now is (had been) running Win Vista.
 
I do have a Windows Vista Recovery CD, which I needed a couple of years ago when a Vista Update went badly wrong, so I know 4 a fact that that Recovery CD works properly.
 
I don't have an extra CD drive, but, if I can't get things to work with a Pen Drive I can ask a friend of mine to loend me is CD drive that links by USB to the PC.
 
Before all of this happened (me messing up Ubuntu and ultimately my PC), the CD/DVD drive of my Laptop had been returning a lot of failed DVD burns, so I actually stopped using it. I didn't fix it because I was already out of warranty when this happened and besides the good people at Asus wouldn't garanty the safety of my data if I sent it for fixing.
When I needed to burn a DVD with data on my laptop I found a way of using the Disc drive from my desktop via a Wireless Network share (it worked basically like this: on the Desktop with XP and the good drive I used Alcohol 52% with the share option on; on the Laptop with Vista and the defective DVD drive i used Windows iSCSI Initiator to recognize the shared drive; this way the good drive of the desktop with show up on the laptop as its own drive, allowing me to burn stuff from the Laptop's HDD without moving the files to the desktop PC).
The model is:
3M-MATSHITA DVD-RAM UJ-860S
 
I'm not quite sure if the problem with the laptop's disc drive is as simple as just cleaning it, but anyway I wouldn't know how to do that properly... lately it was reading DVD's really slowly and it always returned failed DVD burns, could a badly cleaned DVD drive be the reason for this?
 
The key prompt to allow me to choose which device to boot from is "Esc" on my Laptop just as you told me, so no problem there!
 
Yes, I am confident that this laptop PC can be booted from the USB Pen drive though!
 
 
 
So now I'm building the Ubuntu Live USB pen drive to get the results from the script, post it when I'm done!

---

### Post by blehmeco on 2010-06-16
> **dnguyen1963 said:**
> Did you somehow disable your CD-ROM? Go to your computer Bios and make sure that the CD-Rom is still enabled.
 
Nope! it's enabled!
As far as I can tell from the boot priority options on my BIOS settings it is still enabled!
 
I believe the Disc drive is not working properly now because it is just as faulty now as it was before all of this happened!

---

### Post by blehmeco on 2010-06-16
Good news guys! (finally!) \\:D/

I managed to boot from Ubuntu Live USB and get the Boot Info Script, so without further delay:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    14,338,047    14,336,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     14,338,048   170,627,071   156,289,024   7 HPFS/NTFS
/dev/sda3         170,627,072   312,578,047   141,950,976   f W95 Ext d (LBA)
/dev/sda5         170,629,120   312,578,047   141,948,928   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
5 heads, 32 sectors/track, 49600 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,935,999     7,927,936   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       3ce6d759-47fa-4d89-8ab0-84d647a91786   ext4                                     
/dev/sda1        1489-5F00                              vfat       RECOVERY                      
/dev/sda2        0EBAA2C9BAA2ACA1                       ntfs       VistaOS                       
/dev/sda3: PTTYPE="dos" 
/dev/sda5        2C8AA70C8AA6D21E                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        D809-DCED                              vfat       KINGSTON                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2c8aa70c8aa6d21e
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,5)'
search --no-floppy --fs-uuid --set 2c8aa70c8aa6d21e
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=pt
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=2
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-22-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2c8aa70c8aa6d21e
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro  splash vga=769  quiet splash
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-22-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2c8aa70c8aa6d21e
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-22-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single  splash vga=769
    initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2c8aa70c8aa6d21e
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro  splash vga=769  quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, Linux 2.6.32-21-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set 2c8aa70c8aa6d21e
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single  splash vga=769
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 1489-5f00
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 0ebaa2c9baa2aca1
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


   8.8GB: boot/grub/core.img
   9.0GB: boot/grub/grub.cfg
   9.0GB: boot/initrd.img-2.6.32-21-generic
   9.1GB: boot/initrd.img-2.6.32-22-generic
    .1GB: boot/vmlinuz-2.6.32-21-generic
    .6GB: boot/vmlinuz-2.6.32-22-generic
   9.1GB: initrd.img
   9.0GB: initrd.img.old
    .6GB: vmlinuz
    .1GB: vmlinuz.old
```
Just hope this gives you enough info to get somewhere!
To tell you the truth, just the fact that I was able to get past that ugly "Error: no such device" error was such a huge relief! phew!
thanks 4 the help guys! Feeling closer to a solution now!

So, what's next? :D

---

### Post by wilee-nilee on 2010-06-16
Welcome back and you got into the laptop yay. So to me it seems at the least a working cd/dvd drive is needed to run the recovery disc. Since grub is in the mbr, and it should be the vista bootloader. Without at the least reloading the mbr I don't know how to do anything here. There are people on line who could help but may have not commented do to no working cd/dvd player maybe.

At this point since you have access to the Vista partition with the pendrive, you should back up the stuff off of vista you can't afford to lose. It is quite possible that since there is no working cd/dvd player that your dead in the water until you have one that works.

The sdb is the pendrive correct? it looks to be 8 gigs is this correct? and what program did you use to load it?

Edit; also do you have any other thumbs or a external hard drive?

It may be that the recovery can be loaded onto a thumb via the link I posted for loading a thumb with MS installs, we wouldn't know unless we tried.

---

### Post by blehmeco on 2010-06-16
"sdb" is the pen drive and it is a 4GB one...
 
To build this pen I followed the instructions here:
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
though I already had Ubuntu's Live CD .iso file which made things quicker on step 2.7!
 
Then with the Laptop PC off I plugged the Pen drive, then turned on the PC, imediately pressed "Esc" and chose to boot with the Pen drive!
As simple as that!
 
 
> **wilee-nilee said:**
> So to me it seems at the least a working cd/dvd drive is needed to run the recovery disc. Since grub is in the mbr, and it should be the vista bootloader. Without at the least reloading the mbr I don't know how to do anything here. There are people on line who could help but may have not commented do to no working cd/dvd player maybe.
 
At this point since you have access to the Vista partition with the pendrive, you should back up the stuff off of vista you can't afford to lose. It is quite possible that since there is no working cd/dvd player that your dead in the water until you have one that works. 
 
 
> **wilee-nilee said:**
> 
Edit; also do you have any other thumbs or a external hard drive?
 
It may be that the recovery can be loaded onto a thumb via the link I posted for loading a thumb with MS installs, we wouldn't know unless we tried.
 
This was exactly what I was going to ask!...
I've got other Pen drives yes, but not an external HDD! (though if it turns out 2 be absolutely necessary I can also borrow one from my friends)
 
So I've been looking on that links you sent and others to but didn't find a clear cut way 2 build a Vista Recovery Pen Drive!... but maybe I'll go with the simpler one and see where I can get:
 
[http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/](http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/)
 
In any case do you think it's safer to ask for my friend's External USB DVD Drive+Vista Recovery CD than using a USB Pen drive as Vista Recovery?
Or am I at the same risk of loosing data either using the External USB DVD drive or the USB drive to Recover Windows' bootloader?
One more thing, surely, in any case I should copy all the data I can access via Ubuntu's Live USB drive to an external HDD before attempting any of these options for the risk of loosing data, right?

---

### Post by wilee-nilee on 2010-06-16
> **blehmeco said:**
> "sdb" is the pen drive and it is a 4GB one...
 
To build this pen I followed the instructions here:
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
though I already had Ubuntu's Live CD .iso file which made things quicker on step 2.7!
 
Then with the Laptop PC off I plugged the Pen drive, then turned on the PC, imediately pressed "Esc" and chose to boot with the Pen drive!
As simple as that!
 
 

 
 

 
This was exactly what I was going to ask!...
I've got other Pen drives yes, but not an external HDD! (though if it turns out 2 be absolutely necessary I can also borrow one from my friends)
 
So I've been looking on that links you sent and others to but didn't find a clear cut way 2 build a Vista Recovery Pen Drive!... but maybe I'll go with the simpler one and see where I can get:
 
[http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/](http://www.intowindows.com/how-to-create-bootable-windows-7-vista-or-xp-usb-flashpen-drive-with-a-single-click-must-try/)
 
In any case do you think it's safer to ask for my friend's External USB DVD Drive+Vista Recovery CD than using a USB Pen drive as Vista Recovery?
Or am I at the same risk of loosing data either using the External USB DVD drive or the USB drive to Recover Windows' bootloader?
One more thing, surely, in any case I should copy all the data I can access via Ubuntu's Live USB drive to an external HDD before attempting any of these options for the risk of loosing data, right?

Your at risk of losing the data no matter how you try to fix the original vista. So backing it up is the first thing to do. If you can get the data onto a external HD that is the best way to go and always back up that way.

It may be that at this point corruption in vista will keep it from being usable even if accessed by reloading the master boot record, I'm speculating but you want to be prepared for any possibilities. Can you get the OEM disc set for this computer if it is a OEM from the computer maker. 

You have a recovery partition, it looks like, sda1, it is interesting that the boot flag is on the main sda2 partition though, but that is not the main problem since grub is in the MBR.

I am not real familiar with wubi installs, but I think sda5 was not needed as part of the install. Wubi is set to build a file in windows and building a partition I believe can create problems, but like I said I'm not sure here.

Edit:To be honest pulling out the data and the oem disc set would fix this quickly, and you could get rid of the recovery when reinstalling with the oem. You wouldn't need the recovery if you had the install cd's and a recovery cd for problems. The set up is fairly convoluted at this point. Personally I am a reinstall person when things go bad or are a longer more complex fix then just reinstalling. But I keep everything backed up on a external HD so I can reinstall at any time.

---

### Post by blehmeco on 2010-06-16
Ok! Going to get an external HDD to copy the data from Vista partitions then!
 
If it helps to understand why the boot flag is in the 2nd partition:
I believe I had a partition with Vista recovery stuff (probably "sda1"), then another one with Vista installed ( "C:" ; very likely "sda2") and a 3rd one for data ( D: ; suppose it's "sda5" from your "Results.txt").
I installed Wubi on that D: drive...
 
Already got my OEM disc ready 2!
 
Meanwhile, I've just tried building a Vista Recovery CD using "Novicorp_WinToFlash_0.6.0005_beta" and the .iso file made available through torrent download here:
 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
 
(which is also the .iso file I used to build the Vista Recovery CD I own)
 
however the program says it's not a valid Windows files source... so guess I'll have to download a Windows Vista .iso... you don't happen to know a good one, do you? ;-)

---

### Post by blehmeco on 2010-06-16
Your last Edit made me think... "what if I turned this mistake into a good thing?"...
 
Let me share this with you, the main reasons that convinced me 2 try Ubuntu was the sheer speed and praticality it offers in procedures (i can have my Laptop ready 2 use firefox, for example, in less than 20secs from off state!), not 2 mention Open-source, the free stuff and the community...
And honestly, lately Windows Vista was becoming impossibly slow at times, with no resasonable explanation 4 it!...
So my idea now, is: 
1 - Back up all my data
2 - Format the PC laptop entirely
3 - Start from scratch with this Laptop PC and forgetting Vista and the crappy Asus OEM applications
4 - Get a Windows 7 DVD (somewhere ;-) ) and install Windows 7 creating 2 partitions and using it more for work stuff (I need Win 7 because I still need some Windows applications like Office, Photoshop, Illustrator, iTunes and ocasionally gaming)
5 - Install Ubuntu on the 2nd partition and use it mainly for the immediate fun stuff (surfing the web, emailing, etc.), and if I happen to find the adequate software maybe using it for work stuff 2!
6 - Live happily ever after
 
It seems a good idea to me, what I'm not sure is which 1 to make my primary OS, Win 7 or Ubuntu... i mean, I would like it to b Ubuntu, but I know in the end (or at least in my first year usingUbuntu) i'll always need some Windows stuff... and which partition would b larger?...hmmm...guess it could b 50/50 because either system can access each other files, right?... i mean, if there is a good alternative to iTunes on Ubuntu, I can use it 2 play/edit my .mp3 or .mp4 files when I'm on Ubuntu and still use iTunes to acces/modify the same files when I'm on Windows, right?....
 
What do you say? Have any better ideas? Suggestions?
I'm thinking of finally taking a leap forward here!
And this time I want to make it right!... care to throw some advice or valuable knowledge/experience here?
 
thanks!

---

### Post by wilee-nilee on 2010-06-16
> **blehmeco said:**
> Your last Edit made me think... "what if I turned this mistake into a good thing?"...
 
Let me share this with you, the main reasons that convinced me 2 try Ubuntu was the sheer speed and praticality it offers in procedures (i can have my Laptop ready 2 use firefox, for example, in less than 20secs from off state!), not 2 mention Open-source, the free stuff and the community...
And honestly, lately Windows Vista was becoming impossibly slow at times, with no resasonable explanation 4 it!...
So my idea now, is: 
1 - Back up all my data
2 - Format the PC laptop entirely
3 - Start from scratch with this Laptop PC and forgetting Vista and the crappy Asus OEM applications
4 - Get a Windows 7 DVD (somewhere ;-) ) and install Windows 7 creating 2 partitions and using it more for work stuff (I need Win 7 because I still need some Windows applications like Office, Photoshop, Illustrator, iTunes and ocasionally gaming)
5 - Install Ubuntu on the 2nd partition and use it mainly for the immediate fun stuff (surfing the web, emailing, etc.), and if I happen to find the adequate software maybe using it for work stuff 2!
6 - Live happily ever after
 
It seems a good idea to me, what I'm not sure is which 1 to make my primary OS, Win 7 or Ubuntu... i mean, I would like it to b Ubuntu, but I know in the end (or at least in my first year usingUbuntu) i'll always need some Windows stuff... and which partition would b larger?...hmmm...guess it could b 50/50 because either system can access each other files, right?... i mean, if there is a good alternative to iTunes on Ubuntu, I can use it 2 play/edit my .mp3 or .mp4 files when I'm on Ubuntu and still use iTunes to acces/modify the same files when I'm on Windows, right?....
 
What do you say? Have any better ideas? Suggestions?
I'm thinking of finally taking a leap forward here!
And this time I want to make it right!... care to throw some advice or valuable knowledge/experience here?
 
thanks!

I think your on the right track, here is a W7 home upgrade which you qualify for if you were the original owner of the laptop with vista. Although the original owner is a technicality that I doubt would be asked by MS, they want you to use their products.
[http://www.newegg.com/product/product.aspx?Item=N82E16832116713](http://www.newegg.com/product/product.aspx?Item=N82E16832116713)

I am assuming you can buy a upgrade, you should check to make sure.

In the end you will need a working cd/dvd reader though. I got a nice mini slim one from Amazon for my net book for 50$ US.

---

### Post by wilee-nilee on 2010-06-16
Actually I wasn't thinking MS has a thumb loader for W7 so you could have the purchased dvd loaded onto a thumb from your XP desktop and install with no problem and have a dedicated thumb for repairs.
[http://wudt.codeplex.com/](http://wudt.codeplex.com/)
You can get tis tool all over the net. As far as I know it only works on a validated MS product though, and W7 only.

---

### Post by blehmeco on 2010-06-16
Thanks! I'll check if I qualify 4 an upgrade!
 
Meanwhile, while I'm waiting to get an external HDD from my friends, could you direct me to the best and most reliable way of setting up a dual boot system (Win7+Ubuntu) in your opinion?
 
And your also like to have your personal opinion on this...i mean, in my situation right now, what would you do?
And which OS(s) would you install? Only Ubuntu? Do you believe one could live only on Ubuntu?
 
Thanks again!

---

### Post by wilee-nilee on 2010-06-16
I think Ubuntu is a good starting OS, you can add the Kubuntu desktop or Xubuntu or lxde or others if needed. There are 100's of Linux distros so I think it is personal preference here and how much you want to learn to make things easier. Some like Mint Linux because it comes with media codecs, but personally I know where to get the codecs so I use Ubuntu and many others. Ubuntu is pretty straight forward as far as accessing synaptic or the terminal for updates and upgrades.

A dual boot would just consist of installing W7, then using it's disk manager to shrink the partition leaving a open space. Then installing Ubuntu or which ever you like in the open space, the installer would basically ask install in the largest free space. The key to the Ubuntu install is making sure that when your installing is that you check the advanced button in the last install window and that grub is going to the mbr=sda only. 

Many users like to have a separate home from the OS in Linux so that they save stuff and settings that way, I don't use this method, I just have a external HD to save to. I also try out all different types of OS so I don't like relying on the computer to not break at some point.

I would have a extra ntfs partition to be read by both operating systems so you could just access it from either one.

From my experience though with my own W7 upgrade, the activate key worked fine when I installed with a activated XP being the upgrade from, on the HD. Each additional install though without this has taken a legitimate ms software crack to get to the phone auto activation of the key or talking with a MS rep to activate.

This guide is pretty good and describes how to preformat the W7 partition so you don't have to shrink it.
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

Edit: we could even set you up with dual booting on the desktop as well, and since you would put the install in a extended partition, you could have Ubuntu and a whole series of others installed and have a whole handful of OS systems to choose from. The key is knowing how to do a custom install of Linux and one swap, and really for ease of travel all using grub2 so it is a automatic loading grub menu at boot.

This also applies to the laptop as well, with a little knowledge, your friends would think your the geek lol and you would be turning down their need for help when they borked their MS systems if thats what they use. MS is good but has some problems that aren't as easily fixed like a open source OS, and at this time a big target for the nasty-ware.

---

### Post by dnguyen1963 on 2010-06-17
> **blehmeco said:**
> Thanks! I'll check if I qualify 4 an upgrade!
 
Meanwhile, while I'm waiting to get an external HDD from my friends, could you direct me to the best and most reliable way of setting up a dual boot system (Win7+Ubuntu) in your opinion?
 
And your also like to have your personal opinion on this...i mean, in my situation right now, what would you do?
And which OS(s) would you install? Only Ubuntu? Do you believe one could live only on Ubuntu?
 
Thanks again!

Ok, when you have a working CD/DVD drive, you'll want to do a full install of Windows 7 on your computer (use the entire HD).  Start the Ubuntu install from the live CD.  Use Gparted to split the HD 50:50 between W7 and Ubuntu (defrag the HD if you have downloaded a lot of data after W7 installation).  You should be good to go.  You can choose which OS to boot when you start up your computer.

---

### Post by wilee-nilee on 2010-06-17
> **dnguyen1963 said:**
> Ok, when you have a working CD/DVD drive, you'll want to do a full install of Windows 7 on your computer (use the entire HD).  Start the Ubuntu install from the live CD.  Use Gparted to split the HD 50:50 between W7 and Ubuntu (defrag the HD if you have downloaded a lot of data after W7 installation).  You should be good to go.  You can choose which OS to boot when you start up your computer.

Thanks for your interest but using gparted to resize W7 is not a suggested way. W7 has a virtual disk manager that will resize while in the running system and **is** the suggested method, by everybody.

W7 doesn't have a auto chkdsk like XP so doing it this way can break it quite easily.

---

### Post by blehmeco on 2010-06-17
G! Thanks a lot 4 those last 2 posts guys! Really helpful!
 
I still don't have my friend's External USB HDD or External CD/DVD Drive, so I'm taking that chance to anticipate the difficulties/mistakes I might be facing in the (hopefully near) future...
 
So, here r my most recent difficulties/uincertainties:
1 - If my internal HDD has 3 parttions (#1-Recovery; #2-Vista OS and other stuff; #3-Data), if I format it and install a new OS like Win 7, won't I be loosing that Recovery partition 4ever? If so, what will I be loosing here? I have an Assus Recovery DVD, and on that DVD it's printed that the software included in this DVD only works on your Asus PC and that its contents have been factory pre-installed on the PC, does that mean I can always use that DVD (even without that partition) to get my PC back to Vista and its after-bought condition (OS-wise imean).
 
2 - About the distros, I think I'm going to start with Ubuntu and then, after I get comfortable with it I might consider some other distro more suited 2 my needs; question is, how do I prepare my system to be open to the install of more than one distro in the Linux partition? (we're talking about doing it right, with the same Grub2 and all, like wilee-nilee mentioned).
 
3 - I don't own an external HDD, and I'm not thinkin about buying one 4 now, and my internal HDD is a 160GB one, which I belive is enough 4 my needs right now; considering this setup, do you guys think I should create a 3rd NTFS partition where I'd store all my data and leave the OS's in separate partitions? Seems like a good idea in theory, but then how would I decide the size of the partition 4 each of the OS's and the size of the 3rd "only-for-data" partition?
 
4 - so, there's at least 2 easy ways of setting up a dualbooting system: 1 - Fully Install Win7 then shrink the drive and install Ubuntu on the remaining free space; 2 - Install win7 fully and defrag the HDD, then boot into Ubuntu's Live CD, use Gparted to partition the drive in the proportition that I want, and install Ubuntu on partition #2. Which of these methods is safer/better in your opinion? [COLOR=red]EDIT: I suppose it's No.1 then! [/COLOR]Will both of these methods lead to the same setup? I mean will they both offer the option to choose 1 of the OS's to start on boot?
 
5 - Do you know of any methods of using Ubuntu Live CD or any Linux apps to check why my DVD drive is malfunctioning? Or diagnosing it?
 
6 - Are there any known/common mistakes/incompatibilities/limitations that you think I should be aware of before building this dualbooting system with Win7/Ubuntu 10.04 LTS?
 
 
Again thanks for the help and patience guys!...Seems like there will be some green grass coming out of this rough patch!
 
Any other heads up or important info you may want to throw b4 I go on, please do!

---

### Post by wilee-nilee on 2010-06-17
> **blehmeco said:**
> G! Thanks a lot 4 those last 2 posts guys! Really helpful!
 
I still don't have my friend's External USB HDD or External CD/DVD Drive, so I'm taking that chance to anticipate the difficulties/mistakes I might be facing in the (hopefully near) future...
 
So, here r my most recent difficulties/uincertainties:
1 - If my internal HDD has 3 parttions (#1-Recovery; #2-Vista OS and other stuff; #3-Data), if I format it and install a new OS like Win 7, won't I be loosing that Recovery partition 4ever? If so, what will I be loosing here? I have an Assus Recovery DVD, and on that DVD it's printed that the software included in this DVD only works on your Asus PC and that its contents have been factory pre-installed on the PC, does that mean I can always use that DVD (even without that partition) to get my PC back to Vista and its after-bought condition (OS-wise imean).
 
2 - About the distros, I think I'm going to start with Ubuntu and then, after I get comfortable with it I might consider some other distro more suited 2 my needs; question is, how do I prepare my system to be open to the install of more than one distro in the Linux partition? (we're talking about doing it right, with the same Grub2 and all, like wilee-nilee mentioned).
 
3 - I don't own an external HDD, and I'm not thinkin about buying one 4 now, and my internal HDD is a 160GB one, which I belive is enough 4 my needs right now; considering this setup, do you guys think I should create a 3rd NTFS partition where I'd store all my data and leave the OS's in separate partitions? Seems like a good idea in theory, but then how would I decide the size of the partition 4 each of the OS's and the size of the 3rd "only-for-data" partition?
 
4 - so, there's at least 2 easy ways of setting up a dualbooting system: 1 - Fully Install Win7 then shrink the drive and install Ubuntu on the remaining free space; 2 - Install win7 fully and defrag the HDD, then boot into Ubuntu's Live CD, use Gparted to partition the drive in the proportition that I want, and install Ubuntu on partition #2. Which of these methods is safer/better in your opinion? [COLOR=red]EDIT: I suppose it's No.1 then! [/COLOR]Will both of these methods lead to the same setup? I mean will they both offer the option to choose 1 of the OS's to start on boot?
 
5 - Do you know of any methods of using Ubuntu Live CD or any Linux apps to check why my DVD drive is malfunctioning? Or diagnosing it?
 
6 - Are there any known/common mistakes/incompatibilities/limitations that you think I should be aware of before building this dualbooting system with Win7/Ubuntu 10.04 LTS?
 
 
Again thanks for the help and patience guys!...Seems like there will be some green grass coming out of this rough patch!
 
Any other heads up or important info you may want to throw b4 I go on, please do!

Question 1 The recovery is for Vista it wont work anyway, and you will have a install DVD so that is your recovery. I'm not sure of the MS thought on buying a upgrade the reverting back to Vista, I suspect as long as your only using one it is okay but they are the person to contact for this. The oem disc of vista will reinstall as it was when purchased. The advantage of the upgrade is it wont have all the extra Asus stuff you don't need or really want in the end. 

Question 2 Ubuntu will install into a extended partition with a primary partition inside of it. A extended partition allows more primaries the the HD would allow which is only four. But Windows has to be in a primary, that is not inside a extended. Actually I would not worry so much about this at this point, wikipedia gives a explanation of partition types, the only problem is that they are called different things in MS or Linux speak, but are the same type of partition types.

Question 3. The shared ntfs is the way to go. But a external using ntfs is really the best route in that it has everything saved off the computer in case the HD fails or something else does. If you lose the use of computer you lose all the stuff.

Question 4 always use the W7 disk manager to adjust W7 there are 3rd party ones that work as well but only use gparted to build the ntfs partition for W7 if you decide to do a custom install that uses a limited space and leaves the rest of the HD unallocated for Ubuntu. I would use the windows7 dvd to do a custom install with Vista being overwritten and delete the recovery in this install, your activate key for a upgrade should work fine this way.

Question 5 I don't know.

Question 6 The problem that most have is installing grub the Ubuntu bootloader in a MS partition when it goes to the master boot recored which is sda in your computer.

Hope this is helpful, I would get that external HD though you can get a terabyte one off the net for a 100$ or less.

Edit the OEM disc will install as when purchased but wont make a recovery. Actually the first thing I removed on my MS-centric computer was the recovery, but during a upgrade to W7 from XP. The recovery is good if you only have MS on the computer, and don't change OS. For me the recovery was taking up space when I had the ISO and a DVD of W7 and  license for XP and a legit install CD. 

Once you install Ubuntu and it takes over the boot in the mbr it is unlikely that the recovery can be triggered to start and if it can be, may overwrite the whole HD, hint here external HD will save you a lot of problems if they arise. If you have the install discs for all the OS and or loaded thumbs all you have to do is reinstall and update the OS. This can be done with either OS in whatever order as the MBR can be loaded easily to get it going. But I would start with the W7 install when your all backed up then Ubuntu it will make things easier.

If you want something on the computer before you have the W7 purchase you can install W7 second but the activate key may only work with a auto phone activate or with actual help from a MS tech to get to the auto phone to activate the OS. It is easy to reload grub2 bootloader after a MS install being second. The key may activate if you keep the recovery until the W7 install after a Ubuntu install you never know.

---

### Post by dnguyen1963 on 2010-06-18
> **wilee-nilee said:**
> Thanks for your interest but using gparted to resize W7 is not a suggested way. W7 has a virtual disk manager that will resize while in the running system and **is** the suggested method, by everybody.

W7 doesn't have a auto chkdsk like XP so doing it this way can break it quite easily.

Very polite response.  I guess I have been lucky without running into trouble using Gparted with W7.

---

### Post by wilee-nilee on 2010-06-18
> **dnguyen1963 said:**
> Very polite response.  I guess I have been lucky without running into trouble using Gparted with W7.

Some have suggested that this is may be okay, and a chkdsk can be run from a install DVD, but personally I have seen this method suggested by 2 people you and a person on this site. I would use the virtual disc manager in W7 myself.;)

---

### Post by blehmeco on 2010-06-19
> **wilee-nilee said:**
> I would use the virtual disc manager in W7 myself.;)
 
Suggestion accepted! Don't want to take any unneccessary risks here!
 
 
**Great thanks 4 answering all my questions wille-nilee! (again :D)**
 
 
 
So, I'll b receiveing the W7 install DVD in a few days, together with my friend's External DVD drive...
 
And what you said got me thinking, so I'm actually considering buying an Extrenal USB HDD... in any case I can buy it at any time in the future after I recover my laptop, right?... so I'm not rushing 4 it just yet! ;)
 
So that you can understand what I'm truying to achieve with this new "project" here's the setup I want to build (please correct me if something here might be unadvisable/incorrect):
a - a W7 partition occupying as less space as possible in the HDD (e.g. something like 5GB)
 
b - a 2nd Ubuntu partition occupying as less space as possible in the HDD (e.g. something like 5GB)
 
c - a 3rd NTFS partition, occupying the remaining HDD space (e.g. 150GB), where I'd store the data that both OS's would access (including apps)
 
d - my main goal with this new project is to leave as much space as possible for the 3rd NTFS data partition , and the least space possible to the OS's (making the best out of my small HDD (it's enough 4 me but small on today's standards at least); while still allowing for OS updates and a safe and reliable work system on both environments (W7 and Ub)
 
e - is this possible though: In both OS's there are special folders (e.g. "Music", "Photos", "Documents", etc.), is it possible to create symbolic links (i believe that's what they're called) in each of that folders in both OS's to folders containig the corresponding contents in the 3rd NTFS partition? e.g.: a symbolic link in the "Photos" folder of W7 that links directly to a "Photos" folder in the NTFS partition, and the same in the Ubuntu partition
 
f - is this ok?: I'm also thinking about creating 1 "Win7 Programs" folder and a "Ubuntu Programs" folder on that 3rd NTFS partition, so that I can make the most out of the space I got, and leave the minimum required space for the OS's untouched; meaning: I would install Programs to the 3rd NTFS partition where I'd have lots of space to install whatever programs I'd like; this way I would avoid problems with space like I would have if I needed 2 install Programs on the small size OS partition! (it sounds confusing but hope I made myself understood here!)
 
g - pratical example of what I want to happen is this: by symlinking both the "My Music" folder on W7 and Ubuntu with a "Shared Music" in the 3rd NTFS partition, when I used iTunes on W7 (which would have the its Music library on W7's own "My Music" folder) it'd go directly to the "Shared Music" folder in the 3rd NTFS partition opening the *.mp3 files I had stored there (and not on the W7's "My Music folder" that would be empty in fact), without the need to have *.mp3 files on the "My Music" folder of W7; the same would happen using any other Media player in Ubuntu; this would allow for a much better space optimization on the OS partitions and avoid files duplication between OS's, cluttering its (already small space), right?
 
h - no Recovery partitions eating up my HDD's space this time! 
 
 
 
So now that I finally have a much clearer idea of how I want my system setup (sort of), I'm just not sure of (at least ) a couple of essential points of how to get it done...
 
So, to achive the above setup, here's what I'm thinking of doing, after your useful inputs (please correct me if I'm wrong at any point!):
1 - Use Ubuntu's Live USB to recover the data to my friend's USB HDD.
2 - Install W7 from W7 Install DVD (from External USB DVD drive), using all the HDD space and overwriting everything; not having a recovery partition consuming HDD space anymore (yay! more space in the HDD this time around!).
3 - Use W7 Disk utility to first defrag it and then shrink it; question: will it be possible/reccommendable to shrink so that the W7 partition will occupy the least space possible?
4 - Use Ubuntu Live CD (from the External DVD USB Drive) or Ubuntu Live USB thumb drive to install Ubuntu on the unallocated space freed up using the shrink method...but using all that space? Or...Ups! (To be continued...)
 
Halt here!
I'm not sure where to include the creation of the 3rd NTFS partition in this guide! Or really how to do it properly!
Should I use Gparted to do it, right after installing Ubuntu? And will I b able to limit as much as I can the space Ubuntu installation partition is occupying?
And BTW, I know W7 will be reading/writing without problems on the NTFS partition, but will Ubuntu be able to read/write seamlessly on the NTFS partition too?
 
 
P.S. - Sorry 4 my huge posts, but my uncertainties keep building up as I go, and I prefer to clear them b4 I make another rookie mistake, like the one that got me here in the 1st place, you know?...just trying to be a little more thoughtful and wise, this time!...guess i might be turning into Rookie v.2.0beta now! :rolleyes:

---

### Post by dnguyen1963 on 2010-06-20
> **blehmeco said:**
> Suggestion accepted! Don't want to take any unneccessary risks here!
 
 
**Great thanks 4 answering all my questions wille-nilee! (again :D)**
 
 
 
So, I'll b receiveing the W7 install DVD in a few days, together with my friend's External DVD drive...
 
And what you said got me thinking, so I'm actually considering buying an Extrenal USB HDD... in any case I can buy it at any time in the future after I recover my laptop, right?... so I'm not rushing 4 it just yet! ;)
 
So that you can understand what I'm truying to achieve with this new "project" here's the setup I want to build (please correct me if something here might be unadvisable/incorrect):
a - a W7 partition occupying as less space as possible in the HDD (e.g. something like 5GB)
 
b - a 2nd Ubuntu partition occupying as less space as possible in the HDD (e.g. something like 5GB)
 
c - a 3rd NTFS partition, occupying the remaining HDD space (e.g. 150GB), where I'd store the data that both OS's would access (including apps)
 
d - my main goal with this new project is to leave as much space as possible for the 3rd NTFS data partition , and the least space possible to the OS's (making the best out of my small HDD (it's enough 4 me but small on today's standards at least); while still allowing for OS updates and a safe and reliable work system on both environments (W7 and Ub)
 
e - is this possible though: In both OS's there are special folders (e.g. "Music", "Photos", "Documents", etc.), is it possible to create symbolic links (i believe that's what they're called) in each of that folders in both OS's to folders containig the corresponding contents in the 3rd NTFS partition? e.g.: a symbolic link in the "Photos" folder of W7 that links directly to a "Photos" folder in the NTFS partition, and the same in the Ubuntu partition
 
f - is this ok?: I'm also thinking about creating 1 "Win7 Programs" folder and a "Ubuntu Programs" folder on that 3rd NTFS partition, so that I can make the most out of the space I got, and leave the minimum required space for the OS's untouched; meaning: I would install Programs to the 3rd NTFS partition where I'd have lots of space to install whatever programs I'd like; this way I would avoid problems with space like I would have if I needed 2 install Programs on the small size OS partition! (it sounds confusing but hope I made myself understood here!)
 
g - pratical example of what I want to happen is this: by symlinking both the "My Music" folder on W7 and Ubuntu with a "Shared Music" in the 3rd NTFS partition, when I used iTunes on W7 (which would have the its Music library on W7's own "My Music" folder) it'd go directly to the "Shared Music" folder in the 3rd NTFS partition opening the *.mp3 files I had stored there (and not on the W7's "My Music folder" that would be empty in fact), without the need to have *.mp3 files on the "My Music" folder of W7; the same would happen using any other Media player in Ubuntu; this would allow for a much better space optimization on the OS partitions and avoid files duplication between OS's, cluttering its (already small space), right?
 
h - no Recovery partitions eating up my HDD's space this time! 
 
 
 
So now that I finally have a much clearer idea of how I want my system setup (sort of), I'm just not sure of (at least ) a couple of essential points of how to get it done...
 
So, to achive the above setup, here's what I'm thinking of doing, after your useful inputs (please correct me if I'm wrong at any point!):
1 - Use Ubuntu's Live USB to recover the data to my friend's USB HDD.
2 - Install W7 from W7 Install DVD (from External USB DVD drive), using all the HDD space and overwriting everything; not having a recovery partition consuming HDD space anymore (yay! more space in the HDD this time around!).
3 - Use W7 Disk utility to first defrag it and then shrink it; question: will it be possible/reccommendable to shrink so that the W7 partition will occupy the least space possible?
4 - Use Ubuntu Live CD (from the External DVD USB Drive) or Ubuntu Live USB thumb drive to install Ubuntu on the unallocated space freed up using the shrink method...but using all that space? Or...Ups! (To be continued...)
 
Halt here!
I'm not sure where to include the creation of the 3rd NTFS partition in this guide! Or really how to do it properly!
Should I use Gparted to do it, right after installing Ubuntu? And will I b able to limit as much as I can the space Ubuntu installation partition is occupying?
And BTW, I know W7 will be reading/writing without problems on the NTFS partition, but will Ubuntu be able to read/write seamlessly on the NTFS partition too?
 
 
P.S. - Sorry 4 my huge posts, but my uncertainties keep building up as I go, and I prefer to clear them b4 I make another rookie mistake, like the one that got me here in the 1st place, you know?...just trying to be a little more thoughtful and wise, this time!...guess i might be turning into Rookie v.2.0beta now! :rolleyes:

Why only 5 Gb for OSes?  HD is really cheap these days.  I'm not sure how much W7 needs, but 5 Gb seems to be small for any kind of Windows OS.  Are you planning on downloading a lot of movies?

---

### Post by blehmeco on 2010-06-21
> **dnguyen1963 said:**
> Are you planning on downloading a lot of movies?
 
It's not really movies... :redface:
 
I know you won't believe me but what really cramps up my disk space are Video Podcasts!...man, I didn't really realise how much they were eating up my drive until my C: (which was Vista OS Drive and where iTunes and its Music Library and hence podcasts were kept) was full and I had to burn some 10 DVD's with Videocasts to download install Vista's SP1!
 
I'm thinking about downloading Videocasts, yes, and keep on burning them to DVD's whenever the need comes!..that way avoiding the need for a new HDD...(yup! you can call me cheap! :lol: )
 
 
 
> **dnguyen1963 said:**
> I'm not sure how much W7 needs, but 5 Gb seems to be small for any kind of Windows OS.
 
I said 5GB only as an example!
 
I've just heard that W7 takes up as much as 8GB, so I'd say that the Vista partition would get like 15GB to be safe!...for updates and all...but the thing about leaving only that space 2 the OS, is because I'd have lots of space to grow in the shared drive!...if I left it 50% on W7 and 50% to Ubuntu, rather sooner or later I'd be installing W7 programs on Ubuntu partition or I'd be having to spread my video/music files between the 2 making it impossible to organise!...
This way, everything aside from the OS's (everything likely to grow :D , like music folders, program folders, photos folders, etc.) would be in the biggest continuous space where it can grow without bothering me or the OS's...
It sounds good to me, but do you think I'm making a mistake here? What do you say?
 
 
 
> **dnguyen1963 said:**
> HD is really cheap these days.
 
You are quite right! That's why I'm considering a new External HDD! :-D
Also I was holding from buying an External HDD before because I was thinking of getting a bigger HDD with my next PC, and in the meantime surviving by burning DVD's! (wich I was managing just fine I should say!)

---

### Post by blehmeco on 2010-06-24
So, even without replies to my previous posts I'm going to post my latest progress:
 
- bought an external USB HDD (it's a multimedia USB HDD..and yes, it was rather cheap!)
- already have Windows 7 install DVD
- already have the external USB DVD drive
- already backep up both my partitions onto the External USB Drive
- trying 2 install W7 now!
 
 
Next up:
 
- Defrag
- Shrink it
- Install Ubuntu on the unallocated disk space
- from Ubuntu (I'm guessing it's better 2 use Ubuntu 2 do this, right?) create extra NTFS partition

---

### Post by blehmeco on 2010-06-24
So, as it is warned here:
 
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
 
I can only shrink W7's partition to about half its size, which makes my initial plan (20GB to W7 + 20GB yo Ubuntu + 110GB for (shared) data) impossible... 
 
So now, I'm pondering over 2 options:
Option 1 - Leave W7 with 130GB and shrink its drive to 110GB, then install Ubuntu on the remaining 20GB of unallocated HDD space. (although I wouldn't have a separate NTFS drive for data as recommended by wilee)
Option 2 (not sure if it's possible) - Re-install W7, formatting the drive in the beggining and on this screen:
[http://www.techtalkz.com/gallery/files/1/Windows7-2008-11-04-14-55-10.jpg](http://www.techtalkz.com/gallery/files/1/Windows7-2008-11-04-14-55-10.jpg)
choose to create a new partition with 20GB where I'd install W7, and then on the remaining disk space install Ubuntu, creating the extra NTFS partition with Ubuntu&Gparted afterwards!
 
Could you guys please tell me what would you do here?

---

### Post by wilee-nilee on 2010-06-24
I know the link says a min of 20 gigs for windows, but it should be at least 40gigs. W7 unpacks to about 10 gigs, the twenty is twice that amount, leaving you no room for really adding stuff and no consideration of the temporary files MS is so famous for. You want a equal amount of filled and open space on a OS partition for optimal use.

So how big is the HD on the computer and how big is the external HD and how space is left on the external.

I just got up so I may be missing something here.

---

### Post by blehmeco on 2010-06-24
> **wilee-nilee said:**
> I know the link says a min of 20 gigs for windows, but it should be at least 40gigs. W7 unpacks to about 10 gigs, the twenty is twice that amount, leaving you no room for really adding stuff and no consideration of the temporary files MS is so famous for. You want a equal amount of filled and open space on a OS partition for optimal use.
 
Hmmm... I see, so my initial plan was impossible from the beggining then...then what do you think I could do 2 have that separate NTFS drive of shared data?
 
I could leave W7 partition as the Data+W7 partition, maybe? I mean, instead of re-installing W7 and creating a separate NTFS on the install, which wouldn't leave that much space for W7 (because as you're saying, it's not advisable to have a small W7 partition), I can just turn this big (150GB) W7 partition into my data NTFS partition...and share it with Ubuntu... what do you say?
 
And how much space is it advisable to leave 4 Ubuntu?
Please bear in mind that I'm still trying to have the biggest possible continuous space for shared data between OS's!
 
 
 
> **wilee-nilee said:**
> So how big is the HD on the computer and how big is the external HD and how space is left on the external.
 
So, here's the stats:
- my Laptop's internal HDD is a 160GB one; right now on W7 it says it's got about 150GB of free space
- the external USB HDD is a 500GB one; it's a multimedia HDD, so it's formatted 2 have a 289GB NTFS partition, a 163GB FTA32 partition and the rest being used for recordings; right now the backup of my old Vista partitions are occpying about 130GB of the NTFS partition.
 
Oh! BTW, I want 2 use the external USB HDD as a backup only, as I intend to keep everything still inside my internal HDD, so please don't count on it 2 leave stuff out of the disk, ok?...I rather burn DVD's when I'm needing space!...
yeah!...go ahead..call me crazy if you want 2...
 
 
 
> **wilee-nilee said:**
> I just got up so I may be missing something here.
 
Hey!
So good morning 2 you! :p

---

### Post by wilee-nilee on 2010-06-24
The most efficient way to do this is to just split the HD in half on the computer half W7 half Ubuntu. The Ubuntu partition can be shrunk if you want to fit aother OS in their. Ubuntu if installed with the CD should be inside a extended partition which will allow a lot of primary partitions for multiple operating systems. Ubungtu is in an primary inside a extended if you let it install to the free space without a custom or pre-formatted partitions, with a swap in there as well

Now you could do a custom install as your screen shot of the HD shows and put W7 in a smaller area then half the HD I wouldn't go any lower then 40-60 gigs though, for a safety margin.

The idea of saving media inside the computer is okay, if you have a backup on the external. 

Personally I have a computer with the same HD size it only has just the basic operating systems on it everything else is in a external HD. I do it this way for two reasons One if the internal HD fails or the computer fails the only loss is those components. Second reason is I install different Operating systems all the time so it is easier to just pop a disc or load a thumb and install without having to transfer stuff out of the Internal HD first. I can at any minute just pop a new OS in without blinking.

As of now you have about 750 gigs to use between the internal and external HD's thats a pretty good setup just use it with some common sense, apart from what you think you want. You can also get a terrabyte external off the net for around a 100$ US so at some point if you fill these all up buy another external.

I use the external as my shared partition rather the computers HD.

---

### Post by blehmeco on 2010-06-24
> **wilee-nilee said:**
> The most efficient way to do this is to just split the HD in half on the computer half W7 half Ubuntu. The Ubuntu partition can be shrunk if you want to fit aother OS in their. Ubuntu if installed with the CD should be inside a extended partition which will allow a lot of primary partitions for multiple operating systems. Ubungtu is in an primary inside a extended if you let it install to the free space without a custom or pre-formatted partitions, with a swap in there as well
 
So what you're saying is that now, the most efficient way to get it done is by shrinking W7 to about half the HDD size (which is possible to do, s I've just checked) and install Ubuntu on the uinallocated space, right?
And how can I ensure that Ubuntu is installed inside an extended partition with the swap in there, allowing 4 multilpe OS's in the future?...Could you explain how to do that better?
 
 
> **wilee-nilee said:**
> Now you could do a custom install as your screen shot of the HD shows and put W7 in a smaller area then half the HD I wouldn't go any lower then 40-60 gigs though, for a safety margin.
 
(...)
 
I use the external as my shared partition rather the computers HD.
 
Thing is, I don't like the idea of relying only on the External HDD for data keeping, and I don't like to carry more than the PC around, so I'd rather keep the External HDD as back up at home and having everything I need still on the internal drive whenver I take my laptop out...
Mainly, the problem of creating a 50/50 split in the internal HDD for me is because I have lots of files on my iTunes Music Folder (songs, videos, podcasts, etc), and it sucks having to split these files between the 2 partitions, because it makes a mess of managing it and keeping it organised!...it was one of the things that used to bother me the most about the setup I had before on my PC...
 
Now you understand why I was trying to get a larger continuous partition and smaller OS partitions...
 
But, tell me, is my idea of turning W7 partition into the larger DATA+W7 partition and having Ubuntu on a 2nd 50GB partition a bad idea?... do you think Ubuntu (and others) would need much more than say, 50GB to work properly?...
Remember: I would use W7 partition to install Ubuntu's programs 2when needed, and this way, maybe I wouldn't have to split my iTunes Music Library between the partitions!

---

### Post by wilee-nilee on 2010-06-24
First this thread is so long I don't have the patience to look through every part to see what your set up looks like now.

Also download this defrgger it has a optimize option that will consolidate the W7 so that it can be shrunk correctly, go to the preference part that has it move everything that can be moved to the start of the HD. There are parts that can't be moved without a even better optimizer defragger or consolidating programs, this one is a good one though that is free.
[http://www.auslogics.com/en/software/disk-defrag/](http://www.auslogics.com/en/software/disk-defrag/)

So post the question again, with a screen shot of gparted, after running the defragger and seeing if it will shrink to a size that makes you happy.

I'm not responsible for helping you set your computer up in a way that is to exactly how you want it. I think your asking to much of me here. I told you what I would do and I have given you information on how to get closer to your goals by telling you how to defrag or do a custom install of W7 to the size you want.

I have been glad to help but you need to do some outside investigation, I'm not the only answer here.:p

---

### Post by blehmeco on 2010-06-24
Yup! I guess you're right! I'm asking too much of you indeed! And I'm sorry for not noticing it before!
I mean after all the help you gave me and all ((huge) thanks 4 that again BTW! ;) ), it's not fair to still be bothering you with this...
 
So I'll try to be concise and brief...
 
I was just trying to achieve that ideal setup you talked to me about before and which sounded so great to me: with a separate shared NTFS partition aside from the OS's partitions!
 
But in the process I understood that that would be a bit impossible and even an unadvisable thing to do for the OS's to work properly!
So now I guess I'm going to take your advice again and go 4 a somewhat 50/50 setup on my disk with W7/Ubuntu!...maybe I'll leave a bit more space 4 W7 to accomodate iTunes Media files(100GB for Win7, media files and program installs + 50GB for Linux stuff)...we'll see!...
 
But you don't need to worry now! I think I can take it from here! ;)
 
And again: **thanks a LOT for your help, patience and time wilee!**
 
To me it was priceless and I believe that it's the kind people like yourself that make this community an absolute wonder!
 
Cheers mate!

---

### Post by blehmeco on 2010-06-25
Guys!
 
Here's my last question concerning this problem, hope anyone can help me out...
Did a lot of search on Google and the forums, but I found no definite answer, so hope you don't mind me asking a last question concerning Ubuntu install...
(Sorry if this is a rather basic question!...I choose to blame it on my rookines with Linux...)
 
I've installed W7, shrank it to 110GB and now I'm about to install Ubuntu on the remaining 30GB of unallocated space...
I want my system to start off with the prompt for Win7/Ubuntu boot (as a normal dual boot system does)... but I want to be able to install other additional Linux distros in the future.
 
So on the last screen of the installation:
 
[IMG]http://pplware.sapo.pt/wp-content/uploads/2010/04/Ubuntu_06_thumb.jpg[/IMG]
 
After choosing that "Advanced" option I know I should create 2 partitions:
 
 
 
 
 
 

**1 - Primary partition** 
[LIST]
[*]**Partition type:** primary
[*]**Syze in Megabytes:** ??????????????
[*]**Location:** Begining
[*]**With Ext4 and Journling**
[*]**Mount Point:** /
[/LIST][[IMG]http://pplware.sapo.pt/wp-content/uploads/2010/04/Ubuntu_07_thumb.jpg[/IMG]]("http://pplware.sapo.pt/wp-content/uploads/2010/04/Ubuntu_07.jpg") 
 
 
 
 
 
 
 

**2 - Logical partition (swap)** 
[LIST]
[*]**Partition type:** Logical
[*]**Size in Megabytes:** ??????????
[*]**Location:** Begining
[*]**Swap Area**
[/LIST][[IMG]http://pplware.sapo.pt/wp-content/uploads/2010/04/Ubuntu_08_thumb.jpg[/IMG]]("http://pplware.sapo.pt/wp-content/uploads/2010/04/Ubuntu_08.jpg") 
 
 
 
Assuming the definitions for the partitions I've chosen are correct (are they?) how do I distribute the size for the swap partition and the other one to ensure a that I have created a system that will allow other Linux distros? (Basically, what do input where the question marks are above?)
 
My Laptop has 2048GB of RAM and the total unallocated space (available for Ubuntu install) is 30GB!
 
 
Thanks in advance!

---

### Post by wilee-nilee on 2010-06-25
Basically in order to have multiple primary partitions above the limit of 4 on any hard drive is by putting them inside a extended with one swap in there. Post a screenshot of gparted. I think you just need to with gparted fill the rest of the empty space with a extended. Then make a primary inside of it, leaving space for a swap partition. You woukld the just shrink the Ubuntu primary and make another primary for other Linux distro's but would want to make sure any installed were using grub2.

---

### Post by blehmeco on 2010-06-25
Here's my Screenshot of Gparted[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG]

---

### Post by wilee-nilee on 2010-06-25
Here's the deal you have sent me to many PM's, 2 today within minutes of about to post or posting. I get both notifications your PM and the post in the same amount of time. I can't take any more of this it is not a functional protocol get help from others.

---

### Post by blehmeco on 2010-06-25
Only PM'd you in the first place because you had told me 2 feel free to do so, and because you also told me that sometimes it was hard to keep track of the thread because it was too long!
 
I sent you the PM and posted the same msg on the thread at pratically the same time, even before you replied 2 my PM...that way in case you didn't have time to reply 2 my PM (which I would honestly understand), then somebody else would reply in the thread!
 
I understood I asked about a lot of stuff before on the thread, but right now it was my last question...
 
Well, anyways, sorry 4 that!
I honestly meant no harm!...
And I keep my thanks 4 all your help!
 
 
Still, if anybody can just enlighten me with this last thing just let me know!

---

