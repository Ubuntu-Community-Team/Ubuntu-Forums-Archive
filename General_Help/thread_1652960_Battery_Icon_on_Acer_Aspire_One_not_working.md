---
title: "Battery Icon on Acer Aspire One not working"
date: 2010-12-26
forum: General Help
---

### Post by Hack.The.Pow. on 2010-12-26
EDIT:  FIGURED IT OUT.

I had to recompile a kernel with a certain patch.  I found this all out through this thread.  [http://ubuntuforums.org/showthread.php?t=1558296](http://ubuntuforums.org/showthread.php?t=1558296)

Hey guys

I just got new netbook for christmas and so I promptly set it up with a dual boot system cause Windows 7 starter is garbage.

Anyways after ditching the Netbook Remix because quite frankly I found the Unity setup to be quite garbage.  Nothing worked the way I wanted it to and I found it quite annoying.

So I ditched it for the regular desktop version.  I quickly found that the battery indicator didn't work.  

I removed and re added the indicator panel.  Nothing.  killed the gnome panel and restarted it multiple times.  still nothing.  Restarted multiple times. nothing.  I even reinstalled gnome-power-management to no avail.  I also installed laptop-mode-tools and nothing has worked.  I went into the power settings and set it to always display the icon and it simply showed a lightning bolt as if there was no battery and it was a tower computer.

Can anybody help?

Update:

So after researching a little more I found out that Acer uses a so called "smart battery" that uses a different bus then normal and this is why Ubuntu(or any other distros) can't find it.

I've read that support for this is built in but needs to be enabled somehow? Does anybody have an idea of how to do this?

---

### Post by drewsus on 2010-12-26
While I had this problem a few versions of Ubuntu in the past, I am unable to remember how I went about treating this. 
Anyway, I can tell you, that for the time being, you can use the following command in terminal to see information about battery life:
```
acpi -b
```

---

### Post by Hack.The.Pow. on 2010-12-26
Damn let me know if you remember.  

Anyway the acpi -b command doesn't output anything.....

---

### Post by Hack.The.Pow. on 2010-12-27
bump. can anybody help?
 
If I can't fix this I'm gonna have to ditch ubuntu.....

---

### Post by Hack.The.Pow. on 2010-12-30
Nobody?

---

