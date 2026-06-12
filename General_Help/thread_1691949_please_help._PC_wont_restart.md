---
title: "please help. PC wont restart"
date: 2011-02-20
forum: General Help
---

### Post by TimEnid on 2011-02-20
I got a prompt for an update so I went thru with it. I restarted my PC but it wont boot up. I keep getting a black terminal screen which asks me for my log in. But when I put it in, nothing happens. I tried to reinstall gdm but it says its already installed. Please help.

---

### Post by TeoBigusGeekus on 2011-02-20
Any error messages from 
```
startx
```
or
```
gnome-session
```
?

---

### Post by TimEnid on 2011-02-20
I got "cannot open display"

---

### Post by MarkX on 2011-02-20
Ditto here (Ubuntu 9.10) Heeeelp!!!

---

### Post by TimEnid on 2011-02-20
> **MarkX said:**
> Ditto here (Ubuntu 9.10) Heeeelp!!!

You have the same exact issue?

---

### Post by MarkX on 2011-02-20
Sort of. Did update and computer won't boot into GUI, just shows the console with login prompt. I can login on the console but don't know what to do to get my desktop back. 
Starx says loads of things including "Failed to oad module nvidia (module does not exist)
Fatal server error: no screens found

Sorry to butt into your thread, maybe your problem is different.

---

### Post by TimEnid on 2011-02-20
> **MarkX said:**
> Sort of. Did update and computer won't boot into GUI, just shows the console with login prompt. I can login on the console but don't know what to do to get my desktop back.

Yep. Same issue here. Hope Some one comes along and  helps us

---

### Post by sanderj on 2011-02-20
Have you run

```
sudo dpkg-reconfigure xserver-xorg

```

and then
```

startx

```

---

### Post by TimEnid on 2011-02-20
This is what I get when I type in "startx"
[IMG]http://i1080.photobucket.com/albums/j324/timrock83/C360_2011-02-2017-54-59.jpg[/IMG]

---

### Post by TimEnid on 2011-02-20
> **sanderj said:**
> Have you run

```
sudo dpkg-reconfigure xserver-xorg

```

and then
```

startx

```

I got the same thing I posted above

---

### Post by MarkX on 2011-02-20
For me that says: Failed to load module "nvidia" (module does not exist)
and the rest is similar to TimEnid's screenshot

---

### Post by sanderj on 2011-02-20
> **TimEnid said:**
> I got the same thing I posted above


To be 100% sure: you type "sudo dpkg-reconfigure xserver-xorg" and you get that screen?

---

### Post by TimEnid on 2011-02-20
> **sanderj said:**
> To be 100% sure: you type "sudo dpkg-reconfigure xserver-xorg" and you get that screen?

Yes. after That I typed startx and got that screen. When I typed in that first command I just get prompted to put in another command and I type in startx.

I put in my live cd and I get initramfs unable to find a medium......

---

### Post by TeoBigusGeekus on 2011-02-20
Try deleting the .xauthority file
```
rm ~/.xauthority
```

---

### Post by TimEnid on 2011-02-20
I'm able to boot thru my live cd

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Try deleting the .xauthority file
```
rm ~/.xauthority
```

And then

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Try deleting the .xauthority file
```
rm ~/.xauthority
```

No such file or directory

---

### Post by TeoBigusGeekus on 2011-02-20
Make that
```
rm ~/.Xauthority
```
(capital x) and reboot
```
sudo reboot
```

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Make that
```
rm ~/.Xauthority
```
(capital x) and reboot
```
sudo reboot
```

Did that. Now I'm back to he black terminal screen. Type the previous command,  the reconfigure?

---

### Post by TeoBigusGeekus on 2011-02-20
Try 
```
startx
```
and post us any error messages.

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Try 
```
startx
```
and post us any error messages.

Still getting that same screen I posted before. Btw, thanks for the help.

---

### Post by TeoBigusGeekus on 2011-02-20
Are you sure you deleted the .Xauthority file?
Post us the output of
```
ls ~/.Xauthority
```

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Are you sure you deleted the .Xauthority file?
Post us the output of
```
ls ~/.Xauthority
```

[IMG]http://i1080.photobucket.com/albums/j324/timrock83/C360_2011-02-2018-46-30.jpg[/IMG]

