---
title: "Ubuntu 9.04 doesn't hibernate on acer aspire 6930"
date: 2009-07-30
forum: General Help
---

### Post by kireesign on 2009-07-30
Hi, I'm new to Ubuntu. I installed Ubuntu 9.04 on my laptop. It works fine but Hibernate is not working. I followed different threads and solutions on internet (eg. creating SWAP, getting the right UUID for the SWAP partition in my fstab file, etc). My system is going into sleep but when waking up (the bootscreen is saying: 'waking up' (that's a step forward after trying different solutions)), my system hangs.

I know there are many threads about Hibernate but I can't find the right solution. 
Hope you can help me.

Some additional information about my system
Laptop Acer Aspire 6930.
Ubuntu 9.04
Memory 4 Gb. SWAP partition is about 12 Gb. SWAP is turned on. Can see this via Gparted and the graphicstab from my systemmonitor.

Log from the debug section in systemlog (latest try to Hibernate):
Jul 30 12:12:12 Rohan kernel: [    8.240913] PM: Resume from partition 8:22
Jul 30 12:12:12 Rohan kernel: [    8.240914] PM: Checking hibernation image.
Jul 30 12:12:12 Rohan kernel: [    8.241193] PM: Resume from disk failed.

---

### Post by prshah on 2009-07-30
> **kireesign said:**
> 
Jul 30 12:12:12 Rohan kernel: [    8.241193] PM: Resume from disk failed.

Check if the resume parameter in the menu.lst is correct (should point to your swap partition). Open a terminal (Applications-Accessories-Terminal) and give the command```
cat /boot/grub/menu.lst | grep -i resume
```

Compare this to your swap partition id in ```
sudo fdisk -l
```

And a small unrelated piece of advice: 12GB is too much swap; 4.4GB is OK at most, since you are using hibernate.

---

### Post by kireesign on 2009-07-30
the parameter in menu.lst was /dev/hda5.

Changed it into
## e.g. defoptions=vga=791 resume=/dev/sdb6
# resume=/dev/sdb6

according to the output of sudo fdisk -l
/dev/sdb6            6080        7609    12289662   82  Linux wisselgeheugen

(Linux wisselgeheugen = swap. Dutch version)

It still doesn't work...

---

### Post by prshah on 2009-07-30
> **kireesign said:**
> 
## e.g. defoptions=vga=791 resume=/dev/sdb6
# resume=/dev/sdb6

/dev/sdb6            6080        7609    12289662   82  Linux wisselgeheugen


The lines are commented out. You have to uncomment them. HOWEVER:

The defoptions line SHOULD begin with a #; (it's commented out because it contains 2 #'s.)

The resume parameter has to be passed as a kernel option. 

So, make any ONE of these changes```

# either (Note the leading # in the next line, only ONE hash)
# defoptions=quiet splash resume=/dev/sdb6
# _or_ add it to the end of the kernel options; note no # (hash) in the beginning
kernel          /boot/vmlinuz-2.6.27-14-generic root=UUID=4bck0fu6-lf3b-43dc-bd3c-9a3c9b0d4evd \
   ro quiet splash [color=red]resume=/dev/sdb6[/color]
```

You may need to run ```
sudo update-grub
``` for the changes to take effect. Back up your original file before making changes / update-grub```
sudo cp -p /boot/grub/menu.lst /root
```

The kernel line is broken into two for display purpose only; in your menu.lst, keep everything on one line.

---

### Post by kireesign on 2009-07-30
I Choose the first option. After updating my menu.lst looks like:
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash resume=/dev/sdb6
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=de705ba9-fbbc-49f0-b060-7e82d1640d01 ro quiet splash resume=/dev/sdb6 
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=de705ba9-fbbc-49f0-b060-7e82d1640d01 ro quiet splash resume=/dev/sdb6 
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=de705ba9-fbbc-49f0-b060-7e82d1640d01 ro quiet splash resume=/dev/sdb6 

But the system isn't fully awake.
When waking up, I don't have a screen with 'Ubuntu. Waking up, please wait' anymore.
Now its a screen with 2 lines and a blinking cursor (it says starting up)

After a while my laptopscreen blinks and then nothing. Only a blank screen (no blinking cursor anymore). 

Maybe a problem with my videocarddriver?

---

### Post by prshah on 2009-07-30
> **kireesign said:**
> 
Maybe a problem with my videocarddriver?

Have you tried pressing a few keys or moving the mouse? Maybe it's the screensaver?

Or press Ctrl+Alt+F1 (F2,F3..F6); any display? (You should get a text login prompt.)

Can you check / post your suspend log?```
tail /var/log/pm-suspend.log
```

---

### Post by frt975 on 2009-07-30
You probably installed it in windows, which does not allow hibernation. Reinstall by putting your CD in the disk drive, going to start menu>restart. At the first thing you see press f2. Use the arrow keys to navigate to something like startup order make your CD drive the first item in the list. save and exit. Install Ubuntu.

---

### Post by kireesign on 2009-07-30
It isn't the screensaver. Tryed different displays. 
Also can't use Numlock or Capslock so it looks like a sort of freeze.

Ouput pm-suspend.log:
                    Extra: Last beacon: 1576ms ago

success.
/usr/lib/pm-utils/sleep.d/01PulseAudio thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00powersave thaw hibernate: sudo: no passwd entry for 1000!
sudo: no passwd entry for 1000!
success.
/usr/lib/pm-utils/sleep.d/00logging thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/00auto-quirk thaw hibernate: success.
/usr/lib/pm-utils/sleep.d/000record thaw hibernate: success.


@frt975, Windows is on my laptop but on disk 1. Disk 2 is dedicated for Ubuntu. Including swap partition.

---

### Post by frt975 on 2009-07-30
> **kireesign said:**
> It isn't the screensaver. Tryed different displays. 
@frt975, Windows is on my laptop but on disk 1. Disk 2 is dedicated for Ubuntu. Including swap partition.
Did you install like this?

---

### Post by kireesign on 2009-07-30
Nope,
downloaded an .iso file from ubuntu ([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)) and created a CD. Then I rebooted my laptop from CD and installed Ubuntu from CD on Disk 2.

---

### Post by frt975 on 2009-07-30
> **kireesign said:**
> Nope,
downloaded an .iso file from ubuntu ([http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)) and created a CD. Then I rebooted my laptop from CD and installed Ubuntu from CD on Disk 2.
Never mind, it wasn't the problem I was thinking of.

---

