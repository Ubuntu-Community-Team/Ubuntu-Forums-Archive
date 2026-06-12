---
title: "Theme changed itself......."
date: 2010-06-12
forum: General Help
---

### Post by learning_ on 2010-06-12
Ok so I was trying to add a keyboard shortcut for a certain command, but when I pulled up the 'Keyboard Shortcuts' menu option, the window looked ... funny somehow. When I clicked the 'Add' button my entire them changed itself. Background and all. It went to a theme that looked almost like a win2000 theme style. I cannot figure out why, nor can I figure out how to change it back.

Thanks in advance,
Learning.

---

### Post by ucal on 2010-06-12
> **learning_ said:**
> Ok so I was trying to add a keyboard shortcut for a certain command, but when I pulled up the 'Keyboard Shortcuts' menu option, the window looked ... funny somehow. When I clicked the 'Add' button my entire them changed itself. Background and all. It went to a theme that looked almost like a win2000 theme style. I cannot figure out why, nor can I figure out how to change it back.

Thanks in advance,
Learning.

Have you tried the appearance menu?

System ---> Preferences ---> Appearance

First tab open is theme select. I have no idea why it would have changed on it's own though.  That's odd.

---

### Post by learning_ on 2010-06-12
yes i tried that, however my menu layouts, nautilus (and other) windows, icons, they wont revert to the ambience theme i had previously selected

---

### Post by llawwehttam on 2010-06-12
have you tried logging off and logging in again?

---

### Post by learning_ on 2010-06-12
Hm, I just did, and for what ever reason, that worked. May I ask why that worked?

---

### Post by learning_ on 2010-06-12
Also, why would logging out then in be the way to fix that? Isn't there a command that can be used to essentially restart any particular process?

---

### Post by fbicknel on 2011-03-24
I just had the same thing happen - and I was also mucking about with my keyboard shortcuts at the time.

Logout/login fixed it.

Bizarre.

I did a quick search at bugs.launchpad.net, found no theme + keyboard in titles there.

Think this is a bug we should report?

---

### Post by learning_ on 2011-04-17
> **fbicknel said:**
> I just had the same thing happen - and I was also mucking about with my keyboard shortcuts at the time.

Logout/login fixed it.

Bizarre.

I did a quick search at bugs.launchpad.net, found no theme + keyboard in titles there.

Think this is a bug we should report?

It's happened to me multiple times since my original post with various versions of Ubuntu. I think we should do the bug report.

---

### Post by 1984dc on 2011-04-20
This Is a problem with the gnome-settings-deamon. 
 
Please see my thread [http://ubuntuforums.org/showthread.php?t=1732697](http://ubuntuforums.org/showthread.php?t=1732697)
 
I have not really got a fix fo it just a diagnosis.

---

### Post by sasepp on 2011-10-06
Same here. Yesterday my theme suddenly changed and then suddenly changed back. I was switching keyboard layouts (using keyboard shortcuts) frequently when this happened. Then, after the original theme returned, my touchpad stopped working. Perhaps this is related, too? I was using pretty standard Ubuntu 11.04 on a Macbook 1,1.

While this was happening - not sure at which point - this was written to /var/log/kern.log:

```

Oct  5 22:45:47 macbook kernel: [48844.049974] gnome-settings-[1905]: segfault at 0 ip 044e47c1 sp bf867460 error 6 in libgnomekbdui.so.4.2.0[44d8000+12000]

```

---

### Post by jaime256 on 2012-01-01
Interesting, I just turned on my computer and my background just changed to blue? I turned off the computer and turned it back on, but still got the same thing.
Just in case anyone else runs into this. I had a wallpaper and just happened to rename it yesterday while organizing/backing up my files. So my background went back to what my appearance screen setting was, blue in this case. I hope this helps. At least this is what my problem was.

---

