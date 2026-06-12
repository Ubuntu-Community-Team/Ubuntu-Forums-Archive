---
title: "How do I change my computer's name?"
date: 2011-02-13
forum: General Help
---

### Post by Bernie Gallagher on 2011-02-13
Inquiring minds want to know.

---

### Post by Habitual on 2011-02-13
```
man hostname
```

---

### Post by initialhit on 2011-02-13
Should be easily able to do it through the GUI if have one, CLI is sudo hostname <desired hostname>
(see below for a better answer)

---

### Post by Hippytaff on 2011-02-13
and
```

sudo nano /etc/hostname

```
chnge the name, save and it will take effect next time you boot.

---

### Post by Bernie Gallagher on 2011-02-13
> **Hippytaff said:**
> ```
sudo nano /etc/hostname
```

Thanks!  That worked!  I didn't know it was as simple as changing the contents of a text file.  If it's possible to do through Administration on the desktop, it's not obvious.

---

### Post by Hippytaff on 2011-02-13
Glad to be of service ;-)

@[initialhit]("http://ubuntuforums.org/member.php?u=1046584") your method is actually easier - I never knew you could do that...one for the notes :-)

---

### Post by Bernie Gallagher on 2011-02-13
According to **man hostname**, doing **sudo hostname *hostname*** is only temporary.  You have to change the hostname file to make it permanent.

---

### Post by Hippytaff on 2011-02-13
> **Bernie Gallagher said:**
> According to **man hostname**, doing **sudo hostname *hostname*** is only temporary.  You have to change the hostname file to make it permanent.

I'm learning a lot tonight ;-)

---

### Post by Bernie Gallagher on 2011-02-13
> **Hippytaff said:**
> I'm learning a lot tonight ;-)

Me too!

---

### Post by lisati on 2011-02-13
You might have to change the hosts file as well. I'm at work at the moment using XP, so I'm not in a good position to double check.

---

### Post by Hippytaff on 2011-02-13
> **lisati said:**
> You might have to change the hosts file as well. I'm at work at the moment using XP, so I'm not in a good position to double check.

I didn't change the hosts file last time I changed hostname, but I don't know if this would have an impact on networking for samba etc

---

### Post by oldfred on 2011-02-13
I have never done it but my files say you have to change both & reboot immediately. Also Ubuntu tweak should work.

Computer Name
Must do both & reboot right away
sudo gedit /etc/hostname
sudo gedit /etc/hosts
or
Ubuntu Tweak
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Hippytaff on 2011-02-13
I've not changed the hosts file and all seems to work well, but I will change it now anyway...there must be a reason you made those notes!

---

### Post by PaulW2U on 2011-02-13
> **Bernie Gallagher said:**
> Thanks!  That worked!  I didn't know it was as simple as changing the contents of a text file.  If it's possible to do through Administration on the desktop, it's not obvious.
The one time I needed to change my PC's hostname I used Ubuntu Tweak. It didn't work though due to a bug, although that's now been fixed. For anyone who doesn't want to edit a text file [Ubuntu Tweak]("http://ubuntu-tweak.com/") an easy option.

---

### Post by drs305 on 2011-02-13
I have the same notes as *oldfred*, and a quick check shows that Ubuntu Tweak changes both files as well.

---

### Post by Hippytaff on 2011-02-17
Turns out /etc/hosts is automatically updated once /etc/hostname is changed and the system is rebooted - at least on my system :?

---

### Post by Bernie Gallagher on 2011-02-17
Interesting.  I edited /etc/hosts, and I didn't have to change anything either.  I did delete a reference to an old computer on my network that doesn't exist any more, however.

---

### Post by TripleTea on 2011-09-13
hmmmm.....interesting how everyone could change it easily.....I tried editting /etc/hostname and /etc/hosts just like oldfred suggested but it didn't seem to change my computer's name....

anyone have any idea as to why it didn't work in my case ?? im using a live usb boot on Ubuntu 11.04.

---

### Post by nothingspecial on 2011-09-13
Hi TripleTea,

I'm closing this thread because you have also asked your question in this thread.

[http://ubuntuforums.org/showthread.php?t=1725860](http://ubuntuforums.org/showthread.php?t=1725860)

One thread per issue please or you dilute community effort. You are more likely to get help in the one not marked solved.

---

