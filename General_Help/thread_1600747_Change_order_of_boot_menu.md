---
title: "Change order of boot menu"
date: 2010-10-19
forum: General Help
---

### Post by JonnyOSullivan on 2010-10-19
Hi, I've done some searching, and I cant find how to change the order of GRUB. I found someone who asked in '06 but I believe the method has changed. I want windows (The bottom on the list) to start without me having to select it. Thanks :)

---

### Post by Hippytaff on 2010-10-19
This should help - [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by JonnyOSullivan on 2010-10-19
> **Hippytaff said:**
> This should help - [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Sorry, but I cant find any way to change the order on that page...

---

### Post by chessnerd on 2010-10-19
I'm actually not sure if you can change the actual order. You can set which menu item is the default under /etc/default/grub and then it will start on that menu item (they start numbering from 0). However, after a kernel update, you'll need to either remove an older kernel version or change the number again.

There has to be a way to do it. If you find a way, let me know because I would be interested in it. I'll look around a bit more.

---

### Post by yetiman64 on 2010-10-19
> **JonnyOSullivan said:**
> Hi, I've done some searching, and I cant find how to change the order of GRUB. I found someone who asked in '06 but I believe the method has changed. I want windows (The bottom on the list) to start without me having to select it. Thanks :)

I believe the program Startup manager available in the repos can be used to set the default OS. Though I don't actually use it here. Have a look around for it. 

If it is no good to you, you can edit the file /etc/default/grub as root and alter the line,
> GRUB_DEFAULT= to the line number (note, counting the lines starts at 0) of Windows in the menu. It may be possible to use the exact title of the current windows entry in grub instead of a number, but I haven't actually used that method myself, so can't vouch for it.

After editing run the "sudo update-grub" command (without the quotes) to set the changes into grub.cfg.

Link #2 in my sig may be worth reading particularly section 5.

---

### Post by Hippytaff on 2010-10-19
think this is what your lookingf for
> 

**grub-set-default** Sets the default boot entry until changed. 
[LIST]
[*]The format is **sudo grub-set-default X**, with **X** being the menuentry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.32-15-generic" 
[*]To obtain the existing menuentry choice number (starting from 0) or the menuentry "string", run grep menuentry /boot/grub/grub.cfg
[/LIST]

---

### Post by chessnerd on 2010-10-19
Take a look at this: [http://ubuntuforums.org/showthread.php?t=1338798](http://ubuntuforums.org/showthread.php?t=1338798)

Apparently, you can just change the numbers of the files in /etc/grub.d

You could try setting OS_Prober to 07_os-prober and see if that moves Windows up to the top...

After that, run sudo update-grub and see if it changes the output order

EDIT: I just tried that with memtest and it worked...

---

### Post by Hippytaff on 2010-10-19
> 
you can just change the numbers of the files in /etc/grub.d

you can...I think what I posted was the terminal command to do this :-)

---

### Post by JonnyOSullivan on 2010-10-19
That works perfectly thanks.

---

### Post by chessnerd on 2010-10-19
> **JonnyOSullivan said:**
> That works perfectly thanks.

Great. Which of the fixes was the one that worked? :)

That way, people reading this a year from now will know which one to go to.

---

### Post by Hippytaff on 2010-10-19
Cool - remember to mark the thread as solved for others to benefit from your hard work :-)

---

### Post by JonnyOSullivan on 2010-10-19
Both had the same the fix in, thanks guys. I'll mark as solve now.

---

### Post by irv on 2010-10-19
Can't you change it by going to System> Administration> StartUp-Manager and pick the one you want from the drop down menu?
[ATTACH]172847[/ATTACH]

---

### Post by Hippytaff on 2010-10-19
> **irv said:**
> Can't you change it by going to System> Administration> StartUp-Manager and pick the one you want from the drop down menu?
[ATTACH]172847[/ATTACH]
 
Think so - I tend to do thigns the command line way, but good point

---

### Post by JonnyOSullivan on 2010-10-19
I kind of have a bigger problem now though, completely unrelated to Ubuntu. Is there a way to turn the computer on at a scheduled time. Ive entered Setup from bios, but no luck. My BIOS is Phoenix secureCore

---

### Post by Hippytaff on 2010-10-19
> **JonnyOSullivan said:**
> I kind of have a bigger problem now though, completely unrelated to Ubuntu. Is there a way to turn the computer on at a scheduled time. Ive entered Setup from bios, but no luck. My BIOS is Phoenix secureCore
 
Maybe start a new thread ;-)

---

### Post by JonnyOSullivan on 2010-10-19
*Starts new thread* Sorry, on some other forums they would burn me at the stake if I did that :3

---

### Post by Hippytaff on 2010-10-19
:-D this is a nice forum with nice people on it

---

