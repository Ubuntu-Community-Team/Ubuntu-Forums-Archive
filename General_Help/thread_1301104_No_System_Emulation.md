---
title: "No System Emulation"
date: 2009-10-25
forum: General Help
---

### Post by polski_orzel on 2009-10-25
Hey guys, I know this isn't exactly Ubuntu, but I know you're the smartest people around, so maybe you can help me figure this out...

So when I was installing Kubuntu I knew I wanted to do a dual boot, so I split the harddrive up. When I did that I deleted my Windows partition, but I forgot to delete the system recovery partition (or whatever it's called) I'm pretty sure I did it now after making a GParted disc, but I'm still having trouble loading a Windows install disc, because every time I do, it just says, "No system emulation" (It may say detected, I can't quite remember).

Also, when I start up my computer, I get to choose my OS (Which is normal), but I still get an option for Windows. I think it's called something like "Windows (Recovery) or (Safe mode)", but that makes no sense, because I have no Windows on my computer. I dunno what to to :(

---

### Post by rockstarrem on 2009-10-25
You forgot to delete the system recovery partition? I wouldn't do that anyway. With that partition you can get Windows back without the disc... boot from it and install Windows from that if you want.

---

### Post by polski_orzel on 2009-10-25
> **rockstarrem said:**
> You forgot to delete the system recovery partition? I wouldn't do that anyway. With that partition you can get Windows back without the disc... boot from it and install Windows from that if you want.

That doesn't work. I've tried it before, and I get a screen that says that I should either put in a windows install disc and restart or contact by system administrator... so yeah

---

### Post by P4man on 2009-10-25
boot a livecd and run partition editor. then you can remove the partition and make the other one bigger if you want.

The windows menu item will dissapear if you update grub. just run

```
sudo update-grub
```

or 
```
sudo update-grub2
```

if you use grub2 (default for ubuntu 9.10)

---

### Post by polski_orzel on 2009-10-25
Okay, well that didn't seem to work. Now what happens is that I still have the "Windows (Loader)", but when I click it, it just goes into another screen that says it's invalid, and then I get taken back to the OS selection screen.

But yeah, the exact message I get when I try to load the discs is "No Emulation   System 00" and on the next line "No Emulation   System 01".

I'm not quite sure what to do.

---

### Post by P4man on 2009-10-25
what did you do so far? The option will only be removed after deleting the partition and then rerunning grub update (from the installed ubuntu I guess)

---

### Post by polski_orzel on 2009-10-25
> **P4man said:**
> what did you do so far? The option will only be removed after deleting the partition and then rerunning grub update (from the installed ubuntu I guess)

I used GParted to delete the windows partition, and then I ran the grub update. The weird thing is, I have two separate completely empty partitions. One is the big one, that has like 300gb of space, and the other only like 100mb or something.

---

### Post by polski_orzel on 2009-10-26
Any other ideas, guys? I'm in Kubuntu right now (32-bit). I'm downloading a new Windows 7 disc, but  don't think this has anything to do with Windows... I think it's just my computer being weird.

---

### Post by P4man on 2009-10-26
perhaps give a little more info because I dont quite understand whats going wrong.. Is kubuntu booting correctly? Is it just a matter of having a windows item in grub? Is the partitioning wrong somehow (perhaps a screenshot from gparted) ?

---

### Post by polski_orzel on 2009-10-26
Okay, I'll explain it a bit better.

My Kubuntu runs perfectly fine (save for the Flash, but I hear that's a common problem in the newer version of all Ubuntu distros). Here's where the problem lyes:

I'm trying to NOW install Windows. Whenever I try to boot from the Windows disc I get this screen:
[IMG]http://img29.imageshack.us/img29/1988/sspx0230.jpg[/IMG]

No matter what I press, it just goes to the next line and says "Enter a choice", so I just press the enter-key. Then this happens:
[IMG]http://img237.imageshack.us/img237/802/sspx0231f.jpg[/IMG]

I have no idea what to do, so I just press enter, and then it takes me to my regular OS selection screen (I get this screen normally upon boot):
[IMG]http://img23.imageshack.us/img23/8427/sspx0232.jpg[/IMG]

As you can see, there's an option for Windows Vista, this what happens when I select it:
[IMG]http://img29.imageshack.us/img29/2486/sspx0233.jpg[/IMG]

After I press a key, it just goes back to my regular OS selection screen

-------------------

Here's the photo I took of G-Parted of my partitions:
[IMG]http://img39.imageshack.us/img39/4107/sspx0234.jpg[/IMG]


I don't really no what other information I can give you, but if you need to know anything more, I'll be more than happy to try and dig it up.


Thanks so much for helping so far, I really appreciate it.

---

### Post by P4man on 2009-10-26
perhaps you could make those screenies a bit bigger ?
:)

Anyway, if you cant boot the windows cd or dvd, then it has nothing to do with either ubuntu or your harddisk partitioning. I suspect its a badly burnt disc or a bios problem. Do you get the "press a key to boot from cd" message before the ones you posted ?

As for the grub menu, its still has an entry for windows on your harddrive. And that windows is no longer there, so its normal it doesnt work. update-grub(2) should take care of that, but lets not waste too much time on that, because after installing windows, grub will be wiped anyhow and you will need to reinstall grub from a livecd to have a dual boot.

As for your partitions. You have a small unpartitioned space at the beginning of your drive. If I were you, I would move the extended (light blue) partition to the end (right) of your drive. The rest will become one unified unpartitioned space were you can install windows. An extended partition is a container for the logical partitions inside. You cant move the logical partitions except for moving them inside the extended.

Hope that makes sense to you :)

---

### Post by polski_orzel on 2009-10-27
Yeah, it makes a bit of sense. I'll try burning  yet ANOTHER disk, haha.

And no, I don't get an option to run from a disc by pressing a button, because my discs run automatically.

Thanks a lot for the help!

---

### Post by alphaniner on 2009-10-27
The Windows installer will ask you to 'Press any key to boot from CD/DVD'.  At least, every copy of Windows I've ever installed has done so.

---

### Post by polski_orzel on 2009-11-08
Nothing works so far... I tried plugging in an external harddrive, and then making it my default boot drive. It doesn't do anything,obviously, when I just let it sit; however, I when I put in a disck afterwards it just does the same thing...

I don't know how to merge the extra space with the partition manager, and I still can't get rid of the darn Windows loader option, even though I don't have it installed.

Anymore ideas before I decide I should take it in for repairs?

---