---

### Post by TeoBigusGeekus on 2011-02-20
Try
```
gnome-session
```
now.

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Try
```
gnome-session
```
now.

Cannot open display

---

### Post by TeoBigusGeekus on 2011-02-20
I'm pretty sure there was a similar thread about a month ago involving the .Xauthority file, only it worked when the op deleted it.
I don't know mate...
Someone else?

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> I'm pretty sure there was a similar thread about a month ago involving the .Xauthority file, only it worked when the op deleted it.
I don't know mate...
Someone else?

so after i delete it, shouldn't I reinstall it?

---

### Post by TeoBigusGeekus on 2011-02-20
No, it is generated automatically.
Since this was the offending file - as your first screen suggested - deleting it should solve your problem: a new file would be generated and everything would be fine.
Only it doesn't work in your case...

---

### Post by Syed75 on 2011-02-20
[http://www.linuxforums.org/forum/newbie/111172-please-help-me-ubuntu-will-not-boot-i-fear-worst.html](http://www.linuxforums.org/forum/newbie/111172-please-help-me-ubuntu-will-not-boot-i-fear-worst.html)

Check this out??

---

### Post by TimEnid on 2011-02-20
> **Syed75 said:**
> [http://www.linuxforums.org/forum/newbie/111172-please-help-me-ubuntu-will-not-boot-i-fear-worst.html](http://www.linuxforums.org/forum/newbie/111172-please-help-me-ubuntu-will-not-boot-i-fear-worst.html)

Check this out??

I don't see how that would help.

---

### Post by Syed75 on 2011-02-20
> **TimEnid said:**
> I don't see how that would help.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386272](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/386272)


This seemed something like your problem.

---

### Post by TimEnid on 2011-02-20
Fixed it. I ran sudo apt-get dist-upgrade and then rebooted and it worked.

---

### Post by TeoBigusGeekus on 2011-02-20
Pheeew... Glad to hear that!
So, it must have been an incomplete upgrade, heh?
Anyway, don't forget to mark the thread as solved.

---

### Post by Syed75 on 2011-02-20
> **TimEnid said:**
> Fixed it. I ran sudo apt-get dist-upgrade and then rebooted and it worked.

Awesome!

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> Pheeew... Glad to hear that!
So, it must have been an incomplete upgrade, heh?
Anyway, don't forget to mark the thread as solved.

seems so. thats been happening often. everytime i download an update, my pc freezes. one time i lost my gdm. i had to reinstall it. I hope this is not something that will continue to happen.

thanks again

---

### Post by TeoBigusGeekus on 2011-02-20
The next time you have notifications for updates, don't use the update manager; run 
```
sudo apt-get update
```
and 
```
sudo apt-get upgrade
```
from terminal, to see if you get any error messages.

---

### Post by TimEnid on 2011-02-20
> **TeoBigusGeekus said:**
> The next time you have notifications for updates, don't use the update manager; run 
```
sudo apt-get update
```
and 
```
sudo apt-get upgrade
```
from terminal, to see if you get any error messages.

will do.

---

### Post by MarkX on 2011-02-21
Glad you got your problem fixed.
Now, what about my similar one, folks?
I did everything Tim did but it hasn't worked. 
It says "cannot open display".

on startx: Failed to load module "nvidia" (module does not exist, 0)

---

### Post by TimEnid on 2011-02-21
> **TeoBigusGeekus said:**
> The next time you have notifications for updates, don't use the update manager; run 
```
sudo apt-get update
```
and 
```
sudo apt-get upgrade
```
from terminal, to see if you get any error messages.

i did an update (got prompted again for it) and got:
> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://deb.opera.com](http://deb.opera.com) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8

W: Failed to fetch [http://deb.opera.com/opera/dists/lenny/Release](http://deb.opera.com/opera/dists/lenny/Release)  

W: Failed to fetch [http://deb.opera.com/opera-beta/dists/testing/Release](http://deb.opera.com/opera-beta/dists/testing/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-amd64_Packages)

and for upgrade, i get:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mkvtoolnix-gui : Depends: mkvtoolnix (>= 4.5.0) but 4.0.0-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.

---

