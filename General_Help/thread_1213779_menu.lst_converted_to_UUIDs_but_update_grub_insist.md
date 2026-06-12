---
title: "menu.lst converted to UUIDs but update grub insists on adding partition numbers"
date: 2009-07-15
forum: General Help
---

### Post by vmp on 2009-07-15
Hi,

Some time ago I converted completely my menu.lst (and fstab) to UUIDs and got rid of completely the "root=(hdX,Y)" options but now in every update that a new kernel is available, the update script wants to install menu.lst file with partition numbers again.

Is there any way to prevent this and avoid having to manually create the menu.lst file each time?

This behavior remains unchanged from 8.10 to 9.04 that I am using now.

---

### Post by Kraut~salat on 2009-07-15
Well, the installation system should ask you if you want to installl the new menu.lst or keep your old one. I usually keep my old one and only add an new entry for the new kernel. 
I'm a bit confused that updates want to sell you partition nummbers. I always had UUIDs in my menu.lst.

I don't think that you can tell the updater to use UUIDs instead of numbers. All the programm does is trying to install a new menu.lst on your system. If that comes with numbers (a decision the packager made, not the install program) then you have to live with it or simply not install a new menu.lst

---

### Post by philinux on 2009-07-15
Maybe it's picking something up from this file. Not an expert on this file i.e why it exists.

/var/lib/ucf/cache/:var:run:grub:menu.lst

---

### Post by CatKiller on 2009-07-15
> **vmp said:**
>  Some time ago I converted completely my menu.lst (and fstab) to UUIDs and got rid of completely the "root=(hdX,Y)" options but now in every update that a new kernel is available, the update script wants to install menu.lst file with partition numbers again.

I don't think you got them all :)

In your menu.lst there's a section that provides the template for the new entries that you'll get when you install a new kernel. You need to change that too. It will look something like this:

```

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=f0f60ece-7b14-40b8-aca3-c985d66ceac9 ro elevator=deadline

```

It's that last line that you'll need to update with your UUID.

---

### Post by geirha on 2009-07-15
And also change the
```
# groot=*<uuid>*
```

Once done, run ```
sudo update-grub
``` This is what is run when you install/remove a kernel. It removes all uncommented lines (lines not starting with a #) between 
```
### BEGIN AUTOMAGIC KERNELS LIST
and
### END DEBIAN AUTOMAGIC KERNELS LIST

```

and then rebuilds the list with all currently installed kernels, giving each entry the values of those commented variables. 

So after changing menu.lst, always run update-grub and check the resulting menu.lst. Then you won't get any surprises next time a kernel is installed.

---

