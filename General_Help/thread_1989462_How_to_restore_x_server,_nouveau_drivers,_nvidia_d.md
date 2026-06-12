---
title: "How to restore x server, nouveau drivers, nvidia drivers when removed"
date: 2012-05-28
forum: General Help
---

### Post by firekage on 2012-05-28
Hi.

Again i have to ask for Your help. I propably destroyed my ubuntu system when i tought about changing drivers.

**I had 180.13 and linux-headers 3.0.0.16, now i have 295.53 and linux-headers 3.1. I use ubuntu 11.10 with GTX260 from nvidia.**

I removed nvidia drivers, propably removed nouveau, i propably even  removed x system because after installation of nvidia drivers i don't  have gui, it can't enter the gui, unity. I see Ubuntu logo with orange  dots - progress bar - and after it, it switch off to a terminal mode,  where i see couple of infos (like: clamav starts and so on) but there is  no gui. **Top command **doesen't show that xorg is in use.

Only thing that i could do is boot trough generic-pae-save options, and enter terminal.

I have installed drivers from repo, but when i put command :

**glxinfo**

i got message that **there is no display!**


Can somebody help me to fix it? I loved ubuntu, i don't want to install  it again, configure and than again read a lot about software and ppa  that i have now

I would like You to tell me how to completly fix x system in Ubuntu, how  to install nvidia drivers, before it how to install/restore noveau  drivers and install linux-headers/images if my are broken.

Please...I've been gighting with it since 20:00, now its 5:00 at clock!  As a matter of fact when i boot it from generic-pae it hungs up at  booting with logo and orange dots below with purple background - nothing  happens, i cant even hit keys to kill x, and enter terminal - i can do  it only trough booting generic-pae-safeoptions.

**How to remove all x drivers, than install it again: noveau, x, nvidia, and how to istall new working kernel?**


If i had known that changing drivers in ubuntu would be such a pain i wouldn't even try it.

---

### Post by pbrane on 2012-05-28
You might try
```

sudo dpkg-reconfigure xserver-xorg

```

this command
```

dpkg -l | grep -E 'nvidia|xorg' | awk '{print $2}'

```

should list all of your installed nvidia and xorg drivers

Have a look at this, maybe it can help you
[http://ubuntuforums.org/showthread.php?t=690760]("http://ubuntuforums.org/showthread.php?t=690760")

---

### Post by firekage on 2012-05-30
> **pbrane said:**
> You might try
```

sudo dpkg-reconfigure xserver-xorg

```this command
```

dpkg -l | grep -E 'nvidia|xorg' | awk '{print $2}'

```should list all of your installed nvidia and xorg drivers

Have a look at this, maybe it can help you
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

Could you write what  does grep -E "nvidia|xorg" and "awk" mean? I see that it is piped trough it, but what does it mean?

---

