---
title: "Change Order of Boot Options in Grub 2"
date: 2009-11-17
forum: General Help
---

### Post by Ubuntist on 2009-11-17
I'd like to change the order in which the boot options appear on my dual-boot system so that 1) XP comes first and the latest Ubuntu kernel is second, but 2) Ubuntu is the default.

Under the old Grub, I could edit menu.lst accordingly.  I have found an extensive [discussion of how to customize Grub 2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=change+kernel+order+grub"), but it kind of blows my mind; I'm just a naive, non-technical Ubuntu enthusiast.

Could someone please give me a pointer or two?

---

### Post by oldfred on 2009-11-18
You can do it several ways. One make a copy of 30_osprober  as 06_osprober as all the files are processed in the order and any executable file with 2 digits and an underscorce will be processed. Then you have to turn off the 30_prober. Or you can copy 40_custom to 06_custom and copy your windows entry into that file. You still  have to turn the prober off or you will get duplicate entries. After all changes you rerun the update.

cd /etc/grub.d
sudo cp 40_custom  06_custom
[FONT=Bitstream Vera Sans Mono]sudo chmod 755 /etc/grub.d/06_custom[/FONT]

copy your windows entry from [FONT=Bitstream Vera Sans Mono]/boot/grub/grub.cfg into 06_custom

[/FONT]gksudo gedit 06_custom

gksudo gedit /etc/default/grub
add
GRUB_DISABLE_OS_PROBER="true"
Change to 1 or 2 for your ubuntu line
[FONT=Bitstream Vera Sans Mono][GRUB_DEFAULT]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Configuration%20File%20Commands.html#GRUB_DEFAULT")=0   [/FONT]

After all updates
sudo update-grub

More info from Herman:
[http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20Configuration%20File%20Commands.html)

---

### Post by dcstar on 2009-11-18
> **Ubuntist said:**
> I'd like to change the order in which the boot options appear on my dual-boot system so that 1) XP comes first and the latest Ubuntu kernel is second, but 2) Ubuntu is the default.

Under the old Grub, I could edit menu.lst accordingly.  I have found an extensive [discussion of how to customize Grub 2]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=change+kernel+order+grub"), but it kind of blows my mind; I'm just a naive, non-technical Ubuntu enthusiast.

Could someone please give me a pointer or two?

You could do all of what is listed in the other post, or you could just install the old Grub package and get back the previous - easily editable - way of doing things (but look at a HOWTO first!).

---

### Post by wilee-nilee on 2009-11-18
I use startup manager it is in synaptic. Experienced users have suggested that it isn't stable for grub2 but I have had no problems, right before the rc release it was causing a downgrade to legacy grub if installed but that was fixed in less than a week. I suspect that if it wasn't stable it wouldn't be in synaptic, but it may be that it is only there if you open all the repositories I don't know, it works for me.

---

### Post by herdivet on 2009-11-18
OK, I'm lazy, I'll admit it.  That looks like a LOT more work than the old method for editing GRUB's menu.lst.

I found a quicker, maybe not better, way to do this.

Edit /etc/default/grub 

change the line:

GRUB_DEFAULT=0
to 
GRUB_DEFAULT=x  where x is the number of the OS you want to have boot by default.  You can count down from the GRUB menu on bootup - include the Recovery Mode entries and the Memory Test entries.

When finished editing, run 'sudo update-grub'.  

It worked great for me (Ubuntu 9.10) - your mileage may vary.


Bill

---

### Post by Ubuntist on 2009-11-20
Thanks, everybody.  I decided to do it the "official" as described by oldfred, in the hope that I'd learn something about Grub 2 and that the changes I made would be stable against future upgrades, etc.  Anyway, I got it to work although I kept forgetting to update-grub.

---

### Post by oldfred on 2009-11-20
Just a question. I know it looked like a lot of changes as I posted it, but it seemed to work. Was it all that difficult in hindsight?

Yes, you have to open/edit several files instead of just menu.lst, but if you corrupted menu.lst you could not boot. I also am learning grub2 but have started to like it for some of its new features, which of course adds complexity.

---

### Post by Ubuntist on 2009-11-30
I think what makes the new Grub more complicated from my point of view is that it will probably be more difficult to remember what to do next time I need to do this.  I only mess with Grub once in a great while.  Under the old Grub, if I could just remember which file I had to edit, then I could figure it out from there, just by seeing the structure of the file and from the comments I left in it. With the new Grub, remembering a file name isn't going to be enough.  I suppose I could have left comments for myself in the first file to be edited.  I can easily see, though, that the new Grub is superior if you use it frequently.

---

### Post by herdivet on 2010-08-24
OK, I now want to post what I think is the absolutely easiest (maybe laziest) and most foolproof way to do this.  It's all GUI, no command prompt required, no editing necessary.

Click Applications
Click Ubuntu Software Center
Search for Startup Manager
Install Startup Manager
Close Ubuntu Software Center

Click System | Administration
Click Startup Manager
In 'Default Operating System' click the drop down and choose whatever you want to have as the default.
Click Close

You can also change other startup parameters here, all in a simple GUI format.  Extremely simple.

---

### Post by avstudio1 on 2010-10-06
> **herdivet said:**
> OK, I now want to post what I think is the absolutely easiest (maybe laziest) and most foolproof way to do this.  It's all GUI, no command prompt required, no editing necessary.

Click Applications
Click Ubuntu Software Center
Search for Startup Manager
Install Startup Manager
Close Ubuntu Software Center

Click System | Administration
Click Startup Manager
In 'Default Operating System' click the drop down and choose whatever you want to have as the default.
Click Close

You can also change other startup parameters here, all in a simple GUI format.  Extremely simple.


This is the way it should be, thanks!

---

### Post by Mark Phelps on 2010-10-06
The problem with editing the Default number in the config file is that, every time you do a kernel update, the number of entries in the GRUB menu changes.

That's OK if you always want the first entry to be the default.

But, given the sequence by which the GRUB menu entries are built, OSs found with OS prober are always added to the menu AFTER the Ubuntu kernel entries.

This means you have to either keep up removing old kernel entries or you have to keep manually updating the config file.

---

### Post by rcbinwi on 2010-10-19
I think I had a similar problem.  In my old grub I had the first Linux kernel, then XP, then all the rest.  This is the order of usefulness for me.  I want Linux to remain the default.

Is there any way to accomplish this with grub 2?

---

### Post by herdivet on 2010-10-19
Normally Linux is the default, if it's not on your system, try this:

Click Applications
Click Ubuntu Software Center
Search for Startup Manager
Install Startup Manager
Close Ubuntu Software Center

Click System | Administration
Click Startup Manager
In 'Default Operating System' click the drop down and choose whatever you want to have as the default.
Click Close

It's all GUI.  Very easy and should allow you to pick Linux as your default.

Hope that helps.

<Your mileage may vary.>

---

### Post by rcbinwi on 2010-10-19
Thank you herdivet.

Actually, though, my problem is a little different.  Linux is my default, and I want it to remain that way.  On the GRUB 2 list, though, I want XP to come next.  I don't like scrolling all the way past stuff I barely ever use to get to XP.

Do you know how to reorder items?

Thanks.

---

### Post by herdivet on 2010-10-19
I have seen, but don't remember where, how to remove old kernel releases so the list is not that long, but I do not know how to reorder so you have Linux with XP directly below it.

I'm sure there's a way, but I don't know what it is.  If I find it, I'll get back to you with it.  Someone else probably knows off the top of their head and hopefully will reply soon.

<Your mileage may vary>

---

