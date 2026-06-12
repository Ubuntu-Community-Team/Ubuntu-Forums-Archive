---
title: "External Hard Drive Not Recognized"
date: 2010-02-01
forum: General Help
---

### Post by hockeyfreak186 on 2010-02-01
Hello, im new to linux and have just intalled 9.10 and have been setting things up on it when i came across a problem.  I have a WD external hard drive that when i plug into my linux machine does nothing.  It works fine on my XP laptop however.  I have tried it in different slots with different cords and nothing seems to work.
I also typed in lsusb and it didnt seem to recognize it
When i typed in dmesg it looked like it would connect, get an address then disconnect and it would repeat over and over.

Any help would be greatly appreciated thanks!:)

---

### Post by M1GEO on 2010-02-01
open a new terminal and run
```
tail -f /var/log/messages
```

This does the same as dmesg, but in a more real-time way.  With the terminal in view, plug the USB hard disk in.  You will be able to see what is going on.

Do you notice a "device node" mentioned.  It will probably be something in the nature of sdb, sdc, sdd or something like that?

George

---

### Post by hockeyfreak186 on 2010-02-01
Feb  1 20:38:54 hockeyfreak186-desktop kernel: [  505.344109] usb 2-1: USB disconnect, address 59
Feb  1 20:38:55 hockeyfreak186-desktop kernel: [  506.576394] usb 2-1: new full speed USB device using uhci_hcd and address 60
Feb  1 20:38:55 hockeyfreak186-desktop kernel: [  506.724510] usb 2-1: configuration #1 chosen from 1 choice
Feb  1 20:38:56 hockeyfreak186-desktop kernel: [  507.080131] usb 2-1: USB disconnect, address 60
Feb  1 20:38:57 hockeyfreak186-desktop kernel: [  508.064098] usb 2-1: new full speed USB device using uhci_hcd and address 61
Feb  1 20:38:57 hockeyfreak186-desktop kernel: [  508.206730] usb 2-1: configuration #1 chosen from 1 choice
Feb  1 20:38:57 hockeyfreak186-desktop kernel: [  508.568094] usb 2-1: USB disconnect, address 61

and it keeps going and going :-P
Im guessing this is not normal

---

### Post by M1GEO on 2010-02-01
No.  That is *not* normal.

Firstly, I suggest that you connect the hard disk to one of the usb ports on the back of the motherboard, towards the top - These are full power ports.  First thing that I thought of is that as the drive spins up, it cant get enough power (typical of hubs, etc).  Also, if you have the option with your drive, to externally power it, do so.

---

### Post by dcast on 2010-02-01
If it works in Windows XP, then maybe it is NTFS formatted? Try installing ntfs-3g and see if that works.

---

### Post by hockeyfreak186 on 2010-02-01
I did this and it still does the same thing; connecting then disconnecting over and over :-(

would 'sudo modprobe -r uhci_hcd' do anthing?  I just found another post that said that might work but i dont know if that would be bad to do.

---

### Post by buddyd16 on 2010-02-01
If you still have a windows computer or partition connect the drive using windows and then either safely remove the drive by right clicking the safely remove hardware icon or leave the hard drive plugged in and shutdown the computer via windows start menu. This is what solved this issue for me, I assumed it had something to do with how ntfs handles journaling.

---

### Post by hockeyfreak186 on 2010-02-01
I had tried safely removing it, but i went back and shutdown my windows xp laptop with it connected, then pluged it back into my linux machine and still wont work, it just does the connecting and disconnecting thing again and again

---

### Post by hockeyfreak186 on 2010-02-01
i also tried installing ntfs-3g earlier and i just reinstalled it with still no success

---

### Post by MsTran2010 on 2010-02-01
Thanks for the information! I've been meaning to start this process myself so this is a big help. :popcorn:

---

### Post by M1GEO on 2010-02-01
```
sudo modprobe -r uhci_hcd
``` will remove the uhci_hcd driver from the kernel.  It is the USB Universal Host Controller Interface driver.

I dont suspect its a filesystem problem, because the device never gets a device node.  Sounds like a hardware problem, like power.  Does the drive spin up okay, as that rules that out.  I can't think of what else it could be.

Does the drive pass a filesystem check under Windows?

---

### Post by hockeyfreak186 on 2010-02-01
The drive light does turn on, but i cant hear it spinning like it does on the windows xp computer, it just makes a clicking noise instead.  I also cant get this to work on my windows 7 desktop if that helps any lol

and how do i do a filesystem check?

---

### Post by M1GEO on 2010-02-01
The clicking noise diagnoses the problem.  Im pretty sure that its the power then.  The controller negotiates with the computer, and as soon as the drive goes to start up, it draws too much power and so is cut.  And the clicking is the drive keeping to try spinning...  I have had this many times.

I suggest you plug the USB drive directly into the computer itself (not via hubs, etc).  Also, use a connector on the motherboard.  But yeah.  Not enough power.

---

### Post by hockeyfreak186 on 2010-02-01
it is a small passport external hard drive that needs a usb cord to connect it, and there is no option for external power, so how do i go about this if i have already tried the motherboard usbs?  I have also tried powering it with 2 usbs from the motherboard powering it and still the same problem

---

### Post by M1GEO on 2010-02-01
Now thats a different question, haha. It will probably require some swapping about of peripherals.  The hard disk will require a lot of power, so group it with things which wont, for example printers/scanners (as they are separately powered).  Things which are bus powered (i.e. keyboard/mouse) will all draw power, and the computer tries to manage it.

About the best method, is to swap cables around until you hear the drive spin up.  I would defiantly recommend using the two USB connectors if possible.  Plug the non data connector in first, so the drive can spin before the computer can say no?

I had a similar problem with my USB Wireless Lan card.  All sorts of weird problems when it didnt get enough power.  I've had it with HDD's too.

---

### Post by hockeyfreak186 on 2010-02-01
ill mess around with it and see what happens, thanks for the advice tho!

---

### Post by M1GEO on 2010-02-01
No problems :)

---

