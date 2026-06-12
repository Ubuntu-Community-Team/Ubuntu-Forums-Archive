---
title: "where to find C headers for my kernel"
date: 2006-04-20
forum: General Help
---

### Post by PriceChild on 2006-04-20
Hi, i'm trying to reinstall vmware player  after building my new 2.6.16.9 kernel ((from front page of kernel.org))

However:
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The kernel defined by this directory of header files does not have the same
address space size as your running kernel.

So how do i get the 2.6.16.9 headers?

Thanks for any help, Pricey

---

### Post by PriceChild on 2006-04-20
bump

---

### Post by superhac007 on 2006-04-20
[QUOTE=PriceChild]Hi, i'm trying to reinstall vmware player  after building my new 2.6.16.9 kernel ((from front page of kernel.org))

However:


So how do i get the 2.6.16.9 headers?

Thanks for any help, Pricey[/QUOTE]

if you dont have the kernel headers:
$ sudo apt-get install linux-kernel-2.6.10-5

then make a sym link:
$ cd /usr/src
$ sudo ln -s linux-headers-2.6.10-5 linux

---

### Post by PriceChild on 2006-04-20
But i need the ones for 2.6.16.9 don't I?

Shouldn't i have them seen as i compiled my kernel?

Why won't is it telling me the address space size is different?

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=PriceChild]But i need the ones for 2.6.16.9 don't I?

Shouldn't i have them seen as i compiled my kernel?

Why won't is it telling me the address space size is different?[/QUOTE]
did you symlink linux and appropriate source directory? 
sudo ln -s /usr/src/kernel-image-2.6.16.9 /usr/src/linux

to see if it's linked, I think you do
ls -l /usr/src

of course, fix the "/usr/src/kernel-image-2.6.16.9" to your source directory name. Also I remember seeing two things about this:
1. people seem to need to remove and reinstall vmware after kernel update
2. a bug in vmware (some kind of incompatibility with newer kernels??) that's fixed after downloading and applying a patch (I have no idea where i saw this, but was around here in the ubuntu forum. try doing a forum search within the forum for this one).

---

### Post by PriceChild on 2006-04-20
Number 2 was right!!!

Seems many people are having troubles with the 2.6.16 kernel.

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=PriceChild]Number 2 was right!!!

Seems many people are having troubles with the 2.6.16 kernel.[/QUOTE]
do you have the link to that handy? i'd like to check that out again (refresh memory) :)

---

### Post by PriceChild on 2006-04-20
Haven't got a specific link sorry, the vmware forums are down for me, are they for you?

I just foud random search results on google saying it.

Lost them now sorry

---

### Post by PriceChild on 2006-04-20
UPDATE

Found this post:
[http://archlinux.org/pipermail/arch/2006-April/009647.html](http://archlinux.org/pipermail/arch/2006-April/009647.html)

> 
>[I] 2.6.16 kernels need to have the vmware-any-any-update to allow for
[/I]>[I] kernel modules to compile. Do a Google search for it, or download it
[/I]>[I] from here:
[/I]>>[I] [http://ftp.cvut.cz/vmware/]("http://ftp.cvut.cz/vmware/")
[/I]>>[I] I think the latest version is 101

So how do i use this?
[/I]

---

### Post by towsonu2003 on 2006-04-20
[QUOTE=PriceChild]
So how do i use this?
[/I][/QUOTE]
not sure. one thing, you'll use this thing
[http://ftp.cvut.cz/vmware/vmware-any-any-update101.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update101.tar.gz)

try untarring to see if there is any documentation in it. also, check out if you can find anything helpful on google.com/linux with keyword
vmware-any-any-update

---

### Post by PriceChild on 2006-04-20
I've got it working!!! :)

Go team... reasonably simple, just a matter of not running the vmware-config.pl file when asked for in the initial instillation.

Then running the runme.pl file inside that tar.

Think i should message the owner of the following post [http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275) how to get it working on newer kernels... or perhaps make a new How-To :P

Pricey

---

