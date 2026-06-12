---
title: "Ubuntu 12.04 boot problems . Pictures added"
date: 2012-10-06
forum: General Help
---

### Post by ronssacramental on 2012-10-06
Hello everyone,

As you can see I am new to this forum as well as Ubuntu. Want to learn C in Linux so downloaded ubuntu and installed using wubi but when it started i got blank screen. I thought it did not install so i removed it using easyBCD method but while doing so there was no partition created.

I tried installing three times and figured out that when i boot in ubuntu the brightness is at 0 and needs to be increased. After that ubuntu was installed and after few days when i boot in it i get the GRUB menu. 

[IMG]http://imageshack.us/a/img339/3336/dsc01397t.jpg[/IMG]
[IMG]http://imageshack.us/a/img441/2959/dsc01402yt.jpg[/IMG]
[IMG]http://imageshack.us/a/img89/9308/dsc01405sv.jpg[/IMG]


As you can see in images that when i boot i get 3 options for ubuntu. And when i select it it boots in grub and also there is no partition created for ubuntu (i had specified 30gb during installation). So how do i fix all three problems and start using ubuntu. 

I tried so many tricks like the live usb, boot repair and all.

System info - Hp dm4 notebook 
Intel core i5  M460@2.5 ghz
64 bit OS

---

### Post by cway00 on 2012-10-06
start by following the this thread to solve the issues about the boot problem

[HTML]http://ubuntuforums.org/showthread.php?t=2065847[/HTML]

---

### Post by Mark Phelps on 2012-10-06
Wubi installs do not create Ubuntu partitions -- which is why you won't find one.  Wubi installs ubuntu into a single FILE inside an existing NTFS partition.

---

### Post by ronssacramental on 2012-10-06
> **cway00 said:**
> start by following the this thread to solve the issues about the boot problem

[HTML]http://ubuntuforums.org/showthread.php?t=2065847[/HTML]

Tried everything but still the same problem :( any help would be appreciated .

---

### Post by ronssacramental on 2012-10-06
Anyone please help really need this working in order to start working on college C programming labs. 

I have some more info which might help . After finishing the boot repair when i go into  GRUB locations tab as mentioned in other thread there are no options to select. Everything is unselected and I cannot select anything.

---

### Post by bcbc on 2012-10-07
This is likely your problem: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

This can be caused by some incompatible hardware or forced shutdowns.

---

### Post by ronssacramental on 2012-10-07
[http://paste.ubuntu.com/1264891/](http://paste.ubuntu.com/1264891/) 

If this helps

---

### Post by ronssacramental on 2012-10-07
> **bcbc said:**
> This is likely your problem: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

This can be caused by some incompatible hardware or forced shutdowns.

I tried to follow the instructions but it tells me that found.ooo is not recognized as an internal or external command.

---

### Post by ronssacramental on 2012-10-07
Need some reply please help .... need to get it working fast anyone ???

---

### Post by bcbc on 2012-10-07
> **ronssacramental said:**
> I tried to follow the instructions but it tells me that found.ooo is not recognized as an internal or external command.

Slow down and read the link I provided carefully. found.000 is not a command, it's a directory, and it's zero's, not o's. 

You need to:
1. Run chkdsk which requires a reboot, and don't hit any key while it completes. (see the link for how to do this from the windows desktop)
2. Run a command prompt as an administrator.
3. Look for the found.000 directory.

NOTE: there may be other found.??? directories - windows creates one for each time it runs chkdsk and recovers files.
So there could be a found.001 and a found.002.

Inside it you're looking for a file file0000.chk that's over 5GB - whatever the size of your install was. You need to move that back to the \ubuntu\disks folder, renaming it back to root.disk (instructions provided on the link).

---

