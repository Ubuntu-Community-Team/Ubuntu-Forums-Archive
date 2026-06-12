---
title: "No Grub. Automatically Selects OS"
date: 2010-03-08
forum: General Help
---

### Post by Sanchopinky on 2010-03-08
Ok... I can't even begin to type how angry I am. (mainly at my inability to do something for myself)

I tried to cleanup Grub 2. I heard Start-up Manager was the safe option. I installed it from Synaptic opened it up, it didn't offer me any way to cleanup my boot menu so I closed and uninstalled it. What I do remember is it has a default OS option. I dual boot with Win 7 (for school and work).  When I restart my computer it now goes automatically to Ubuntu. I don't even get the option of choosing.

I've tried several guides, lost and recovered grub 2, and now I'm stuck with the same problem 2 hours later. 

This is the one I thought had the best chance of working, but no luck. 

[https://wiki.ubuntu.com/Grub2#Where](https://wiki.ubuntu.com/Grub2#Where) did my Grub2 boot menu go!?!?!

Sorry for my whining & thanks in advanced for the help.

---

### Post by PRC09 on 2010-03-08
If I remember correctly Start-Up Manager allows you to pick which os to boot as well as a time out before it boots your os.Maybe that is your problem.If time out is 0 then it boots directly to the default with no menu.the default is 10 seconds.....

---

### Post by Elfy on 2010-03-08
If you are not seeing the grub menu at boot - you can see it with Shift or edit the grub file to show the menu, this is how the beginning of mine looks

> GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="2"

```
gksudo gedit /etc/default/grub
```

Edit the file, save and then update grub

```
sudo update-grub
```

---

### Post by Sanchopinky on 2010-03-08
See but the thing is, I don't want a time limit. I want the menu to wait until I choose. How would I do that?

---

### Post by PRC09 on 2010-03-08
The maximum time-out in the start-up manager is 100 seconds...I dont know if someone else can figure out how to set it longer manually...

---

### Post by Elfy on 2010-03-08
-1 as a time I believe should do so

Edit - yep 
> 
Setting this value to -1 will cause the menu to display until the user makes a selection. 

---

### Post by Sanchopinky on 2010-03-08
You guys are awesome!\\:D/

Is there a way as easy as this to cleanup Grub?

Thanks again guys!

---

### Post by Elfy on 2010-03-08
clean up grub?

what do you mean exactly.

---

### Post by oldfred on 2010-03-08
If you want to make the default windows:

But Grub 2 also lets you use the title. Suppose your Windows title is [COLOR=DarkRed]"Windows Vista (on /dev/sda1)"[/COLOR]. Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT=[COLOR=DarkRed]"Windows Vista (on /dev/sda1)"[/COLOR]
Then do:
sudo update-grub

---

### Post by Sanchopinky on 2010-03-08
Ah well I mean... when grub shows up it lists all the OS'. I have a bunch of different linux headers. At the moment I have like 4-5 listed and I only really need 1 set.

---

### Post by Elfy on 2010-03-08
In that case open synaptic in the sys admin menu, search for linux-image and mark the old ones for complete removal. I do tend to keep the current and previous myslef though.

---

### Post by Sanchopinky on 2010-03-08
Thanks a lot! That seemed to do the trick.

---

