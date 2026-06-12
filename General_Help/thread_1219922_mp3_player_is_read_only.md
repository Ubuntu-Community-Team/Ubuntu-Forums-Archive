---
title: "mp3 player is read only"
date: 2009-07-22
forum: General Help
---

### Post by curiousnoob on 2009-07-22
I have a really cheap pixxo mp3 player.  It's been working fine for me until now.  
Normally I just plug it in and it appears on the desktop as a USB device.  I drag and drop my mp3s and everyone is happy.  
Now, though, when I plug it in the same USB device icon comes up but I can't put items on or delete them off.  It says the device is Read Only.  
Any ideas on how I can force it to let me put stuff back on?  I've done it a trillion times before.

---

### Post by khelben1979 on 2009-07-22
Have you tried to access the device with super user priviliges (root) ?

---

### Post by curiousnoob on 2009-07-22
> **khelben1979 said:**
> Have you tried to access the device with super user priviliges (root) ?

Ummmm.  I know how to do that but for all the other newbies reading this could you explain how to do that?

---

### Post by mbeach on 2009-07-22
Did it work for you?

I've helped a friend with a similar problem which turned out that the card in the player had was in locked mode (meaning the little phycisal slider was moved to the locked position). Does your player have a similar feature by any chance? Just a thought, although it may be obvious and seem silly to point out, but such things often go unchecked.

---

### Post by Sidewinder1 on 2009-07-22
If it's a permissions issue, you might try this, if you can ascertain the drive name that ubuntu is assigning to it. I know that Ext. Hard Disk Drives usually show up as /media/disk.
```
sudo chown -R curiousnoob:curiousnoob /media/disk
```
if curiousnoob is your login username. Input password when prompted.
Not sure that this'll solve your problem, but it's worth a try.
Strange that it worked before and suddenly stopped. Did you, perhaps, mount it in winbloze, and not go through the "safely remove hardware" routine? If so you could try that...

HTH,
Side

---

### Post by curiousnoob on 2009-07-22
I have tried it with hold switch on and off with no luck.  
I tried the above command to change permissions and it went through every file on the drive but was unable to change anything.  
I have never used it on windows. 
Really weird.  Don't know what is going on. 
How can I access it as root?

---

### Post by khelben1979 on 2009-07-22
> **curiousnoob said:**
> How can I access it as root?

Go to a text console ```
ctrl + alt + f1
``` or open up an xterm.

```
df -h
```
displays your devices.

Locate your device from the list and do what was suggested by SideWinder1.

---

### Post by curiousnoob on 2009-07-22
[QUOTE=
```
df -h
```
displays your devices.

Locate your device from the list and do what was suggested by SideWinder1.[/QUOTE]

The device is listed as /dev/sdb1 but after following the instructions nothing changes.  It is still read only.  
No error message, or any message, is given.

---

### Post by khelben1979 on 2009-07-22
Try this:
```

sudo mount -t vfat /dev/sdb1 /mnt/
```
it will mount the device and you will access it with full super user priviliges.

Does that help? ( You can then access the device by entering /mnt/ )

---

### Post by curiousnoob on 2009-07-22
> **khelben1979 said:**
> Try this:
```

sudo mount -t vfat /dev/sdb1 /mnt/
```
it will mount the device and you will access it with full super user priviliges.

Does that help? ( You can then access the device by entering /mnt/ )

This is what I get when I input that command: 
desktop:~$ sudo mount -t vfat /dev/sdb1 /mnt/
mount: /dev/sdb1 already mounted or /mnt/ busy

---

### Post by khelben1979 on 2009-07-22
On the desktop you should be able to unmount the mp3 player simply by pressing the right mouse button over the mounted device and choose unmount or..

```
umount [path to your mounted mp3 player]
```

Then go back to what I wrote before and try again.

---

### Post by curiousnoob on 2009-07-22
> **khelben1979 said:**
> On the desktop you should be able to unmount the mp3 player simply by pressing the right mouse button over the mounted device and choose unmount or..

```
umount [path to your mounted mp3 player]
```

Then go back to what I wrote before and try again.

I unmounted the device and then tried again.  This is what I got: 
-desktop:~$ sudo mount -t vfat /dev/sdb1 /mnt/
mount: special device /dev/sdb1 does not exist

---

### Post by khelben1979 on 2009-07-22
I would suggest that you reboot your Linux system and try again or wait for someone else to come up with something better.

---

### Post by curiousnoob on 2009-07-22
I'm not sure what is going on.  
After restarting the computer I still get the exact same messages:(

---

