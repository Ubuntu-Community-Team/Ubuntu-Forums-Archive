---
title: "&quot;Error 21&quot; After 2nd Install"
date: 2009-09-12
forum: General Help
---

### Post by happytofu on 2009-09-12
So, my goal was to install Ubuntu onto an external hard drive for future usage with Windows computers, such as lab computers at school, my netbook, and so forth.  I'd boot to the external HD, essentially be running my own computer, but then the host computer remains unharmed and everyone is happy.

I succeeded in the installation, but because I did this through my laptop (whose sole OS is Ubuntu), I can no longer boot my laptop without having the external HD plugged in and telling Ubuntu which hard drive to boot.

So, I need help telling it to default to "/dev/sda1".


And second, a question: If I do what I'd originally intended (booting random Windows-only computers to this external HD), do I run the risk of causing this error on them as well and/or blowing up the world?  :<

Ie, was this a terrible experiment from the start?


I'd really appreciate any help you can give.  Thanks!

---

### Post by TetonsGulf on 2009-09-12
I have had luck with disconnecting the hard drive in the computer so that only the external can be found at installation time. This makes it so Grub is only installed on the external drive and not your laptop.

Never had a problem with jumping onto another computer.

Check this out for tips...

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by happytofu on 2009-09-12
Unfortunately, I've already done the install.  I really just need to fix my laptop now.

I know I need to do something along the lines of,
> sudo grub
find /boot/grub/stage1 or find /grub/stage1
root(hdX,Y)
setup(hd0)
quit

...but I'm not getting anywhere.  I get:
> grub > find /boot/grub/stage1
   (hd0,0)
   (hd1,0)
grub > root(hd1,0)
   Error 27: Unrecognized command"

I realize it's probably just something stupid that I'm doing wrong, though. :<

---

### Post by TetonsGulf on 2009-09-12
Ok, well there are a couple solutions from what I can gather.

Simplest would probably be to go to [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) download and follow the instructions there.

I did find a couple other sites in my own post history that were useful though... try:

[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/](http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/)

and 

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

Hopefully you find what you need.

It is simply a misdirection, looking for grub in a location that no longer exists, but they are maddening. I had one drive me crazy for three days!

---

