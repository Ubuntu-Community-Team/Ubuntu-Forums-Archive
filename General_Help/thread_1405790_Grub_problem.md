---
title: "Grub problem"
date: 2010-02-13
forum: General Help
---

### Post by frank cox on 2010-02-13
Solved1

Could someone help me get my 9.04 install working? I have read and tried everything I could but I just don't seem to get it. I had to reinstall XP .
TIA

---

### Post by lenoirrichelieu on 2010-02-13
I am impressed about how you partitioned the hdd :D
 
But anyway tell what is the problem? I mean where you installed Ubuntu, what stage of grub is not working etc.

---

### Post by lindsay7 on 2010-02-13
How to restore the Ubuntu grub bootloader

First of all, all credit for this part of the tutorial goes to catlet.   

So, lets begin. To restore the grub, you must boot off the ubuntu live cd, the one you installed this system with. 

Once there, open a terminal (Applications>Accessories>Terminal) and type this:
Code:
sudo grub
Next, you need to find which hard drive ubuntu and the grub is installed to. You do this by running this command:
Code:
find /boot/grub/stage1
Take note of what it returns (something like (hd0,1).)

Now you need to tell Grub where it is installed. Using the output of the last command, change this one and run it:
Code:
root (hd<a>,<b>)
Replacing <a> and <b> with what you got back before. For example, if "find /boot/grub/stage1" gave me "(hd0,1)", you would run "root (hd0,1)"

Ok, so thats the configuration over and done with. Now we just need to run one command to install the Grub to your hard drive:
Code:
setup (hd0)
Now to quit and check if it has worked:
Code:
quit
Code:
sudo reboot
Make sure you have taken the live cd out of your disc tray. All going well, you should start back up and see the grub once again.

---

### Post by audiomick on 2010-02-13
> **lindsay7 said:**
> To restore the grub, you must boot off the ubuntu live cd.[COLOR=Red] Any ubuntu live cd will do.[/COLOR]

That needs to be qualified. If you want to stick with grub legacy, it needs to be 9.04 or older. If you use a 9.10 CD, you will get grub2, and those instructions may not work. There are some fundamental differences between the two, principally that grub 2 doesn't use the menu.lst file anymore.

I would suggest sticking with the 9.04 live CD if that is the Ubuntu you have installed. I have a feeling that this would lead to a "neater" result, but it is just a feeling.

---

### Post by lindsay7 on 2010-02-13
That is correct. These are part of instructions that cover both systems.  The op has the old grub and needs to use the correct install disk. I will edit that line to make it clear.  Thanks for pointing it out.

---

### Post by frank cox on 2010-02-13
Thank you Lindsay, thank you  catlet.!

That was simple. I could make no sense of the instructions in the manual.

---

### Post by lindsay7 on 2010-02-14
Good for you. Happy this worked out so well.

---

### Post by frank cox on 2010-02-14
> **lindsay7 said:**
> Good for you. Happy this worked out so well.

Thanks again! I will save the instructions.
Wish you and catlet had written the manual!

---

