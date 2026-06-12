---
title: "powerdown USB"
date: 2012-01-02
forum: General Help
---

### Post by jefelex on 2012-01-02
I need to find the command line option to power down a USB drive.

I know that Nautilus can powerdown the device, but I have not been successful with udisks --detach /dev/sdb or udisks --unmount /dev/sdb1 - this eludes me - I read all the udisks documentation, but no luck!

Any ideas?

TIA :-)

John

---

### Post by spacecheck on 2012-01-02
You could use sudo umount /dev/sdx
so the USB drive would no longer be mounted (no read/write activity) but I doubt you can cut power to the device for more than a few seconds, before the daemon again snoops around looking for new devices. You can power it down for safe removal per disk utility but, that isn't what you ask for, nor, do I believe, does it keep the power off for more than long enough to pull the USB plug/drive out.

Good luck!

---

### Post by chipbuster on 2012-01-02
I've had success with umount, but I'm using Thunar, not Nautilus, so they may behave differently in terms of remounting removed partitions.

---

### Post by jefelex on 2012-01-02
powerdown and umount work great with nautilus - no problem there, powerdowns the USB fine, as well as unmount and leave the power on in case I want to remount it.

I have a script file that at the end calls for the USB drive to be unmounted.  Currently I use 

udisks --unmount /dev/sdb1  

which works great to finish writing data to the USB and unmounting it ready for removal, which is what I then do.

But I'd really like the option to totally powerdown the USB - there is no difference to what I have now, except that the power to the USB port has been switched off.  That is supposed to happen with 

udisks --detach /dev/sdb1

According to man udisks --detach  is supposed to powerdown the USB port. I know linux can do it - nautilus can - I'd like to know what command or set of commands that it uses to do that.

I have searched everywhere for the exact syntax - 

/udisks --detach devicefile --detach-options options

but nowhere are there listed any options

???

---

### Post by spacecheck on 2012-01-02
"Eject" and umount will remove power to the device for a few moments, but not completely turn power off to the port. It cannot totally powerdown the USB port because the port would no longer be able to detect/power up the next inserted device.

---

### Post by jefelex on 2012-01-02
Solved - you have to call the unmount before you call detach - then it works as advertized!!

Yay :-)

John

---

### Post by spacecheck on 2012-01-02
I disbelieve power to the port is cut completely for more than a few seconds. Nonetheless, why not post the syntax?  :-)

---

