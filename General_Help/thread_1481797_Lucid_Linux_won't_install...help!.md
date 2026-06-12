---
title: "Lucid Linux won't install...help!"
date: 2010-05-12
forum: General Help
---

### Post by djamyx on 2010-05-12
Hey guys...I'm brand spankin new to Linux...so know up front that we're dealing with a noob....


I've followed the development of Ubuntu for a while and tonight I decided to make the jump and dual boot xp with the latest release of Ubuntu.

Burned the iso...got the Ubuntu screen after reboot which has the five dots...

after that, the screen goes to horizontal lines which show pixels...in weird colors..and installation doesn't continue...I haven't entered any boot parameters...don't know that I was given an opportunity to...

What's going on here?  I'm guessing video card issues...so I'll list the system specs below

Asus Mboard
4gb DDR2 Ram (4x1GB)
Nvidia Geforce 7800
AMD Athlon 64 x2 5600+

Any thoughts would be appreciated as I'm trying to get my wife excited about linux!

---

### Post by McMichael96 on 2010-05-12
> **djamyx said:**
> Hey guys...I'm brand spankin new to Linux...so know up front that we're dealing with a noob....


I've followed the development of Ubuntu for a while and tonight I decided to make the jump and dual boot xp with the latest release of Ubuntu.

Burned the iso...got the Ubuntu screen after reboot which has the five dots...

after that, the screen goes to horizontal lines which show pixels...in weird colors..and installation doesn't continue...I haven't entered any boot parameters...don't know that I was given an opportunity to...

What's going on here?  I'm guessing video card issues...so I'll list the system specs below

Asus Mboard
4gb DDR2 Ram (4x1GB)
Nvidia Geforce 7200?  or 7800...Not sure..but definitely the 7 series...
AMD Athlon 62 x2 5600+

Any thoughts would be appreciated as I'm trying to get my wife excited about linux!


Maybe to disc that contains Ubuntu is messed up. I remember when I  was new to Linux (Ubuntu was my first linux distro). I downloaded the ISO and I tryed like 4 times to install it but it would not work. Well comes to find out the CD was messed up, so I burned another. And it worked! :) Maybe that the only problem. Just try to burn another. The ISO file might also be corrupted.


Just my 2 cents.

---

### Post by djamyx on 2010-05-12
Hey..thanks for the reply!

I can get to the menu within the bootable disc..and I actually ran the utility to check the disc...and it said that it didn't find any errors...

I then tried the option of "trying Ubuntu without installing"...after it goes to the purple screen with 5 dots below, it goes into the horizontal lines again....just like it did while trying to install...

on the Ubuntu documentation it says this...

If your screen begins to show a weird picture while the kernel boots, eg. pure white, pure black or colored pixel garbage, your system may contain a problematic video card which does not switch to the framebuffer mode properly.  Then you can use the boot parameter **fb=false** to disable the  framebuffer console. Only a reduced set of languages will be available during the installation due to limited console features. See [the section called “Boot Parameters”]("https://help.ubuntu.com/10.04/installation-guide/amd64/boot-parms.html") for  details.  

I just don't know where to type in fb=false to see if that is my problem...

any ideas?

---

### Post by MSPdwalt on 2010-05-12
Or whatever drive you used to burn the disk is hosed, I've had that happen, ubuntu is pretty easy to get to install from a flash drive and faster than from optical disk.

Download unetbootin and it should take your iso, move the files to your flash drive and make it bootable

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Be careful though, if I remember right this will wipe the flash drive.

---

### Post by djamyx on 2010-05-12
I may try that...but I'm sure that my drive is good...

I ran across this link which is similar to my problems...check it out....
[http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/](http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/)

He fixed it by disabling onboard usb and 1394...I'm trying that now...I'll let you know how it turns out...crossing fingers...

---

### Post by djamyx on 2010-05-12
> **djamyx said:**
> I may try that...but I'm sure that my drive is good...

