---
title: "Help using Ubuntu"
date: 2006-05-18
forum: General Help
---

### Post by spamzilla on 2006-05-18
So I have just installed Ubuntu 5.10 on my laptop, but say, when I put a CD in the CDrom drive to install some software, I get a message saying something like:

Couldn't display "/media/cdrom0/blah/blah.exe"

Why is this?

Do I need to do something to get everything to work?

Any kind of help is greatly appreciated :)

---

### Post by tribaal on 2006-05-18
Hum the problem seems to be that you're trying to install a windows program under Ubuntu.

Ubuntu (and linux in general) are radically different from windows, and thus most off-th-shelf software will not work. That's the bad part.
The good part is that there exists an equivalent to pretty much any Windows program in Ubuntu, that is free! You should probably take a look at [this post]("http://ubuntuforums.org/showthread.php?t=33183"), and [this too]("https://wiki.ubuntu.com/AptGetHowto?highlight=%28apt%29"), for more info.

Welcome to linux!

- trib'

---

### Post by 23meg on 2006-05-18
Just to make sure: are you trying to install and run software for Windows on Ubuntu? That will not work, unless you're running them via emulation software such as Wine (even then, most won't work in a stable manner). Ubuntu is an OS based on the Linux kernel and will only run apps that are compiled to work with this kernel.

---

### Post by spamzilla on 2006-05-18
The CD I am trying to boot is a EZ Connect SMC Network CD. Surely this will work on any OS? Or am i incrediably wrong!

Thanks so far guys :)

---

### Post by mips on 2006-05-18
Those CD's usually only work on windoze & osx if it is for stuff like adsl etc.

What exactly are you trying to do ?

---

### Post by skinnygmg on 2006-05-18
the cd may only have windows drivers on it.  not sure if SMC has linux drivers for your card.  you may need to use a generic linux driver to get it working

---

### Post by skinnygmg on 2006-05-18
found this here...

[http://www.linuxvoodoo.com/store/product_info.php/products_id/494](http://www.linuxvoodoo.com/store/product_info.php/products_id/494)

> The drivers require a kernel recompile, the first time, subsequent driver updates do not require this. 
This has been tested under Debian/GNU with kernel 2.4.23 and 2.6.1, Red Hat 9 with recompiled 2.4.24 and 2.6.0. 
This is NOT a plug and play solution - requires the drivers and a kernel recompile, but works nevertheless perfect. 

are you trying to use a similar card?

---

### Post by skinnygmg on 2006-05-18
here are some links to look at for info on SMC wifi, and drivers...

[http://www.homenethelp.com/web/review/smc-SMC2632W.asp](http://www.homenethelp.com/web/review/smc-SMC2632W.asp)

[http://www.linux-wlan.com/](http://www.linux-wlan.com/)

---

### Post by spamzilla on 2006-05-18
[QUOTE=skinnygmg]here are some links to look at for info on SMC wifi, and drivers...[/QUOTE]

Heh oddly enough, that NIC in the first link is the exact one I am using!

Thanks a lot

---

### Post by spamzilla on 2006-05-18
So I just downloaded the file for the NIC driver and saved it to a floppy disk on my PC. I put the disk in my Laptops Floppy Drive and went to open the file, when I got this message:

"Unable to mount the selected volume"

I clicked show more details and it said:

"Error: given UDI is not a mountable drive."

The same happens when I click on the CDROM and a similar message appears when I click on some files in the Filesystem.

Does anyone know why this is happening? 
All I have done to the OS is install from the disk and then login if thats any help at all.

---

### Post by spamzilla on 2006-05-18
Anyone :sad:

---

### Post by oyvindaa on 2006-05-18
I'm not sure, as I don't have a floppy and I've never tried this myself, but maybe this will help:

[Possibility](http://ubuntuforums.org/showthread.php?t=149686&highlight=Unable+mount+selected+volume)

And when you get error messages it might be wise to use the search-function in this forum and just type in your error message. Maybe someone's had the same problem you're having :)

---

### Post by spamzilla on 2006-05-18
Excellent. That link solved my problem!

Thanks

---

### Post by oyvindaa on 2006-05-18
[QUOTE=spamzilla]Excellent. That link solved my problem!

Thanks[/QUOTE]

No worries mate, glad to help! :)

---

### Post by spamzilla on 2006-05-19
[QUOTE=oyvindaa]No worries mate, glad to help! :)[/QUOTE]

Can anyone help me to 

a) make my account "matt" a root user.
I have gone to users and  groups > properties > privileges and ticked executing admin tasks but I still cannot execute admin commands :(

b) mount my cdrom drive
I go to places > systems > right click CD rom drive > mount and I get an error message - "given UDI is not a mountable volume." Why is this? 

