---
title: "kernal update broke nvidia, I have 1/2 a desktop!"
date: 2011-01-29
forum: General Help
---

### Post by camppen2 on 2011-01-29
Ok, I am running Ubuntu 10.04 and ran the normal weekly updates last night. There were kernal updates listed but they have run alright before so I went ahead and let everything update. On restart my Nvidia drivers would not load, so I restarted in low graphics mode. I uninstalled the Nvidia driver (with the intent of reinstalling them) but decided to restart before I reinstalled the driver (windows habit). upon restart I was told (in a very small box) that Ubuntu was running in low graphics mode. I clicked ok and it proceeded to load, but it loaded it in regular mode and only the right half of the desktop is visible! It is like it is cut totally in half! And I can't get to the important side with Admin and Preferences. I tried boot options but that just gets me a very small colored box. There are no options when it boots just 3/4 of a box that says it is running in low graphics mode because "unable to load module "fglrx" module does not exist". I can not try and reinstall the Nvidia drivers because I can't see the part of the desktop that has Admin on it. I have used Ubuntu for several years now but have not used the terminal very often. 
Does anyone have any help to offer?

---

### Post by sikander3786 on 2011-01-29
Try reconfiguring your graphics. Go to Applications > Accessories > Terminal and follow these commands one by one.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

Commands are case sensitive. Note capital 'X' for X11.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

```
sudo reboot now
```

---

### Post by camppen2 on 2011-01-29
I would try it if I could get to Applications. I can only see the right 1/2 of the desktop. Is there a keyboard way to bring up the terminal?

---

### Post by sikander3786 on 2011-01-29
Press Ctrl + Alt + F1 and log in to tty1 using your login credentials and carry on the commands there.

---

### Post by camppen2 on 2011-01-29
I tried that at the box where it says it is running in low graphics (that is the only thing that comes up at boot) and the screen just goes black, nothing. I restarted and logged in and tried that after my 1/2 a desktop came up but it just goes to a black screen with Ok four times in a row.Is there a way to bring up the terminal with the keyboard after you log in?

---

### Post by sikander3786 on 2011-01-29
Apologies I didn't make that clear. You need to press Ctrl + Alt + F1 from your desktop. At the screen where you are seeing 1/2 of your desktop.

Or another way is to reboot press and hold down Shift key from your Bios screen until you see the Grub menu. Choose the recovery option (2nd on the list) and then choose Drop to root shell prompt and carry on the commands there.

---

### Post by camppen2 on 2011-01-29
this is really weird! I did what you said, I will remember that shift brings up grub, when i chose drop to root shell and pressed enter the whole box just started moving up! I would not do anything but keep moving up. Now it won't do anything at all, I think it froze.

---

### Post by camppen2 on 2011-01-29
I tried it again with a different kernal but it did the same thing- the whole box just kept moving up every time I hit enter, other keys do nothing. Something is really screwed up!

---

### Post by sikander3786 on 2011-01-29
> **camppen2 said:**
> this is really weird! I did what you said, I will remember that shift brings up grub, when i chose drop to root shell and pressed enter the whole box just started moving up! I would not do anything but keep moving up. Now it won't do anything at all, I think it froze.
If it is working wierd even with the command line, are you sure there is no problem with your display itself? You might be interested to test with some other monitor if possible.

---

### Post by camppen2 on 2011-01-29
Sorry I haven't replied but I think the site was down.
monitor is fine, tried it with my laptop.
I figured out how to install Nvidia driver (added another main menu).
Tried what you said but now it boots into safe mode without asking. I think it is the only one now. How do I get back to normal?

---

### Post by camppen2 on 2011-01-29
I managed to fix it. I found there was no xorg.conf in X11 so I found out how to get one. It fixed the problem! I learned a few more things which is great. I won' let the kernel update again though.
thank you for your help!

---

### Post by JKyleOKC on 2011-01-29
Take a look at [http://ubuntuforums.org/showthread.php?p=10410516#post10410516](http://ubuntuforums.org/showthread.php?p=10410516#post10410516), post number 15 (use the up-arrow key), for a way to be able to accept kernel updates without harming your Nvidia drivers.

---

