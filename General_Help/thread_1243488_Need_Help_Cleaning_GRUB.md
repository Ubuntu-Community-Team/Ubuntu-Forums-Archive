---
title: "Need Help Cleaning GRUB"
date: 2009-08-18
forum: General Help
---

### Post by fiveacez on 2009-08-18
Back in June, I had to install Ubuntu a couple of times on my computer (was still learning about the partitioning process for a dual booted computer).   By the time I partitioned the disk space the way I wanted to, my GRUB screen when I turn on my computer gave me the option to boot with Ubuntu 2 times (regular & another mode twice), the memory test, and then Windows Vista.

I have been putting this off because it has just been a minor annoyance, but after the kernel update today, I now have the option to boot with Ubuntu **3 times** and Vista is further down the screen. It's way too messy and I need it cleaned up.

I want to clean up GRUB so I can have the options presented like this:

Ubuntu
Winows Vista
Ubuntu Mem Test
Windows Vista Memory Backup

Thanks in advance.

---

### Post by Tyke91 on 2009-08-18
edit /boot/grub/menu.lst with the text editor of your choice. Remember, you need to have root access to edit this file. 

scroll down to the bottom, you should see a table. 

remove the entries of the choices you don't want. save the file. 

done :)

PS: you probably want to keep the Ubuntu Recovery mode in your grub. just in case.

---

### Post by indytim on 2009-08-18
The easiest way is to edit the /boot/grub/menu.lst and comment out the extra options.  Of course back things up before embarking on the edit session.

IndyTim

---

### Post by mcduck on 2009-08-18
Actually the *easiest* way is to simply uninstall the old kernel versions with Synaptic, and they will disappear from the Grub menu automatically.

What comes to reordering the menu, that's going to be a bit of a problem. At least with the order you want.. You can arrange things in the menu, but you need to keep all Ubuntu-related options together and put other options either above or below them. This is because the Ubuntu options are generated automatically, and the section that contains them is also automatically rewritten during kernel updates. If you add any extra entries between the Ubuntu ones (or anywhere inside the section marked as "debian automagic kernels list" they will disappear during the next kernel update..

---

### Post by fiveacez on 2009-08-18
> **mcduck said:**
> Actually the *easiest* way is to simply uninstall the old kernel versions with Synaptic, and they will disappear from the Grub menu automatically.

Well, I already commented the text out, but how would I go about doing this through Synaptic?  Is this the same thing as the Package manager?

---

### Post by oldos2er on 2009-08-18
> **fiveacez said:**
> Well, I already commented the text out, but how would I go about doing this through Synaptic?  Is this the same thing as the Package manager?

 Yes, Synaptic is a package manager. Use 'Search' (not Quick search) to find **linux-image**, and it should show all the kernels you have installed. Mark any older ones you don't want for removal, then Apply. Your menu.lst will be automatically updated.

---

### Post by kuja on 2009-08-18
Actually, there's another way of doing it that doesn't involve removing the older kernels (you might want to keep them in case of emergencies and other problems that could happen later). I would edit /boot/grub/menu.lst and look for a line in the automagic configuration that says "howmany=all" and change it to "howmany=1". After doing that run "sudo update-grub" and you should have a slim menu.lst again.

---

### Post by mcduck on 2009-08-18
> **kuja said:**
> Actually, there's another way of doing it that doesn't involve removing the older kernels (you might want to keep them in case of emergencies and other problems that could happen later). I would edit /boot/grub/menu.lst and look for a line in the automagic configuration that says "howmany=all" and change it to "howmany=1". After doing that run "sudo update-grub" and you should have a slim menu.lst again.

On the other hand, even in the worst case you'd only ever need one older kernel available, the rest are just wasting your disk space. And once you have removed them from the Grub menu booting them is considerably harder. Besides, a Live-CD would do the trick just as well as the old kernel version would. Often even better.

I'm all for solving the real problems instead of curing the visible symptoms. ;)

edit: During the 6 months (minimum) you'll be using a certain Ubuntu version it's not unlikely that you'll get couple of gigabytes worth of kernels and kernel-related files.  While disk space is cheap, I still have better use for it than storing 6 old kernels I'll never use..

---

### Post by fiveacez on 2009-08-18
Can I put things before and after the Ubuntu boot options?

Also for moving boot options before the Ubuntu ones, do I place it after the line that says:
### BEGIN AUTOMAGIC KERNELS LIST

(Thanks for the help so far btw.)

---

### Post by kuja on 2009-08-18
> **fiveacez said:**
> Can I put things before and after the Ubuntu boot options?

Also for moving boot options before the Ubuntu ones, do I place it after the line that says:
### BEGIN AUTOMAGIC KERNELS LIST

(Thanks for the help so far btw.)
Before, not after.

---

### Post by fiveacez on 2009-08-19
So it's everything before or everything after?

---

### Post by mcduck on 2009-08-19
> **fiveacez said:**
> Can I put things before and after the Ubuntu boot options?

Also for moving boot options before the Ubuntu ones, do I place it after the line that says:
### BEGIN AUTOMAGIC KERNELS LIST

(Thanks for the help so far btw.)

Either before "### BEGIN AUTOMAGIC KERNELS LIST", or after "### END DEBIAN AUTOMAGIC KERNELS LIST".

As long as your extra entries are not between those lines.

---

### Post by kuja on 2009-08-19
> **fiveacez said:**
> So it's everything before or everything after?

The things you want to have showing up before Ubuntu go before.
The automagic section is autogenerated, so edit at your own peril, because you lose any manual changes there everytime update-grub happens. Things you want to have at the bottom of the list will go after the automagic section.

---

### Post by fiveacez on 2009-08-19
So if I understand you guys correctly,  GRUB will only change options for what's between the ### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST".  All the other boot options around it will be left alone, right?

---

### Post by mcduck on 2009-08-19
> **fiveacez said:**
> So if I understand you guys correctly,  GRUB will only change options for what's between the ### BEGIN AUTOMAGIC KERNELS LIST" and "### END DEBIAN AUTOMAGIC KERNELS LIST".  All the other boot options around it will be left alone, right?

Correct.

And to configure the settings inside the automagic section you'd change the settings in Default Options-section, in the beginning of the "automagic kernels list".

---

### Post by fiveacez on 2009-08-19
Ok, thanks guys!

---

### Post by raymondh on 2009-08-19
Have you tried startupmanager (GUI) to set defaults, parameters, etc to grub? 

You can set it to show only 1, 2 or 3 kernels.  You can also set it to default to a specific kernel or OS.  Etc.

SUM also writes to the menu.lst.

Just a .02-cent input.

---

### Post by fiveacez on 2009-08-19
Wow! That's pretty handy for quick editing.  I like the easy color changes to the text.  Thanks again.

---

### Post by mansell on 2009-09-26
After reading this post I tried Startup Manager. It saves the day. Simple and easy to use.
Thankx

---

