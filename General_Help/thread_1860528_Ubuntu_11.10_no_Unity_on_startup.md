---
title: "Ubuntu 11.10 no Unity on startup"
date: 2011-10-14
forum: General Help
---

### Post by virgiliox on 2011-10-14
HI, I just installed Oneiric Ocelot for the 2nd time since yesterday, I uninstalled it the first time because I ran into the same problem again. After installing the ATI drivers, when I login to my user account, Unity and the top bar disappeared. I had to run firefox from the terminal by pressing CTRL+ALT+T to be able to post this comment. If anyone can please point me into the right direction. this is really frustrating. I've waited for months for this release and now I'm really disappointed by the way it has been behaving. Thank you very much in advance.

---

### Post by Prosis on 2011-10-14
Same here, this is very annoying! :(

This is what I get when I try to run aticonfig

aticonfig: error while loading shared libraries: libGL.so.1: wrong ELF class: ELFCLASS32

---

### Post by Musmanno on 2011-10-14
Check your system settings. Sometimes the Unity plugin gets unselected automatically. Not sure why. If it is unselected, select it and log back in.

---

### Post by effenberg0x0 on 2011-10-14
Use the terminal to run this commands:

```
sudo apt-get install compizconfig-settings-manager
/usr/bin/ccsm
```

Inside ccsm, check that the Ubuntu Unity Plugin is enabled. If it is, deactivate, wait 5 sec, reactivate it. If it's not, activate it.

Regards,
Effenberg

---

### Post by harlequin_ on 2011-10-14
Yep, this is worked for me on the same problem


> **effenberg0x0 said:**
> Use the terminal to run this commands:

```
sudo apt-get install compizconfig-settings-manager
/usr/bin/ccsm
```Inside ccsm, check that the Ubuntu Unity Plugin is enabled. If it is, deactivate, wait 5 sec, reactivate it. If it's not, activate it.

Regards,
Effenberg

---

### Post by Prosis on 2011-10-14
That didn't do it for me. It was indeed unchecked and I checked it. Then it told me about some conflict between some keys and then, once all that was out of the way, I disconnected and reconnected. No luck. I even restarted. :(

Thing is there seems to be a problem with the ATI driver. I installed it which caused the problem and I can't configure it in any way.

I even installed Gnome-Shell and when I connect with Gnome I get Classic Gnome. No 3D acceleration

---

### Post by durtie on 2011-10-14
did you hit ignore conflicts?

---

### Post by Prosis on 2011-10-14
No resolve I think.

---

### Post by virgiliox on 2011-10-14
None of that worked for me either, I guess I'll just give up on Ubuntu for now until this issue is resolved. They basically screwed the whole system after adding Unity to it. The last good release I can remember was 10.04, afterwards it's been nothing but crap in my opinion.

---

### Post by Prosis on 2011-10-14
That's the way I feel too right now. But I don't think it's Unity the problem. I think it has to do with the driver itself.

---

### Post by Prosis on 2011-10-14
It's definitely the driver! I uninstalled it (go to /usr/share/ati and run sudo sh ./fglrx-uninstall.sh) and Unity's back after reboot...

---

### Post by Prosis on 2011-10-15
GOT IT!!!

Found on this forum, solution given by effenberg0x0 to whom I tip my hat!

Follow these instructions:

[http://ubuntuforums.org/showpost.php?p=11326398&postcount=5](http://ubuntuforums.org/showpost.php?p=11326398&postcount=5)

---

### Post by effenberg0x0 on 2011-10-15
Cool, glad it worked for you.

Regards,
Effenberg

---

### Post by virgiliox on 2011-10-15
Since I couldn't understand how to do that, I just went the easy way and reinstalled it again :), this time I won't be installing the ATI drivers so I guess I should be fine. ANyways, thanks for all your help :)

---

### Post by Tidu5 on 2011-10-16
I solved it in this way:
after installing ati drivers, you have to copy file ./usr/lib/fglrx/FGL.renamed.libGL.so.1.2 in ./usr/lib/ and rename it to libGL.so.1

then reboot and everything will work as it is supposed to do!

---

