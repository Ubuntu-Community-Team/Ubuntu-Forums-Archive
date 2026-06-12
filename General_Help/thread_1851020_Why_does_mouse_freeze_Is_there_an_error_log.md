---
title: "Why does mouse freeze? Is there an error log?"
date: 2011-09-27
forum: General Help
---

### Post by kiwibrit on 2011-09-27
I'm very new to Ubuntu, having recently installed 11.04 in an EeePC 1000h  formerly  used with Windows xp.  So far, after a wifi issue had been  fixed, there  has been little problem. 

However, I have had a few times  when the mouse froze, Ctri+Alt+Del did not get me out of jail, and I had  to use the off switch. 

I have not spotted a pattern.

So 2 questions:

1.  How can I find out if I am using the best video driver?  In case it helps 
```
lspci -nn | grep 
```shows 
```
VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile  945GME Express Integrated Graphics Controller [8086:27ae] (rev  03)
```2. Is there an error log somewhere where I can see what happened?

PS: 1GB RAM

---

### Post by Basher101 on 2011-09-27
There is a log, but i do not know where as i never had those. As for your mouse freezing, sometimes your hard disk spins down to save power. Thats when your OS gets very sluggish and laggy for a few seconds as the disk spins up again. If your mouse freezes for a longer time, maybe its your DE. Do you use gnome or KDE or XFCE or LXDE?

---

### Post by kiwibrit on 2011-09-27
Basher101, thanks for your interest.  I am using 11.04 straight out of the tin, so, by default, I think I am using Gnome.

I don't remember a similar problem with Windows, so I don't think that I am having an inherent HDD issue.

---

### Post by ajgreeny on 2011-09-27
There could be something showing in the hidden file **.xsession-errors** in your home folder.

---

### Post by Surkow on 2011-09-27
Network Manager can make your system come to a grinding halt. For me this happens when I connect with unstable networks.

---

### Post by kiwibrit on 2011-09-27
> **ajgreeny said:**
> There could be something showing in the hidden file **.xsession-errors** in your home folder.

There's quite a lot in that, actually - though what's relevant I don't know.  There are a few instances of messages like this
> 
(nautilus:1163): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
Many others lie this:

> (nautilus:1163): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failedAnother

> 
** (process:1164): DEBUG: desktop-launch-listener.vala:118: ran with uri: ghelp:gnome-help#files
** (process:1164): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
** (<unknown>:1149): DEBUG: MaximizeIfBigEnough: Yelp window size doesn't fit

** (<unknown>:1149): WARNING **: Unable to fetch children: Method "Children" with signature "" on interface "org.ayatana.bamf.view" doesn't exist
That lot normal?

---

### Post by jonobr on 2011-09-27
Mouse  and other peripheral issues, I usually open a terminal and type xev 
that allows me to see if the movements are being traceked and seen

Mind you, doing anything without a mouse is tricky

---

### Post by kiwibrit on 2011-09-27
jonobr, now that I have had a few more instances, I can see that it's a total freeze - tab inputs do not work, nor does Ctrl+Alt+Delete.

---

### Post by jonobr on 2011-09-27
Ill get back in my box then ;-)

---

