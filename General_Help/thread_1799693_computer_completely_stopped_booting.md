---
title: "computer completely stopped booting"
date: 2011-07-08
forum: General Help
---

### Post by Muster Mark on 2011-07-08
Hi,

[SIZE=3]History[/SIZE]
So, first of all, this is my sisters computer so I am not sure exactly what happened.  I had installed ubuntu alongside WinXp a couple of weeks ago.  Today she booted into xp for the first time and accidentally launched some system restore option.  A dialog box appeared and told that if she continued, everything on her disk would be erased. apparently, there was no indication of how to not to continue, so she shut it down by holding the power button.

[SIZE=3]Symptoms[/SIZE]
Now, it won't boot.  Not even to grub, it just cycles where the screen comes on, a courser blinks in the top left, and then it automatically restarts after about 5 seconds and repeats (unless one launches BIOS configuration).  I assume something about the MBR has gotten messed up.  I tried booting off a USB thumb drive, but it just accessed the drive for a second or two, and then went back into the cycle (I tried every USB socket, and the BIOS was configured properly to boot off external USB, also, I was able to boot my computer from the USB)

I have no idea how to proceed if I can't even boot off of USB.  Oh, the computer is Asus Eee pc netbook (no CD drive).

Any advice at this point is greatly appreciated.

---

### Post by Muster Mark on 2011-07-09
FIXED!!

So, it turns out that simply putting 'removable dev' at the top of the boot sequence wasn't enough to get it to boot from the usb.  Had to put usb as the to HDD too, which surprised me.  Anyeay, after successfully booting from the USB it was a simple matter to re-install GRUB.  Everything went smoothly from there on.

---

### Post by Diametric on 2011-07-09
How do you set a USB as an HDD for a boot option - not trying to sound dense, but I've just never seen that in a bios option.  Interesting.

---

### Post by Muster Mark on 2011-07-09
Yeah, I'd never seen that before either,and took me an hour or so of poking around randomly to find.  Most bizarre.  It was just under the option to change the Boot Sequence was HDD configuration, and I set USB as HDD 1 from HDD 2 and it was able to boot (on my dell, the one time boot menu is so easy to use compared to this Asus/american megatrends mess).

---

### Post by Diametric on 2011-07-09
Good to know; thanks for the follow up post.  Glad you got it working!

---

