---
title: "Unable to boot after hibernate"
date: 2009-12-30
forum: General Help
---

### Post by mkhurramali on 2009-12-30
When I put my laptop to hibernate today, it gave three lines of errors. I did not really pay attention to what they were. 

When I came home and switched on my laptop a blank screen came up. I did a hard shut down. Now when I boot, I get some error messages:

ata1.00: ...exception EMASK...
...
ata1.00: status ... {DRDY}
...
ata1.00: error .... {ERNY}
...
kinit: trying to resume from (/dev/disk/by-uuid/{some number}  
kinit: No resume image, doing normal boot...
mount: mounting /dev/disk/by-uuid/{some number} on /root
failed: Invalid argument
mount: mounting /dev on /root/dev failed: No such file or directory

And then I get the BusyBox console

What to do?

---

### Post by Red_Acid on 2009-12-31
> When I put my laptop to hibernate today, it gave three lines of errors. I did not really pay attention to what they were. 
Just like what happened to me. But unlike you, I can't see any error. :???:

Only last Monday I had the opportunity to install Karmic (a lot of work to do lately), and besides all the differences it has to Jaunty, everything was running smoothly and I was happy with my system. I thought all was going fine, until 2 hours ago.

I was working on a University project (Computer Vision), and had a lot of files opened. I didn't wanted to close all the files, so once I turned on the PC, I would get instantly back to work, then I used the hibernate option. Really really bad move.

Once I booted up, the screen got stuck in the USplash screen. I waited for about 10 minutes, and nothing happened. Tried using the "Ctrl+Alt+Fx" to see if I could go to a console mode, to see what was happening, but it continued stucked on the USplash. So, had to do a hard shutdown. Booted up again, and still the same, tried the recovery mode, and still the same USplash screen... Nothing!

Then, put the LiveCD and searched on Google a way to clean up this mess, but I've found nothing.

Here I am.

**I can access to my partition with the LiveCD, and see all the files. So, is there a way of remove the hibernation files (or something like that), so that the system boots normally and don't wait for that files? Or something that solve this?**

I just don't want to have to install all the system again (and all the customization I usually do). It really sucks. I just did that on Monday. :(

---

### Post by Red_Acid on 2010-01-02
I'm sorry for the bump, but no one can help us? :confused:

---

### Post by john newbuntu on 2010-01-02
Are you at least able to get to the grub menu?  If so hit escape immediately and follow instructions 1 through 7 on this page (In step 3, hit 'e' on the line starting with Ubuntu). In step 6, you just need to append the word "S" without quotes:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Once you get a prompt, login as root and try typing "sudo init 2" without quotes.

---

### Post by Red_Acid on 2010-01-02
Man... YOU MADE MY DAY! I'm writing from my Ubuntu right now. Many thanks for that! I totally was unaware of that option. If I could buy you a beer, I would do it right now. :mrgreen:

One last thing: because I'm using Karmic, and it comes with GRUB2, I followed the instruction 11 in the **[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")**. But if it wasn't for you, I would be doomed.

---

### Post by eisbaar on 2010-01-08
I have the same problem, only I can't even access the boot-loader, i only get a blank screen and a restart if i try typing enter for a few times... I'm going really nervous, can anyone help?

---

### Post by Red_Acid on 2010-01-08
Can you access the boot menu? The one where you choose which is the drive to boot?

If so, use a LiveCD and reinstall GRUB2. You can follow this instructions: **[Grub2 - Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")**

If not, I can't help you, since I'm not aware of what could be happening.

---

### Post by eisbaar on 2010-01-08
NO, when I start the computer I get absolutely nothing except the blank screen and a few restarts... I guess it gotten into some kind of a dead-loop...

---

### Post by Red_Acid on 2010-01-08
Man, I'm sorry to tell you, but that should definitely be hardware related.

The same thing happened to me last year, in April. I normally shutdown the computer one day, the next day the exact same thing that is happening to you, happened to me.

In my case, it was the motherboard that suddenly died. My luck was that the PC was still in the guarantee.

I hope that yours is still in the guarantee.

---

### Post by eisbaar on 2010-01-08
it is. thank you, I'll get it to service :(

---

### Post by michaelg81 on 2010-08-11
> **john newbuntu said:**
> Are you at least able to get to the grub menu?  If so hit escape immediately and follow instructions 1 through 7 on this page (In step 3, hit 'e' on the line starting with Ubuntu). In step 6, you just need to append the word "S" without quotes:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

Once you get a prompt, login as root and try typing "sudo init 2" without quotes.

I, too, am unable to boot after hibernating my machine (Ubuntu 9.10). However, my GRUB entry looks different than the one in the solution you suggested here:

    [http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)
    
Rather than proceed blindly, I thought I'd get some advice specific to my situation. Here's my GRUB entry, after having already attempted to edit it per another forum post. The first four lines are exactly as they were before I removed them (I made note of them before deleting them). These four lines reappeared after my editing attempt. So the remaining lines might not be exactly what I had on the initial failure. I seem to remember that all disk references were by uuid.#
 ```

	recordfail=1
	if [-n ${have-grubenv}]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)  #note: this may have been set to the UUID String#
	search --no floppy  --fs-uuid --set <uuidString>
	linux boot/vmlinuz-2.6.31-9-rt root=UUID=<uuidString> ro   quiet splash
	initrd /boot/initrd.img-2.6.31-9-rt
```
	
Here's my unsuccessful editing attempt:
```

	set root=(hd0,5)
	search --no floppy -fs-uuid --set /dev/<myLinuxVol>
	linux boot/vmlinuz-2.6.31-9-rt root=/dev/<myLinuxVol> ro   quiet no splash
	initrd /boot/initrd.img-2.6.31-9-rt
```

Before I really mess something up, I thought I'd ask for help. 
!!! NOOB ALERT !!!
Please be detailed and explicit, giving the exact syntax for each command, which programs (e.g., shell) to use, and how to launch those programs, if I need to be root, etc., etc.

Thanks a bunch. Ubuntu and its community really rocks. I'd never get Linux running if it hadn't been for you guys (and gals).

Michael

---

