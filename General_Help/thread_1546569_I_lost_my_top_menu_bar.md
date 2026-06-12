---
title: "I lost my top menu bar"
date: 2010-08-05
forum: General Help
---

### Post by NobleSavage on 2010-08-05
I've been using Ubuntu for about 5 years now. I just installed it on one of my neighbors computers.

I tried deleting an applet from the top menu bar and the entire menu bar disappeared.  I click on the add new menu bar and it just throws something up on the side. I'm using 10.04. I never had this problem before. 

Thanks for any help or advice.

---

### Post by ibuclaw on 2010-08-05
Rename the folder ~/.gconf to ~/.gconf.old - then logout/login and the factory settings will be restored.

Word of advice, there should be an option to warn you on removing a panel. Though ideally you'll want to lock it anyway to prevent such common error.

Regards

---

### Post by NobleSavage on 2010-08-05
> **ibuclaw said:**
> Rename the folder ~/.gconf to ~/.gconf.old - then logout/login and the factory settings will be restored.

Word of advice, there should be an option to warn you on removing a panel. Though ideally you'll want to lock it anyway to prevent such common error.

Regards

Ok, I have 2 accounts on this computer. One for the admin and one for family.  I'm writing this now under family as there is a top menu bar.

Is there a way to launch a terminal under the admin.. I have no accessories option to launch a terminal and I go to Places and get into the home directory.

Or is there a way I can do it from the family account?

Thanks.

---

### Post by davidmohammed on 2010-08-05
reboot - but press shift to display your grub.  Choose the recovery option.  This will given you a number of options.  Choose to drop to a terminal.

Login as administrator and make your changes.

---

### Post by NobleSavage on 2010-08-05
Thanks guys, everything is back to normal now.  Is there an actual way to lock the panels?  The only think I know how to lock are the applets. 

This is something that has always bothered me.  If there is a way to lock the panels them selves this would be great. Often when I set up Ubuntu for other people they have a bad habit of accidentally moving the panels... like to the left or right.

I remember Win 2K had this problem, there was no way to lock the entire panel, but when XP came out you could lock down the entire panel.

---

### Post by ibuclaw on 2010-08-05
hit Alt-F2 and run
```
gconf-editor
```

when you run it navigate to 

```
/apps/panel/global/lock_down
```
Click the checkbox.

---

### Post by marl30 on 2010-08-05
It's my first time posting on this forum, but I have been lurking around for a couple of months since installing Ubuntu. 

You can try this thread: [http://ubuntuforums.org/showthread.php?t=392387](http://ubuntuforums.org/showthread.php?t=392387) there is a command shared in the thread for restoring the panel to default. It has always work for me.

---

### Post by Cavsfan on 2010-08-05
I thought maybe this was similar to a problem I have every so often where the three buttons on the top of all the boxes disappear. 
The Min. Restore and Close buttons.
Terminal, Firefox, any windows I have open do this and i was rebooting to solve it.
But, recently figured out that in the Compiz Icon in Cairo-Dock - if I click on "Reload WM" it fixes it.
Beats re-booting!

---

### Post by ntg on 2010-11-25
It is possible that the bar is still there, but you cant see all your desktop. try these
```
gnome-panel
gnome-panel --restart 
gnome-display-properties
``` (last to set another resolution)

---

