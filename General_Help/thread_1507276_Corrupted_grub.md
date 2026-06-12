---
title: "Corrupted grub?"
date: 2010-06-11
forum: General Help
---

### Post by red oak on 2010-06-11
I have a Jaunty, I believe.

Suddenly, I'm not able to boot.

It starts grub, but then very fast goes into a logo screen just before the login and stalls.

It does not respond to holding shift down, clicking "e" or to anything else for that matter.

I'm on live CD right now of a very old version of Ubuntu.

I can view most of the files, but it does not allow me to do anything with them and I don't even know enough to make myself sudo there, all my attempts fail as "invalid user", I suspect that I don't know how to get to the proper root.  

It looks to me that it should be a simple matter of replacing or editing a corrupted file if I only knew how to do it.

I tried to read the manual but it will take me days or weeks probably to learn the basics.

If I could be pointed in the right direction I would appreciate it greatly.

---

### Post by Mark Phelps on 2010-06-11
Essentially, what you would need to do is the following:
1) Boot from a Jaunty LiveCD
2) IF your root partition from the hard drive is not already mounted, then mount it
3) Using a text editor (gedit), open the menu.lst file on the hard drive
4) Look for the boot stanza you're using
5) If it has a kernel parameter of "quiet", delete that parameter
6) Save the menu.lst file
7) Reboot

Then, when you reboot, you will see status messages scrolling by on the screen.  Hopefully, when the machine stops, the last few messages on the screen will indicate the errors.  You can write those down and come back here with the details.

---

### Post by red oak on 2010-06-11
Thank you Mark,

I have 2 instances of "quiet". Should I delete both?

> title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		55f87d8e-472a-44dc-a873-75b7983110e5
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=55f87d8e-472a-44dc-a873-75b7983110e5 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-20-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid		55f87d8e-472a-44dc-a873-75b7983110e5
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=55f87d8e-472a-44dc-a873-75b7983110e5 ro  single
initrd		/boot/initrd.img-2.6.31-20-generic

title		Ubuntu 9.10, memtest86+
uuid		55f87d8e-472a-44dc-a873-75b7983110e5
kernel		/boot/memtest86+.bin
quiet

However, I'm not "authorised" to save anything when I'm using a live disk.

I want to add that it's been working fine for months of daily use... :p

---

### Post by oldfred on 2010-06-11
Have you tried the recovery mode. it also does not have the quiet and in 90.10 gives more options.

You may have to use gksudo gedit but in the liveCD there is no Password.

---

### Post by dino99 on 2010-06-11
> **red oak said:**
> Thank you Mark,

I have 2 instances of "quiet". Should I delete both?



However, I'm not "authorised" to save anything when I'm using a live disk. [COLOR="Blue"][SIZE="5"]you need to use[/COLOR] [COLOR="Red"]sudo [/SIZE][/COLOR] with the hdd path

I want to add that it's been working fine for months of daily use... :p

let the "quiet" where they are

---

### Post by red oak on 2010-06-11
Thanks so much

I tried again and this time while holding the shift key down I was able to login.  Do I understand correctly that this is a Recovery Mode?

So now, how should I edit my menu.lst?  Delete "quiet" from the line:

kernel /boot/vmlinuz-2.6.31-20-generic root=UUID=55f87d8e-472a-44dc-a873-75b7983110e5 ro **quiet** splash  ?

---

### Post by red oak on 2010-06-11
OK, it seems to be **SOLVED**.

While in Recovery Mode I simply reinstalled Grub-pc and Grub-common (those marked as already installed) through the Synaptic Package Manager.

Then I was able to boot as usual...

Thanks for all the help

---

