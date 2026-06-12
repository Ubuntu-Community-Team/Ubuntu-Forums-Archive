---
title: "Network Manager"
date: 2011-02-12
forum: General Help
---

### Post by theozzlives on 2011-02-12
I got up today fixin to copy some files to my laptop, but my laptop didn't appear on my network. After some investigation, I find network Manager isn't running (in fact it looked like my Notification Area was gone). I proceeded to install my Notification Area to my panel to no avail. 

I decided to moved my laptop to my office to try wired network, that did no good either. When I unplugged my laptop, the battery popped up so I know the Notification Area is working.

I don't know how Network Manager got all flubbed up, any help would be appreciated.

Update: Wired network does work, but no NM icon in the panel.

---

### Post by plucky on 2011-02-12
> **theozzlives said:**
> I got up today fixin to copy some files to my laptop, but my laptop didn't appear on my network. After some investigation, I find network Manager isn't running (in fact it looked like my Notification Area was gone). I proceeded to install my Notification Area to my panel to no avail. 

I decided to moved my laptop to my office to try wired network, that did no good either. When I unplugged my laptop, the battery popped up so I know the Notification Area is working.

I don't know how Network Manager got all flubbed up, any help would be appreciated.

Update: Wired network does work, but no NM icon in the panel.

Try ALT+F2 and ```
nm-applet &
``` and see if that brings it back.

Good Luck

---

### Post by theozzlives on 2011-02-12
> **plucky said:**
> Try ALT+F2 and ```
nm-applet &
``` and see if that brings it back.

Good Luck

Yeah that worked, but I'm baffled why it did do that and am I gonna have to do this all the time now?

---

### Post by grahammechanical on 2011-02-12
Make sure that Network Manager is in the list of Startup Applications. Was the icon removed from the panel or was Network Manager not loaded? This is the question.

Regards.

---

### Post by theozzlives on 2011-02-22
> **theozzlives said:**
> Yeah that worked, but I'm baffled why it did do that and am I gonna have to do this all the time now?

That works but now I have to connect to my network manually and it asks for my password everytime I reboot. I tried to re-create the key-ring to no avail.

---