I have tried searching for help on both points on this site and Google, but to no avail. Any help is much appreciated :)

---

### Post by skippy81 on 2006-05-19
Making your user account into a root account is really not recommended, it is a really bad idea.  It is far better to stick with using "sudo" before entering commands into the terminal.  You can use "gksudo nautilus" if you want to use the file manager to copy stuff.

However, if you really want to make your account into a root one, then you need to change you user ID to 0.  Here is a guide [http://linuxgazette.net/issue48/tag/16.html]("http://linuxgazette.net/issue48/tag/16.html")

I really do not recommend it though.  If you do try it then at least make another admin acount for yourself, incase you lock yourself out. Remeber this method is basically a hack, there is only supposed to be one superuser on a linux box - root, who has an user ID of 0.

---

### Post by skippy81 on 2006-05-19
As for mounting your CD rom drive, have you tried rebooting and putting a CD into it which you know works?  Sorry I know it sounds silly, but best to rule out the obvious things- it shouldnt really ever be necessary for you to fiddle with mounts on a CD.  If you are still having problems - can I suggest you give Dapper Drake a spin?

I know it is techincally a beta, but it will be released very soon.  I found most of the niggling problems I had with disks etc dissapeared one I moved to dapper, dapper is the way to go if your PC is less than a couple of years old.

---

### Post by spamzilla on 2006-05-19
Ok so if I shouldn't make my accout a root user, how can I enable sudo so I can execute admin commands?

My laptop is about 3+ years old - should I still use Dapper? What is Dapper and where can I get it from?

---

### Post by redistributer on 2006-05-19
why not just change the root password
sudo passwd root

then when you need root privlidges just type
su
this will bring you into substitue user mode by default the sub user is root

hope this helps

---

### Post by spamzilla on 2006-05-19
[QUOTE=redistributer]why not just change the root password
sudo passwd root

then when you need root privlidges just type
su
this will bring you into substitue user mode by default the sub user is root

hope this helps[/QUOTE]

Yup that helped a lot! Now how do I mount my CD so I can access files on a CD?

I tried a simple reboot, but I still get an error message - "given UDI is not a mountable volume."

Any suggestions?

---

### Post by Al3xanR0 on 2006-05-19
[QUOTE=spamzilla]Yup that helped a lot! Now how do I mount my CD so I can access files on a CD?

I tried a simple reboot, but I still get an error message - "given UDI is not a mountable volume."

Any suggestions?[/QUOTE]

```
sudo mount /media/cdrom0
```

---

### Post by spamzilla on 2006-05-20
[QUOTE=Al3xanR0]```
sudo mount /media/cdrom0
```[/QUOTE]

When I type that into Terminal, I get a message that says

mount: can't find media/cdrom0 in /ect/fstab or /etc/mtab

The same message appears when I type /cdrom into the command line.

Does anyone know why this is happening?

---

### Post by IYY on 2006-05-20
What's the output of 

```
cat /etc/fstab
```

---

### Post by spamzilla on 2006-05-21
I'll only post the important line:

/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

---

