---
title: "Where Did This Floppy Drive Come From!!?"
date: 2010-04-30
forum: General Help
---

### Post by physic.dude on 2010-04-30
Both Windows and Ubuntu think there is a floppy drive connect to the computer. I did build my computer with 2 CD / DVD drives but no floppy drive. Every peace of hardware is up to date but still, Ubuntu and windows see a floppy drive. I cant explane why this is like this, it has been like this ever since I first built the computer about a year or so ago. 

How can I "remove" this floppy drive that I didn't have in the first place? 
Perhaps it can be in the BIOS?

---

### Post by _0R10N on 2010-05-01
Check if there's a line in the /etc/fstab file for some floppy drive
```
cat /etc/fstab
```If you find one, and since there's no floppy attached to your system, then you can safely comment that line.
```

gksudo gedit /etc/fstab

```Insert a # at the beginning of the line, reboot and you're done!!!:)

---

### Post by nixclusive on 2010-05-01
Perhaps you need to disable the floppy disk controller from your BIOS setup utility.

---

### Post by Dayofswords on 2010-05-01
perhaps ( i doubt it though) you connected the cd to a port thats the mobo thinks is floppy only?

---

### Post by physic.dude on 2010-05-01
Ok, this is weird... :-k

The BIOS sees the floppy drive too.

There is an info message on the side when I highlight the "Boot Device Priority" button that says If the CD drive is set to boot first then this will cause there to be a virtual floppy drive. But when I see the priority order, the HHD is first, then the CD drive, then the floppy drive.

Just look at the pictures...
 (And I do have 2 HHD's and 2 CD drives, you just need to select the 1 you want to use in another menu)

---

### Post by dino99 on 2010-05-01
cant you disable that floppy in bios ?

into unbuntu you can also do:

sudo gedit /etc/modprobe.d/blacklist

and add this at the end:

# floppy driver since I don't have one
blacklist floppy

Also, if in the file /etc/fstab there is an entry like this:

/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0

Add a # in front.

Reboot and let us know if you still get the error message!

---

### Post by physic.dude on 2010-05-01
Well, I tried both of your solutions and it still shows up. (i dont quite understand the "#" in the command line, but I tried.)

My motherboard has a floppy connector, but it has never been used. 
I have the ASUS P5Q PRO Motherboard. 

But wait!!!
After a really really long time after I click the floppy drive icon I get this error: (see attachment)

---

### Post by robvas on 2010-05-01
> **physic.dude said:**
> Well, I tried both of your solutions and it still shows up. (i dont quite understand the "#" in the command line, but I tried.)


The # symbol simply comments a line out. So if you had a configuration line in a file, and you put the # in front of it, that line would be ignored. 

It's useful for testing, since you can just go back in the file and take the # out and return the file to it's original state!

---

### Post by physic.dude on 2010-05-02
It is still there.
here is what that file I edited now looks like.

---

### Post by lisati on 2010-05-03
bump on behalf of OP

---

### Post by physic.dude on 2010-05-05
bump

---

### Post by linden940 on 2010-05-05
wow...this is a weird problem that you have...most times its the other way around....having a HARD time TRYING to get a drive to work...not trying to get a drive NOT to work (even more so with there being no drive)

best thing i can think of (as noted all ready) check to make sure the floppy drive slot on mobo is not being used by anything else.

another thing you could try do is..most mobo have a online chat help with computer tecks....maybe it would be a good time to go on there and ask them what is up.

Another thing that COULD be wrong but i dont think it is...or is a big deal...is that your mobo chip set is not working right causing it to think there is a floppy drive..but if there was an error (during the 1 year you have had this computer) i think you would of had OTHER errors with the mobo..but dose not seem like you are.

---

### Post by ubunterooster on 2010-05-05
It is a BIOS setting but as they vary from board to board I can't help much

---

### Post by physic.dude on 2010-05-05
It is not a BIOS setting, and there is nothing in the floppy port on the mobo (not even dust)

---

### Post by physic.dude on 2010-06-01
Well I solved this problem by buying and installing a new floppy drive. (Has a 23 card card reader)
I like this old technology.

Here is what I bought...
[http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=4266375&CatId=287](http://www.compusa.com/applications/SearchTools/item-details.asp?EdpNo=4266375&CatId=287)

---

### Post by cascade9 on 2010-06-01
I know, this it at least semi-solved, but anyway... 

> **physic.dude said:**
> It is not a BIOS setting, and there is nothing in the floppy port on the mobo (not even dust)

If the floppy is still turned on in the BIOS, you can have exactly the issue you are getting. It should have been turned of at this screen- 

[IMG]http://images.hardwarecanucks.com/image/mac/reviews/asus/p5qpro/large/p5q_35.jpg[/IMG]

You might have needed to poke around in 'advanced' as well (either in 'chipset' or 'onboard devices configuration'). If the floppy was turned at both of those areas, then it must have been the virtual floppy drive. Without a P5Q Pro to check with I cant be 100% sure ;)

---

### Post by physic.dude on 2010-06-02
> **cascade9 said:**
> I know, this it at least semi-solved, but anyway... 



If the floppy is still turned on in the BIOS, you can have exactly the issue you are getting. It should have been turned of at this screen- 

<picture>

You might have needed to poke around in 'advanced' as well (either in 'chipset' or 'onboard devices configuration'). If the floppy was turned at both of those areas, then it must have been the virtual floppy drive. Without a P5Q Pro to check with I cant be 100% sure ;)

I already searched the entire bios.
You may notice that the bios warns you that it will make a virtual floppy drive if one of the settings in the boot tab are set in some (not so strange) way.


[URL="http://ubuntuforums.org/showthread.php?t=1499378"]Ps. Also related to this floppy drive can you help me here?
http://ubuntuforums.org/showthread.php?t=1499378[/URL]

---