I ran across this link which is similar to my problems...check it out....
[http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/](http://darinshaw.com/blog/index.php/2010/04/ubuntu-10-04-install-on-acer-aspire-m1640/)

He fixed it by disabling onboard usb and 1394...I'm trying that now...I'll let you know how it turns out...crossing fingers...


No dice...still have the same problem with everything I could disable in bios...well...disabled...

I'm still thinking its an issue with my video card...any work arounds?

---

### Post by ryan858 on 2010-05-13
To add boot parameters during Ubuntu setup, press F6 at the menu. This should bring up a popup box. Hit ESC and the box should disappear and you should be able to see a line of code with the words Boot Options fixed in front of it. You should be able to edit this line, and type the parameter at the end. Make sure you put a space after the -- at the end like so:

**.... initrd=/casper/initrd.gz quiet splash -- fb=false**


If it still doesn't work after adding the boot parameter, then you can try pressing **F4** (at the menu) and use the arrow keys to select **Safe graphics mode** and press the **Space** key to enable it.

Let us know how it goes, and we'll go from there if you still have problems.

Good Luck!

---

### Post by djamyx on 2010-05-13
okay..I got to the command line where I could see where the install process was failing...

The first thing it lists is:

GLip-warning get pwuid_r failed due to unknown userid

It continues on past this..so I don't think that is a big deal..

It gets to "Setting sensor limits" or something I couldn't see...and then it goes directly to horizontal lines...

Any clues?

---

### Post by djamyx on 2010-05-13
> **ryan858 said:**
> To add boot parameters during Ubuntu setup, press F6 at the menu. This should bring up a popup box. Hit ESC and the box should disappear and you should be able to see a line of code with the words Boot Options fixed in front of it. You should be able to edit this line, and type the parameter at the end. Make sure you put a space after the -- at the end like so:

**.... initrd=/casper/initrd.gz quiet splash -- fb=false**


If it still doesn't work after adding the boot parameter, then you can try pressing **F4** (at the menu) and use the arrow keys to select **Safe graphics mode** and press the **Space** key to enable it.

Let us know how it goes, and we'll go from there if you still have problems.

Good Luck!


Thanks for the info...like I said...noob here...I appreciate your help and patience greatly...

Still got the issues after using fb=false...apparently not what I was looking for

The text in the command line is pixelated..hard to read--I tried using nomodeset and the text was readable...

As for your Safe graphics mode...that doesn't show up in the options when I hit f4...the options I have are Normal, Use driver update disc, and OEM install(for manufacturers)

---

### Post by djamyx on 2010-05-13
OEM install seems to work...why?!?!  

Is the OEM install different as far as the operating system is concerned?


I'm choosing my language now...after selecting OEM install...weird...just want to be able to install Ubuntu with normal options...

FWIW...I also used the nomodo....thing....lol...

---

### Post by ryan858 on 2010-05-13
I'd say you're right that the error isn't a big issue...

From what you describe, it's getting all the way to the part where it starts up the X server... (X is basically the GUI part of linux, to put it very plainly...) So I would say this isn't a framebuffer problem but rather something to do with X... 

I still say try it with the Safe graphics mode... iirc, that should affect X, and not the framebuffer console. 

If that doesn't work... I don't know...

Oh, and if you do get into X, with the Safe graphics mode, and you get a box saying that it couldn't load the display correctly (or something like that) and asks you what to do, choose 'Reconfigure my graphics' (or something like that) and pick 'Use default configuration' or if that doesn't work, then 'Use low graphics mode this one time'.

I don't exactly know what they say... Hopefully I'm close and you can figure it out...


Edit: I just read your last couple posts after I posted this, cause I take so long to make a post, lol.

Anyway, so I guess it's not just an X issue since you had to use nomodset to get the console working right... And that's weird that Safe graphics doesn't show up... But glad to hear that OEM install works (which is also very strange).

---

### Post by djamyx on 2010-05-13
> **ryan858 said:**
> I'd say you're right that the error isn't a big issue...

From what you describe, it's getting all the way to the part where it starts up the X server... (X is basically the GUI part of linux, to put it very plainly...) So I would say this isn't a framebuffer problem but rather something to do with X... 

I still say try it with the Safe graphics mode... iirc, that should affect X, and not the framebuffer console. 

If that doesn't work... I don't know...

Oh, and if you do get into X, with the Safe graphics mode, and you get a box saying that it couldn't load the display correctly (or something like that) and asks you what to do, choose 'Reconfigure my graphics' (or something like that) and pick 'Use default configuration' or if that doesn't work, then 'Use low graphics mode this one time'.

I don't exactly know what they say... Hopefully I'm close and you can figure it out...

Ryan...you have no clue how much I appreciate your help and advice so far...

I would use the "Safe Graphics mode" but that isn't an option when I hit f4 from the menu...and as I stated..I'm installing after running the OEM version...which I selected from the f4 menu...I don't understand why this would install and the normal install wouldn't work...I dont' want a dummed down...or overly "techy" version of Ubuntu made for developers...so I'm kinda concerned and wonder if I should delete this installation and try all over again

What are your thoughts?

---

### Post by ryan858 on 2010-05-13
Lol, yeah I just edited my post, so read it again...

Anyway, OEM just means Original Equipment Manufacturer, basically its for computer companies like Dell or Gateway, etc, or anyone that's building a lot of computers and installing ubuntu on all of them... I don't know exactly what the differences are between OEM version and normal, probably a few things are automated and some options are geared more toward computers with Ubuntu being preinstalled on them... In any case, it shouldn't cause any problems to use OEM version. It would basically be like a computer that you bought with Ubuntu already installed on it, minus any customizations the manufacturers would make. Just in this case, you would be the Original Manufacturer, lol.

It shouldn't be radically different... Wouldn't be 'dumbed down' or in 'developer mode'... come to think of it, there's actually a developer's version of Ubuntu for that.

Ok, I'm done editing my post now. Lol.

---

### Post by djamyx on 2010-05-13
> **djamyx said:**
> Ryan...you have no clue how much I appreciate your help and advice so far...

I would use the "Safe Graphics mode" but that isn't an option when I hit f4 from the menu...and as I stated..I'm installing after running the OEM version...which I selected from the f4 menu...I don't understand why this would install and the normal install wouldn't work...I dont' want a dummed down...or overly "techy" version of Ubuntu made for developers...so I'm kinda concerned and wonder if I should delete this installation and try all over again

What are your thoughts?


Okay...OEM installed correctly...here's the problem...when it gets to the Ubuntu loading screen...it does it again...lines across the screen...what the heck?!?!

Maybe the nomodeset fixed the graphical issue..and that's why it installed...and actually had nothing to do with OEM...

How can I set it to boot using nomodeset until I can install the proper drivers for my video card?

---

### Post by ryan858 on 2010-05-13
That could be...

Do you see the GRUB bootloader when you boot up? (It's a menu kinda  thing asking which OS to use, basically.) If not, press an arrow key repeatedly during boot, this should stop it from picking the default choice automatically (if it has a low timeout like 1 or something) and let you pick it yourself... F2 might also work...

Once you're at the GRUB menu, select "**Ubuntu, with Linux 2.6.x-x-generic**" and press **E** to edit the boot parameters... Just add nomodset to the end of the line that says something like "linux /boot/vmlinuz-2.6.34-999-generic root=UUID=.... ro quiet splash"

It should look like this (besides the linux version number and UUID, those should be different because I copied this line from my system)

**linux /boot/vmlinuz-2.6.34-999-generic root=UUID=c17adedf-9f46-4e67-9ecd-268017d99c30 ro nomodset**

Remove the 'quiet' and 'splash' options so you can see what's going on behind the scenes... any errors, etc.

Once you've edited it, press **CTRL+X** to boot with the new options.

---

### Post by ryan858 on 2010-05-13
If that works and you get into Ubuntu fine, then you need to edit the nomodset option into /boot/grub/grub.cfg so that its permanent... When you just edit grub during boot it doesn't save the changes for the next time and only uses it once.

the grub.cfg file is pretty complicated, so you can just open it up and paste the contents here and i'll do the editing for you.

To open the file go to the menu at the top of the screen and click Applications, then goto Accessories and click Terminal. This should open up a console that you can type commands into, sorta like a DOS command prompt...

Type in:

**gedit /boot/grub/grub.cfg**

This should open up Gedit (its a program like Notepad in Windows) and show you a bunch of code... press **CTRL+A** to select all, then **CTRL+C** to copy it (you probably know that, lol) and then paste it into a post here with **CTRL+V**.

---

### Post by djamyx on 2010-05-13
> **ryan858 said:**
> If that works and you get into Ubuntu fine, then you need to edit the nomodset option into /boot/grub/grub.cfg so that its permanent... When you just edit grub during boot it doesn't save the changes for the next time and only uses it once.

the grub.cfg file is pretty complicated, so you can just open it up and paste the contents here and i'll do the editing for you.

To open the file go to the menu at the top of the screen and click Applications, then goto Accessories and click Terminal. This should open up a console that you can type commands into, sorta like a DOS command prompt...

Type in:

**gedit /boot/grub/grub.cfg**

This should open up Gedit (its a program like Notepad in Windows) and show you a bunch of code... press **CTRL+A** to select all, then **CTRL+C** to copy it (you probably know that, lol) and then paste it into a post here with **CTRL+V**.


Yeah...Im familiar enough with Linux/Unix/OSX to know how to get to a terminal...now..I'm a dos guy..and do just about anything in dos..but I don't know ANY commands for Linux from a terminal...Let the learning process begin...

As for where we stand, I had to call it quits for last night because of an early day today...I plan on trying the nomodset today to see if that gets me booted into Ubuntu...

I'll let you know...I get home around 5 central time....I'll post the results...again..thanks for your help

---

### Post by djamyx on 2010-05-13
Okay..using nomodeset worked in getting Lucid Lynx to boot...

Here are the contents of the grub.cfg file...ready for editing to make nomodeset a permanent boot condition...

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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 3a581b7f-178d-40d8-9429-656ad74ebd96
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
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 3a581b7f-178d-40d8-9429-656ad74ebd96
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3a581b7f-178d-40d8-9429-656ad74ebd96
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3a581b7f-178d-40d8-9429-656ad74ebd96 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3a581b7f-178d-40d8-9429-656ad74ebd96
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=3a581b7f-178d-40d8-9429-656ad74ebd96 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3a581b7f-178d-40d8-9429-656ad74ebd96
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 3a581b7f-178d-40d8-9429-656ad74ebd96
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sdc1)" {
    insmod ntfs
    set root='(hd2,1)'
    search --no-floppy --fs-uuid --set 5a10eee510eec6db
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

Thanks Ryan....Looking forward to hearing from you...

---

### Post by letmein on 2010-05-26
> **ryan858 said:**
> That could be...

Do you see the GRUB bootloader when you boot up? (It's a menu kinda  thing asking which OS to use, basically.) If not, press an arrow key repeatedly during boot, this should stop it from picking the default choice automatically (if it has a low timeout like 1 or something) and let you pick it yourself... F2 might also work...

Once you're at the GRUB menu, select "**Ubuntu, with Linux 2.6.x-x-generic**" and press **E** to edit the boot parameters... Just add nomodset to the end of the line that says something like "linux /boot/vmlinuz-2.6.34-999-generic root=UUID=.... ro quiet splash"

It should look like this (besides the linux version number and UUID, those should be different because I copied this line from my system)

**linux /boot/vmlinuz-2.6.34-999-generic root=UUID=c17adedf-9f46-4e67-9ecd-268017d99c30 ro nomodset**

Remove the 'quiet' and 'splash' options so you can see what's going on behind the scenes... any errors, etc.

Once you've edited it, press **CTRL+X** to boot with the new options.

I have this exact problem, however when i make the changes to the kernal (removing quiet/splash, adding nomodset) CTRL+X does nothing, the only option i have is 'b' to reboot and when i do so, the changes to my kernal dont stick.  Any advice?

---

### Post by lidex on 2010-05-26
It's not recommended to edit this file directly: [B] /boot/grub/grub.cfg
[/B] and is even stated in the actual file contents:
> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
Changes made here will likely be overwritten. Instead edit **/etc/default/grub** then run terminal command **sudo update-grub** to update config.

---

### Post by joopbraak on 2010-06-24
> **letmein said:**
> I have this exact problem, however when i make the changes to the kernal (removing quiet/splash, adding nomodset) CTRL+X does nothing, the only option i have is 'b' to reboot and when i do so, the changes to my kernal dont stick.  Any advice?

It should be nomodeset instead of nomodset !
Also the first time you manage to boot into Ubuntu, you should install the proprietary video hardware drivers, after that it works, you don't have to add the permanent nomodeset entry into grub.

---

