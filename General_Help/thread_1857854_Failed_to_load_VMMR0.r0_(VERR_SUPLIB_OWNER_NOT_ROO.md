---
title: "Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT)."
date: 2011-10-11
forum: General Help
---

### Post by papampi on 2011-10-11
I have a problem starting virtualbox on my ubuntu 11.04 .
install shows no error and i can manage a new virtual but when i'm going to start the new virtual with windows xp it give me error !
I installed and removed many times !
I installed virtualbox-4.0 and 4.1 from terminal and also from synaptic virtualbox-ose all with same result !!!
I searched so much and read many post over the net and i have no idea what i should do to make it work !!!
here is the error when i click the start :
```
Failed to open a session for the virtual machine Windows XP.
Failed to load VMMR0.r0 (VERR_SUPLIB_OWNER_NOT_ROOT).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console
Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}

```
i chown root:root /usr/lib/virtualbox/
and this is the output :

```
payam@PAYAM-UBUNTU:/$ sudo chown root:root /usr/lib/virtualbox/
payam@PAYAM-UBUNTU:/$ ls -ld /usr/lib/virtualbox/
drwxr-xr-x 5 root root 4096 2011-10-11 00:57 /usr/lib/virtualbox/

```
any idea what should i do to make it run my virtual.

---

### Post by papampi on 2011-10-11
any idea ?????

---

### Post by skierpage on 2011-11-28
I had the same problem. I'm running Kubuntu 11.10 with VirtualBox 4.1.6 regularly updated from Oracle's own .deb file. It turns out, as Googling suggests, my /usr and /usr/lib were owned by user:group 501:501.  Weird, I have no idea how this happened.  /usr/lib/virtualbox and its contents were owner:group root:root.

So, in a terminal, check by entering:```
ls -ld /usr /usr/lib
```If it doesn't show "root root", then enter: ```
sudo chown root:root /usr /usr/lib
``` After this I retried and I could boot a VirtualBox from my .iso

I hope this helps.

---

