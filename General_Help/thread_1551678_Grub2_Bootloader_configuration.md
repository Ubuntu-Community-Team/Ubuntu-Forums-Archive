---
title: "Grub2 Bootloader configuration"
date: 2010-08-12
forum: General Help
---

### Post by ptoche on 2010-08-12
I dual-boot kubuntu 10.4 and Windows 7, with Grub2. I'm trying to edit the boot menu. I've been able to remove older kernel entries by cleaning the boot menu, and I've removed the memtest entries by chmoding them (or whatever). So, now I've got:

Ubuntu blabla,
Ubuntu blabla (safe mode or something)
Windows 7 (loader) on /dev/sda1
Windows 7 (loader) on /dev/sda2

I'd like to remove the last entry.

I have read this: [HTML]http://www.dedoimedo.com/computers/grub-2.html[/HTML]

Ideally I wouldn't modify the 30_os-prober file as I'd rather add information in 40_custom instead.

Anyone knows a quick way to this?

---

### Post by cj.surrusco on 2010-08-12
The only way to remove that entry would be to disable the 30_os-prober and add the one desired entry to the 40_custom, I believe.

---

### Post by oldfred on 2010-08-12
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)

I added this to turn off prober :
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

You can turn it back on whenever you update system with new system if you want.

---

### Post by ptoche on 2010-08-12
thanks for your quick reply cj, so I guess I can try something like 

```

sudo chmod -x 30_os-prober

```

and then add the following to 40_custom

```

#! /bin/sh -e
 echo &#8220;Adding Windows&#8221; >&2
 cat << EOF
 menuentry &#8220;Windows 7&#8243; {
 set root=(hd0,1)
 chainloader +1
 }
 EOF

```

I found the above code [here]("http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/"), I think it does what I want.

Perhaps I could test by modifying 40_custom without immediately chmoding 30_os-prober ? Anything else could go wrong?

---

### Post by ptoche on 2010-08-12
> **oldfred said:**
> 
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom


Thanks oldfred, I'll give this one a try right now! If you don't hear from me in the next few hours, it won't be good!!

---

### Post by Cavsfan on 2010-08-12
Check out the tutorial in my signature. It will do what you want.

---

### Post by ptoche on 2010-08-12
Oh absolutely Cavsfan, great help, works. How did I miss your tutorial, it's excellent.

---

### Post by Cavsfan on 2010-08-12
> **ptoche said:**
> Oh absolutely Cavsfan, great help, works. How did I miss your tutorial, it's excellent.

Thanks! I didn't want to butt in as we are all trying to help! :P
If you have any problems just let me know.

---

### Post by ptoche on 2010-08-12
This question is now SOLVED.

okay, a note to myself based on Cavsfan's tutorial:


the boot loader configuration file is in: 

/boot/grub/grub.cfg

grub.cfg is created with the command:

sudo update-grub

grub-cfg is created by compiling the files in:

/etc/grub.d/

To make sure update-grub does not compile backup files, do:

sudo chmod -x *.bak

The order of the boot menu list is based on the numbering of the files,
00_header: compiled first,
05_debian_theme: compiled next, etc.
10_linux: creates the boot menu entries for the linux install, 
30_os-prober: creates the boot menu entries for the windows install
40_custom: commands to customize the menu.

Step 1: create a standard grub.cfg.

Step 2: from grub.cfg copy the following info (or similar) into 40_custom

menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 598e9444-a0f1-4d6b-8987-56191a2fcd1d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=598e9444-a0f1-4d6b-8987-56191a2fcd1d ro  quiet vga=769  quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set 598e9444-a0f1-4d6b-8987-56191a2fcd1d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=598e9444-a0f1-4d6b-8987-56191a2fcd1d ro single  quiet vga=769
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f62cdc062cdbbfb3
	chainloader +1
}


Order them as you would like them to appear on the menu and edit the names, for instance:

menuentry "Bill Gates's Favorite OS" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set f62cdc062cdbbfb3
	chainloader +1
}


step 3:

Disable the compilation of:
sudo chmod -x 10_linux
sudo chmod -x 20_memtest86+
sudo chmod -x 30_os-prober


step 4:

sudo update-grub
to recreate the grub.cfg file

---

### Post by Cavsfan on 2010-08-13
**ptoche**, as long as you changed the UUID and other stuff it should be working great.
Have you tested everything and it works to your expectations?

I added a picture of what my screen looks like at the bottom of the tutorial.
It has just 3 lines and I don't have to touch it. Check it out. If you made these 3 files 
(10_linux  20_memtest86+  30_os-prober) unexecutable it should look just like mine does.
With a different picture of course.

---

### Post by ptoche on 2010-08-13
yes, it works great, I too have three lines,

Windows 7
Kubuntu 10
Kubuntu 10 (recovery)

great stuff, thanks.

As a side remark, before being directed to your tutorial I had experimented with a utility called "startup manager." It did some pretty cool things with grub, in a totally intuitive manner, but unfortunately many of its functions don't work with grub2.

---

### Post by Cavsfan on 2010-08-13
> **ptoche said:**
> yes, it works great, I too have three lines,

Windows 7
Kubuntu 10
Kubuntu 10 (recovery)

great stuff, thanks.

As a side remark, before being directed to your tutorial I had experimented with a utility called "startup manager." It did some pretty cool things with grub, in a totally intuitive manner, but unfortunately many of its functions don't work with grub2.

I think I played around with startup manager myself. I played with a lot of stuff actually.
I have mine the opposite of yours:
[B]Ubuntu
Ubuntu (recovery)
Windows 7[/B]
and for the wife and son it defaults to windows 7. But which ever you prefer is great and
what is so cool about this is the fact that it is customizable.
At least in what is displayed and in what order you wish them to be displayed.
You are the 2nd person that I know of that has used the tutorial. 
Maybe others have used it without saying anything. At least I am hoping that is the case.
I was mentioning to Ranch Hand, who showed me how to do this that I had to edit my default line as I had just installed a new kernel.
Which made my default line be wrong. He showed me this and I haven't had to touch it except when there was an update to Grub2.
It asked if I wanted to keep mine or update and I did a side by side comparison and then took the new version.
All I had to change was the default line I believe and haven't touched it since.

That is what this is all about - maintenance free bootup.

---

### Post by ptoche on 2010-08-15
Oh I'm sure your tutorial has been seen and used. It's particularly important to tweak the boot-load menu if you have a windows recovery partition, because grub2 will list it as a bootable and if it gets accidentally selected (most likely by someone other than the main user), you could see your machine go back to its factory settings before you can say ouch!

---

