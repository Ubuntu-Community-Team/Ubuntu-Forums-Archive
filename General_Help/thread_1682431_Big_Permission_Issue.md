---
title: "Big Permission Issue"
date: 2011-02-05
forum: General Help
---

### Post by Sr4d on 2011-02-05
Hi all, I'll get right too it..

I was playing around with aircrack-ng and all of the goodies, all of a sudden I was getting errors saying it couldn't open or write to files anymore because my hard drive was set to read only.

Obviously, I did not set it that way. A few days back I was reading that the ext4 filesystem does this when ever it detects errors. So, I rebooted, sure enough, errors. I press F, it then fixed the errors and rebooted, or so I thought.

Upon checking to see if all of the permissions got put back to normal, I found that "root" still owned nearly every directory in my computer. I tried chown and chmod to set everything back to normal, but to no avail.

I am getting frustrated by this. This happened once before the same way and I couldn't figure it out so I just reinstalled. I can't keep reinstalling every time I want to use aircrack so I need to find a solution to this.

Has this happened to anyone else before? Does anyone have any solutions for me?

Thanks for reading.

---

### Post by Sr4d on 2011-02-06
Bump.
 
Anyone? :/

---

### Post by asmoore82 on 2011-02-06
> **Sr4d said:**
> I found that "root" still owned nearly every directory in my computer.
Did you mean in your home folder, or literally on the whole computer?
root *should* own most of the system files outside of your home.

If your ext filesystem really is kicking to read-only unexpectedly,
it sounds like a failing hard drive to me.

You can test it from a LiveCD with: ```
sudo badblocks -sv /dev/sda
```

---

### Post by Sr4d on 2011-02-06
Ty for the reply!
 
I agree that root should own most of the files for security reasons, however; every folder is set to read only, and only root can read from it. I can't do anything.
 
Sudoing and trying it changes nothing, the permissions will not change with the gui nor with terminal.
 
The first time I had this issue I was on a standard rotary hard drive, so I figured the second time around I would try on my ssd to see if anything would change. I got aircrack all set up, started using it to inject, ect, and then out of know where, the drive changed itself to read only.
 
The ssd is brand new so I know it's not failing, but idk whats going on.
 
Is there anything else you can suggest? I'll be willing to try anything, but I know the drives aren't bad.
 
Edit: Also, I am on 10.10, if that matters. Thanks again.

---

