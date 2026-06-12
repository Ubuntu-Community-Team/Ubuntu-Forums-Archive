---
title: "boot problem"
date: 2010-01-12
forum: General Help
---

### Post by leorth on 2010-01-12
Ubuntu hello friends,
Get 1 year using ubuntu (8.04 in fact) and could not have been a better desicion but I have a problem to see if they help me

the first thing on my pc I have 2 operating syst, window and ubuntu, win because I keep some programs work multitrack audio editing
and I have not yet learned to use this type of program in ubuntu.

a recently discovered virus and trojan on my win partition so I decided to reformat the partition, the problem arose
after completing the formatting as it never gave me the option but to start with ubuntu, before it gave me the option of choosing
begin with that operating system. If it is, the question is there not formatted the whole pc? Not so, the Ubuntu partition is intact
and that it will win because the partition has the capacity hard drive that I had prior to formatting.

my question is
How do I return to have the option to start with a opetartivo or another?
With the help of Live-CD could recover the files kept in ubuntu. But I would like it to boot because I really liked the operating system.
I thank in advance the help they can offer consultation forums but none have given me an answer.
sorry not write or speak English, sorry for the text, if they can give me an answer in Spanish would be great, otherwise it's fine, too

Leo Castillo

---

### Post by Mickser_52 on 2010-01-12
Hola Leo,

I found this explanation on another site which might be the answer to your problem:

[You have got a problem with the programme which decides, which System to select. this program is called "grub"
grub is installed by ubuntu automatically. Normally /boot/grub/menu.lst knows the paths of the Operating systems automatically (Windows and Other OS)
So If Windwows is the only OS which is offered, there is a problem with grub.
If Ubuntu is installed properly, you would have to boot into ubuntu via installations-Cd and look into

/boot/grub/menu.lst to see, what happened with grub.
It could be, that windows is the first system which boots automatically. Or other possibilities of errors.
good luck :-)]

It may not solve your problem but it is somewhere to start.

---

### Post by Sef on 2010-01-12
Download [Super GRUB Disk]("http://www.supergrubdisk.org/index.php").   Windows only sees windows oses.

---

