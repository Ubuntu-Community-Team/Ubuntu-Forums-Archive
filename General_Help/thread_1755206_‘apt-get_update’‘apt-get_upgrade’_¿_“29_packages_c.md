---
title: "‘apt-get update’:‘apt-get upgrade’: ¿ “29 packages can be updated.” ??"
date: 2011-05-10
forum: General Help
---

### Post by jtwdyp on 2011-05-10
Just did ‘apt-get update’ then ‘apt-get upgrade’ then ‘apt-get install linux-generic linux-headers-generic linux-image-generic fdutils linux-doc linux-tools’

Now at: “Linux 2.6.32-31-generic on an x86_64”

But upon console login after rebooting into the new kernal:

[quote="tty1"]29 packages can be updated.
26 updates are security updates.[/quote]

Hunh???

Why would Ubuntu insist there are so many updates available when neither apt-get nor synaptic seem to find anything to upgrade???

---

### Post by plucky on 2011-05-11
> **jtwdyp said:**
> Just did ‘apt-get update’ then ‘apt-get upgrade’ then ‘apt-get install linux-generic linux-headers-generic linux-image-generic fdutils linux-doc linux-tools’

Now at: “Linux 2.6.32-31-generic on an x86_64”

But upon console login after rebooting into the new kernal:
Hunh???

Why would Ubuntu insist there are so many updates available when neither apt-get nor synaptic seem to find anything to upgrade???


Is this Ubuntu Server 10.04?

[This](http://ubuntuforums.org/showthread.php?t=1737625) might help.

See [Bug Report](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/766827)

Good Luck

---

### Post by jtwdyp on 2011-05-11
> **plucky said:**
> Is this Ubuntu Server 10.04?
Well it is "Ubuntu 10.04.2 LTS" But even though I boot to console and use startx when/if I'm ready for the gui. it's not a server...

[QUOTE=plucky] [This](http://ubuntuforums.org/showthread.php?t=1737625) might help.[/QUOTE]
Yup that helped. 
sudo rm  /etc/motd.tail
And the problem is solved.
And your link even explained something about the 'why' I'd asked about... Though Now I'm embarrassed. If this is something the installer did, then I should have noticed it a long long time ago...

---

