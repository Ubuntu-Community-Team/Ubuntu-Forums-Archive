---
title: "I get kicked back to lightdm right after login"
date: 2011-12-03
forum: General Help
---

### Post by snlzkn on 2011-12-03
Hi,

I was using my Ubuntu for some time but at some point I became unable to login again. I searched on the internet and people suggested removing .Xauthority but it did not help me at all. Sometimes I managed to get Unity again with sudo startx but then I am logged in as root which is not a good solution.
I fiddled with my ubuntu a lot so I decided to do a fresh install on a virtual machine. After my fresh install, I installed LabVIEW, SVN Workbench and VI Packet Manager and the latest updates. It took me couple of hours to do all of this and in the end the same thing happened! LabVIEW and VI Packet Manager installations are just moving some files under usr/local/ and I cannot see how they can stop me from logging in. But the others were installed from the repository so I am not suspecting them too much.

I tried Gnome, Gnome Classic and Ubuntu 2D as well and all of them directly return back to lightdm. On VirtualBox I did not install ccsm or do some other compiz adjustments. Where can I look to find some error messages?  I had a quick look to /var/log/Xorg.log but I did not notice anything. All suggestions are welcome.

---

### Post by The Cog on 2011-12-03
Sometimes you have to remove .ICEauthority as well as .Xauthority. 

For this problem, try logging into a Ctrl-Alt-F1 console and doing "sudo stop lightdm". Then you can try "startx" and see if it generates any useful error messages.

---

### Post by snlzkn on 2011-12-03
Deleting both files also did not help. When I used startx I received the following errors (lines starting with (EE)). 

```

AIGLX: reverting to software rendering
Error compiling keymap (-)
XKB: Couldn't compile keymap
XKB: Failed to load... loading default
Keyboard initialisation failed.
Failed to activate core devices

```

So I need to set my keyboard mapping somehow. How was it erased any way :S I guess I can find this one a solution online after dinner :)

---

### Post by snlzkn on 2011-12-03
Well the problem was not related to keyboard. Somehow my temp folder did not allow others to write.
```
sudo chmod o+w /tmp
```
solved the problem. But I really need to find what changes the permissions of /tmp.

---

### Post by The Cog on 2011-12-04
My /tmp looks like this:
> drwxrwxrwt 12 root root 4096 2011-12-04 13:18 /tmpYou can achieve that with:
```
sudo chown root:root /tmp
sudo chmod 777 /tmp
sudo chmod +t /tmp
```

---

