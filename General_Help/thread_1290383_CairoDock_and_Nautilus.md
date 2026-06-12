---
title: "CairoDock and Nautilus"
date: 2009-10-13
forum: General Help
---

### Post by AlanR8 on 2009-10-13
Good evening and I trust I find you all well?

This is beginning to p**s me off!

Have Cairo installed and am really impressed! All works well and I can just drag and drop application icons to the dock and they just work......apart from an icon for Nautilus!

If I have Nautilus open, I can click the menu "Make a launcher" and it WON'T work. If I click the applet Bin then I CAN open an instance of Nautilus. If I try to create a manual launcher for Nautilus it WON'T work.

What am I doing wrong? Do I need to include some switches to make the launcher work, and if so why because if, for example I drag FireFox to the bar it just works?

Confused......

---

### Post by slambrick on 2009-10-15
I hate to say this Alan but I have exactly the same problem and whilst googling found the exact same issue from users over a year ago with no resolution. I'm guessing it's not found it's way to the right bug list. Any maintainers out there? can you let those of us with this issue what is going on?

---

### Post by ankspo71 on 2009-10-15
Hi,
Your can drag your home folder from the menu to cairo dock too. Then you can change the icon and name if you want. I have been trying to manually create shortcuts too, but some of them don't work. But they are working for me when I drag and drop an item onto the dock.
Hope this helps,
James

---

### Post by akakingess on 2009-10-15
I would suggest checking to see if it has been reported to launchpad.net in the upper right-hand corner of the forums screen, and if no bug has been reported or it is not a reported issue, than I suggest reporting it and giving as much detail as possible while doing so.  That is the only way we progress, is if everyone contributes just a little bit and even just reporting something not working is contributing  :)

---

### Post by howefield on 2009-10-15
> **AlanR8 said:**
> If I try to create a manual launcher for Nautilus it WON'T work.

Am I misunderstanding your issue ?

Right clicking the dock and selecting "add a custom launcher" allows you to create a launcher for nautilus.

---

### Post by justleen on 2009-10-15
I just dragged  a folder to cairo dock, which functions as a shortcut to nautilus.. works just fine?

---

### Post by fabounet on 2009-10-15
I don't have such issue (just tested on CD2.1.1, dragging the nautilus launcher from the menu works)
I just changed the icon name from "system-file-manager" to "nautilus" to have a better icon.

---

### Post by ankspo71 on 2009-10-15
Hi fabounet
I'm using cairo dock version 2.1.0 on Ubuntu 9.10 beta, and I had some trouble adding some manually created launchers to cairo dock. One I can remember was trying to manually add htop to the dock and htop would not launch. However, I can easily drag and drop the htop shortcut from the gnome menu to the dock and it will work. It is a command line program if it helps any. Despite this only minor problem I had it still is my favorite dock. :P I had trouble adding the nautilus shortcuts back when I was using Ubuntu 9.10 (with the previous version of Cairo Dock).
Thanks,
James.

---

### Post by AlanR8 on 2009-10-15
Thanks for the responses guys. Do you know, I didn't realise I could just drag a menu item from the menu to the dock. I now have a functional Nautilus item on my Dock! Thank you.

However, I can't change the icon. I'm using Mac4Lin and I want the Mac Icon (that appears last but one on the right of the dock when Nautilus is open). The screen shot below shows the dock with the Ubuntu Home Icon on the right and the properties of the Icon displayed. There's no option to change the icon.

Suggestions?

---

### Post by ankspo71 on 2009-10-15
Hi,
If it is an applet,
Right click on it and select 'configure this applet', then set the path for the mac4lin icon you want to use.

If it is a launcher,
Right click on it and select 'modify this launcher', then set the path for the mac4lin icon you want to use.

mac4lin icons should be in  /home/<yourname>/.icons or /usr/share/icons . (according to the mac4lin v1.0 installer)
James

---

### Post by fabounet on 2009-10-16
instead of setting a path, you can just add the icon theme you want to use in the config (in the Icon module), and keep the short names.
It's better because then you can just switch to another theme when you want, and the icons will follow it.

---

### Post by AlanR8 on 2009-10-18
Sorted!!

Opened an instance of Nautilus and made the icon a launcher in the dock. Then went into the properties and altered the launch command to:

nautilus /home/alan (substitute your name for mine).

It worked.

---

