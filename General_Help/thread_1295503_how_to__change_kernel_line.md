---
title: "how to  change kernel line"
date: 2009-10-19
forum: General Help
---

### Post by Moses1200 on 2009-10-19
hello, someone in the furom wrote how to fix a problem with the keyboard. he write 'add to the kernel line.' what does it mean?
and below he wrote more instructions. 
this is my first days with ubuntu and i don't know how to this.
thank you for your help. his instructions are hereby attached:

 				 				**Re: Ubuntu 9.04/Dell Vostro 1520 Keyboard/Touchpad hang** 			
 			 			 		   		 		 		I have solved the problem on my Vostro 1320 in
/boot/grub/menu.lst

add
i8042.reset i8042.nomux i8042.nopnp i8042.noloop
to the kernel line.

kernel /boot/vmlinuz-2.6.28-13-generic root=UUID=91013859-dfec-4a84-ae8d-21233f16c89a ro quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop

---

### Post by Giblet5 on 2009-10-19
He's referring to grub's /boot/grub/menu.lst file.

(He says) that if you ```
sudo gedit /boot/grub/menu.lst
```

then scroll down to where the kernel definitions are, and make that change, then everything will be peace, happiness, and cheesecake.

I'll wager that the economy will still suck, but it's worth a try, right?

Once you've edited it, it would be wise to write the changes to grub's boot record.

Run ```
sudo fdisk -l
```

What's the first disk drive? Is it /dev/sda? Let's assume that it is: ```
sudo install-grub /dev/sda
```

Reboot, and all done. Wow, my boss just called. I'm getting a raise! It worked!

---

### Post by golanbatrac on 2009-10-19
You can open /boot/grub/menu.lst with gedit by typing the following into the terminal:

```

gksudo gedit /boot/grub/menu.lst

```

Scroll down toward the end of the file, and you'll see something like this:

```

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-15-generic
uuid            3f4f50c8-11e4-4259-a8c7-f474d69bd46b
**kernel          /boot/vmlinuz-2.6.28-15-generic root=UUID=3f4f50c8-11e4-4259-a8c7-f474d69bd46b ro quiet splash**
initrd          /boot/initrd.img-2.6.28-15-generic

```

Add 'i8042.reset i8042.nomux i8042.nopnp i8042.noloop' to the kernel line (in bold above).  Save and reboot.

---

### Post by P4man on 2009-10-19
detailed info on how to do that here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

select the appropriate scenario on the right hand (depending if you want to this for a livecd session, test it once on an installed or make it permanent)

ubuntu community gets a raise now ? ;)

---

### Post by P4man on 2009-10-19
golanbatrac and Giblet5, your solution will work... until the next kernel is released. Its better to do it like its outlined in the community help page I linked. Try it first by changing it from grub, if it works make it permanent and for all kernels by adding it to "# kopt=".

---

### Post by Giblet5 on 2009-10-19
> **P4man said:**
> golanbatrac and Giblet5, your solution will work... until the next kernel is released. Its better to do it like its outlined in the community help page I linked. Try it first by changing it from grub, if it works make it permanent and for all kernels by adding it to "# kopt=".

Gotcha. Thanks.

---

### Post by golanbatrac on 2009-10-19
> **P4man said:**
> golanbatrac and Giblet5, your solution will work... until the next kernel is released. Its better to do it like its outlined in the community help page I linked. Try it first by changing it from grub, if it works make it permanent and for all kernels by adding it to "# kopt=".

I did not know this.  Thanks.

---

### Post by Moses1200 on 2009-10-19
thank you, but it says i don't have permission to do this.

---

### Post by P4man on 2009-10-19
> **Moses1200 said:**
> thank you, but it says i don't have permission to do this.

to do what exactly?

---

### Post by golanbatrac on 2009-10-19
You can open /boot/grub/menu.lst with gedit by typing the following into the terminal:

```

gksudo gedit /boot/grub/menu.lst

```

Scroll down and you'll see something like this:

```

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
**# kopt=root=UUID=3f4f50c8-11e4-4259-a8c7-f474d69bd46b ro**

```

Add 'i8042.reset i8042.nomux i8042.nopnp i8042.noloop' to the '# kopt' line (in bold above) so that the line looks like this:

```

# kopt=root=UUID=3f4f50c8-11e4-4259-a8c7-f474d69bd46b ro i8042.reset i8042.nomux i8042.nopnp i8042.noloop

```

 Save and reboot.

---

