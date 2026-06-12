---
title: "Newbie to ubuntu needs help :)"
date: 2011-02-07
forum: General Help
---

### Post by trell88 on 2011-02-07
Hey guys,

Basically i have a problem with my toshiba laptop.

I have windows 7 installed and it has a fault.

I have booted it up on ubuntu from usb,

i want to check my hard drive and ram etc for corruption etc through ubuntu but what i need help with is how.

also does any one know how to burn windows 7 onto a disk that can be used as a boot up disk? ( through ubuntu )


thamk you in advance

---

### Post by compactbrain on 2011-02-07
to check the hard disk for corruption, boot into ubuntu
go to System > Administration > Disk Utility, it will tell u all the info on your hard drive, as for the ram theres the memtest option in grub, ive never used it before but maybe someone has some more info on that

---

### Post by markthekdeguy on 2011-02-08
Just before you start ... 

Disk Utility, if its on the USB, will check ALL file-systems or disks it can see, so be very careful, because a single click in the wrong place and bye bye data. No windows, no nothing. 

Do please backup your important data *if you can see  it* onto another USB drive, if you have a large enough and spare one, or something,

There are other free HD maintenance programs, ( like UBCD) but are very technical, and as a Newbie, these can be more dangerous than Ubuntu's humble disk utility anyway !

Ubuntu should have at boot time, a MEM TEST option,
the Ubuntu Live CD did, many free utility CDs do too. 
i guess the USB image will too. but i cant remember, as i haven't used Ubuntu on USB for a long time.

If the fault is on the windows 7 part of the disk, and can be fixed
you may be lucky, and disk utility may fix it. i've done it before.

Beware !
Most laptops do not come with a Windows 7 CD.  they should.
but they dont. :mad:  when you first use your (new) laptop it should tell you
to make 'backup' or 'recovery' disks. this is very important.

There is usually a 'hidden' part of your hard disk where, if everything
crashes, the windows 'setup' programs live, but is only usable to set up Windows. it is not Windows 7 itself. and should generally be left alone, unless you have a proper Windows 7 install CD.
it is sometimes used to make the recovery disks or sometimes at boot time,  a menu may offer to start a Windows recovery program.
- it depends how Toshiba have done it.

You risk the erasing this special partition, (if it exists) and are unlikely
to get Windows back. if this happens you may have to buy <!> a Windows CD from the company who sold the laptop.

I just want to save you from deleting anything you may later need :)
there are other ways, but i'm sure other folks will write in with better suggestions than I have.

Mark
:guitar:

---

### Post by trell88 on 2011-02-08
ok,

on the disk utility it is telling me there are a few bad sectors

ID5          reallocated sector count
ID197      current sector count

how do i fix these??


thanks you for your advice :)

---

### Post by markthekdeguy on 2011-02-12
sorry, i have been away for a while.

I hope you found an option to fix these bad sectors ?

these hard disc checkers are of little use if they cant
offer to fix any problems they find :D

I hope you have had good luck 
Mark

---

