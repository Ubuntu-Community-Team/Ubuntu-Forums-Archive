---
title: "Touchpad Not Working on ASUS EEEPC 1000 after Karmic upgrade - HELP!"
date: 2009-11-20
forum: General Help
---

### Post by gr81dorn on 2009-11-20
Hi,

I am a total noob to the forum, been using Ubuntu for about a year, but still not super well versed, so bear with me.

I have Ubunto running on 3 different machines, but my main Ubuntu machine is a Asus EEEPC 1000 from Zareason.  Since upgrading my EEEPC, everything works better than it did before except my touchpad does not work at all, not a lick.

I have searched all the forums and all over the web and can't get the fix that works for me.

Here are some facts, hopefully it will help someone (a savior) to get me the help I need.

1) Keyboard works!
2) USB Mouse works
3) I have accessed the /boot/grub/menu.lst and have seen that the main kernel is up to date (2.6.31- 14-generic).  I also noticed a couple of lines relating to the EEEPC kernel, but not sure what I'd change or update on them.
4) I have done the xorg.conf suggestions I've see, but if someone has an exact file that I could just replicate, (if that would solve something) that would be good.
5) I installed the Touchpad GUI thing (System > Preferences > Touchpad - HOWEVER, it doesn't let me access it, instead it gives this error message "GSynaptics couldn't initialize. You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics. But, when i look at those files, i do have it set to 'true' in both locations.

Again, I am a noob, so help me in any way you can and I would be forever grateful...this is SOOOOO frustrating.

Thanks so much in advance.

---

### Post by jimmy the saint on 2009-11-20
I would contact zareason as they support Ubuntu.  They deal with very specific machines, therefore probably have specific knowledge of this issue.  If they can help you, please post the fix for others who experience similar issues.

---

### Post by gr81dorn on 2009-11-20
i talked to Earl...he thought it might be a kernel issue, my main kernel is correct, but when I try and boot up using the eeepc kernel, it fails and gets all sorts of errors and failure notices and then just stops.

Aside from his suggestion about booting to the kernel he said:
"We're still not sure how to get the touchpad working. We're looking into it."

Hopefully there are some folks on here with some ideas.

---

### Post by davidryderuk on 2009-11-22
Hi,
Just to say I'm running 9.10 on the same computer. I haven't had any problem with the touchpad, however I did do a fresh install.

> if someone has an exact file that I could just replicate, (if that would solve something) that would be good. 

I thought it might be worth mentioning that I don't have an xorg.conf file on my computer. You might want to try getting rid of yours (after backing it up) e.g. 

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

---

### Post by Oliphant on 2010-02-27
Maybe this will help, maybe not but it worked for me. 

1. Open a terminal (if you don’t have a mouse hooked up, use Alt+F2).
2.Type “su”, press Enter, and give the root password
3. At the prompt, type:

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

4. At the next prompt, type “reboot”.
Your touchpad will come back up after rebooting.

If you’ve forgotten your “su” password, type “sudo passwd”, and reset it.

HOWEVER, when I used "su" I got an error stating: Authentication Failure. 

I found this work around to get "su" working and then I entered the code above, rebooted and it worked perfectly.

"sudo -i" first, then enter "chmod +s /bin/su"


Maybe there was unnecessary steps maybe not, I don't know.  I am a Ubuntu noob but this worked for me so I hope it helps someone else.

---

