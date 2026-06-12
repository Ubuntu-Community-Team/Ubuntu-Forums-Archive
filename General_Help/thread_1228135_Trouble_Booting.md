---
title: "Trouble Booting"
date: 2009-07-31
forum: General Help
---

### Post by Darth_Canadius on 2009-07-31
I'm trying to install Ubuntu on a friend's computer. I've done it on my laptop, and a different friend's laptop, so I get how to install it. lol. 

The current computer I'm working on is a HP Pavilion 525w, it's a desktop and it appears as though there should be no issues, since I can't find any threads on it. 
However, after install, I reboot, the splash screen doesn't show up, then the login screen appears, and after logging in, the computer freezes.  :confused: 

Before the install, I wiped the hard drive clean, so there was nothing on it to interfere. 
I'm all out of ideas  ](*,), so if any one can help, that'd be really great of you. 

Thanks in advance, 
Nathaniel

---

### Post by merlinus on 2009-07-31
You might post system specs.

---

### Post by michy99 on 2009-07-31
Did you run a check on the cd to make sure it was okay?

---

### Post by egalvan on 2009-07-31
+1 for checking the install CD integrity.
+1 for posting the specs


> **Darth_Canadius said:**
> 
Before the install, I wiped the hard drive clean, so there was nothing on it to interfere. 


My question...

HOW did you "*wipe the hard drive clean*"?

Not all methods leave a truly clean drive, although this is probably not the problem.

I'm thinking video problems.

Anyway,
After checking the CD integrity, try running  the memory check for at least one full cycle.

Check the HP website for any BIOS updates.

And don't forget to post that info they asked for...
help us help you.

---

### Post by Darth_Canadius on 2009-07-31
:redface:

Excellent point. 
Motherboard: Intel D845GRG
CPU: Intel Celeron 2.00 GHz
RAM: 384 MB DDR
the Graphics card and ethernet are both integrated and unclaimed.
anything else you need, let me know.

Thanks again!

---

### Post by Darth_Canadius on 2009-07-31
Yes, the cd is ok.
I used the "shred" command because I can get it to run in recovery mode, and I put it into the root shell.

---

### Post by merlinus on 2009-07-31
IIRC, 384M RAM is the least amount required to install via the live cd.  If video memory is shared, then you do not have enough.

In that case, try the text-based alternate install cd.

---

### Post by Darth_Canadius on 2009-07-31
how do I do that?

---

### Post by merlinus on 2009-07-31
You will have to d/l the .iso from the ubuntu webpage.  Make sure to select the alternate install cd.

---

### Post by Darth_Canadius on 2009-07-31
ok, thanks for the help! I'll try that now.

---

### Post by oldfred on 2009-07-31
I agree with egalvan that it probably a graphics problem with the intel internal graphics. I think your machine has 512 and they deduct the shared graphics memory to give you 384.

If you got past the Ubuntu login and it hangs you should try hitting CTRL-ALT-F1 to see if you can get to a command line. You can also edit grub to boot to run level 1 or a command line. If either of these work then this site has instructions on updating the intel graphics: 
[http://www.red91.com/2009/05/08/intel-270-driver-on-ubuntutp://]("hthttp://www.red91.com/2009/05/08/intel-270-driver-on-ubuntutp://")

Also check chipset with:
lspci -nn|grep VGA

---

### Post by Darth_Canadius on 2009-08-01
No, It does not have 512, I checked the actual chips, and one is labeled 128MB and he other is 256 MB. 

In any case, the Alternate Install CD worked flawlessly, and the Desktop is now running beautifully. Thanks for all the input and replying so quickly.

---

### Post by merlinus on 2009-08-01
Very glad to hear you got it working!  Have fun...

---

### Post by egalvan on 2009-08-03
> **Darth_Canadius said:**
> No, It does not have 512,
 I checked the actual chips, and **one is labeled 128MB **and he other is 256 MB. 

In any case, the Alternate Install CD worked flawlessly
 and the Desktop is now running beautifully.
 Thanks for all the input and replying so quickly.

Hey, great to hear that you are now Ubuntu'ing to your heart's content. :)

The alternate install CD basically uses much less graphics-oriented tools to install Ubuntu, 
which usually results in by-passing video problems during the install phase.
So it probably WAS a video problem. :)

And lastly, see if you can find another 256M chip for your machine.
It will show a good increase in responsiveness.

Of course, a pair of 512M would be fantastic, but may not be as readily available as 256M

Take the chip out and go to a "mom-and-pop" type local computer shop,
they may have some they are "going to throw away".
Local computer clubs are also a good source.
Even better, try to find a Linux User Group, known as LUGs, 
in your area.

go to 
[http://www.linux.org/groups/](http://www.linux.org/groups/)

and search for one close enough to you.

Again, congratulations on the install.
Happy Linux

ErnestG

---

