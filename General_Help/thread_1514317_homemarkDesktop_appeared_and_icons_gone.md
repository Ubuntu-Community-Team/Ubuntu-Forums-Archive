---
title: "home/mark/Desktop appeared and icons gone"
date: 2010-06-20
forum: General Help
---

### Post by Cool Javelin on 2010-06-20
A new directory (Desktop with uppercase D) appeared in my /home/mark dir and my icons disappeared.

Upon further looking, I see there are 2 directory's in my home, one called desktop (all lower case,) the other is Desktop with uppercase D.

I copied the stuff from desktop to Desktop and my icons are back.

Where is this information kept so I can fix it back. I guess I need to tell Linux to use desktop, but I don't know where that is.

xubuntu Hardy.

Thanks, Mark.

---

### Post by Cool Javelin on 2010-06-21
Anybody?

---

### Post by mikewhatever on 2010-06-21
The default desktop folder in Ubuntu is 'Desktop' and not 'desktop'.

---

### Post by Cool Javelin on 2010-06-22
Thanks, mikewhatever, with your info, I think I may have figured it out, 

Operator Error.

An interesting note, I started looking at the dates, and:

desktop is 2010-06-19 22:19
Desktop is 2010-06-20 12:40

It is looking like Desktop was renamed to desktop at 10:19pm and Desktop was created when I rebooted (in an attempt to restore my missing icons) the next day at 12:40pm.

I copied a bunch of pascal programs from my Windows machine and they were all upper case. I ran a script in a PUTTY window to rename those files (and sub directories) to lower case and may have run it from my personal directory rather then the personal/pascal directory. I guess I hosed it then and didn't notice it till the next day.

Thanks for your help.
Mark.

---

