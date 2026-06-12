---
title: "Deleting GRUB selections"
date: 2009-12-01
forum: General Help
---

### Post by S2UIRR3L on 2009-12-01
I have a dual-boot laptop (I think it's called a grub loader?). Every time I update Ubuntu, there's a new selection in the list of operating systems at start up. There's like 8 Ubuntus and one for Windows-XP.

**_My question is_: How do I delete the 6 older versions of Ubuntu from the grub loader selection screen at start up? Can I do it without terminal?**

I would love to get rid of XP all together, but I use one program that doesn't like Ubuntu. Thanks for all the help. I'm sure this was mentioned before, but I don't know how to use Ubuntu Forums yet.

Cheers!
-Squirrel

---

### Post by 0cton on 2009-12-01
you need to edit /boot/grub/menu.lst (it may be in another directory, search for menu.lst in /boot )
you need root privileges for that
I'd recommend just opening the menu.lst and pasting it's content in here (or just the contents near the end of the file that contain the menu listings) so we could tell you what to remove so you don't end up messing with things
look for something like this:
title		Ubuntu , kernel 2.6.27-7-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda6 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
if you want to directly open it as root and be able to edit
type in a terminal
sudo gedit /boot/grub/menu.lst 
and do your job.

---

### Post by john newbuntu on 2009-12-01
One way of doing this is by removing the older kernels using synaptic package manager and then run a sudo update-grub.
Type the following from a command line:
uname -smr
it will list the kernel that is being used currently.  Say it is Linux 2.6.31-15-generic i686.
So, you may want to keep the previous one (-14) and remove all prior versions using synaptic. Search for "linux-headers" in synaptic.
Once these are removed, run a sudo update-grub and you are good to go.

---

### Post by oldfred on 2009-12-01
The extra kernels do not take a lot of space so I only houseclean occasionally. But I only show two in menu.lst. I have not figured out how to do that yet with grub2.

This stanza in menu.lst controls how many versions of the kernel it adds on updates, one # is the command two ## are comments in this section of menu.lst.

gksudo gedit /boot/grub/menu.lst 
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
[COLOR=Red]# howmany=2[/COLOR]

then run
sudo update-grub

---

### Post by n_spect_r on 2009-12-01
I tried these things but my menu list is empty.  Still I have three different Ubuntu options plus windows and the memory test.

What now?

---

### Post by NFblaze on 2009-12-01
Do what John Newbuntu suggests.


Open a terminal type in *uname -smr* to find out your current kernel being used.

Open up *System > Admin > Synaptic*

In the search box in synaptic type in '*linux-image*" and delete all the kernels (linux-images) except for your current one and the second newest one that worked.

Then go back to the terminal and type *sudo update-grub*.

---

### Post by S2UIRR3L on 2009-12-02
Thanks a million guys... I'll let you all know how it goes!!!

Cheers!
-Squirrel

---

### Post by S2UIRR3L on 2009-12-17
John Neubuntu & NFBlaze
THANK YOU SO MUCH!!!

John gave the easiest solution and Blaze gave the clearest instructions.
I did exactly as instructed and now I only have one choice for Ubuntu:

2.6.28-16-generic i686 (Ubuntu)
2.6.28-16-generic i686 (recovery)
2.6.28-16-generic i686 (mem test)
Windows XP Home Edition (SP2)

It doesn't look exactly like this, but it's close enough and I thank you all!
You guys, along with Ubuntu Forums have made my Linux experience
that much greater. Thank you so much. I look forward to learning more!

Cheers!
-Squirrel

---

