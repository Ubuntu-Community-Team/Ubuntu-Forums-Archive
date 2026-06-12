---
title: "Updates not working : Requires installation of untrusted packages"
date: 2012-02-13
forum: General Help
---

### Post by SoulDoubt on 2012-02-13
Hi,

Made the switch from Windows 7 to Ubuntu 11.10 a couple of weeks ago! been loving it so far,

Having a bit of an issue though, today the update manager said I needed 8 updates.. fair enough so when I go to update I get this error:
[B]
[FONT=Courier New]Requires installation of untrusted packages[/FONT][/B][FONT=Courier New]
*The action would require the installation of packages from unauthenticated sources.*
[I]
Details>
linux-generic linux-headers-3.0.0-16 linux-headers-3.0.0-16-generic linux-headers-generic linux-image-3.0.0-16-generic linux-image-generic linux-libc-dev[/I][/FONT]

I've tried everything in:
[http://ubuntuforums.org/showthread.php?t=1626757](http://ubuntuforums.org/showthread.php?t=1626757)

Hope someone can help with this!

Cheers

Edit:
just trying sudo apt-get install [FONT=Courier New][I] linux-generic linux-headers-3.0.0-16 linux-headers-3.0.0-16-generic  linux-headers-generic linux-image-3.0.0-16-generic linux-image-generic  linux-libc-dev to see if this fixes
[/I][/FONT]

---

### Post by jerrrys on 2012-02-13
Some people have had success with this code.  So open a terminal and enter:

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

If that will not clear it; try this in terminal:

sudo -i
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

That should fix it.  The last command (apt-get update) should be error free.  If you get any errors, please post them.

[https://help.ubuntu.com/community/UsingTheTerminal#In_Unity](https://help.ubuntu.com/community/UsingTheTerminal#In_Unity)

And welcome to the forums

---

### Post by SoulDoubt on 2012-02-13
[FONT=Courier New]W: Failed to fetch copy:/var/lib/apt/lists/partial/ppa.launchpad.net_yannubuntu_boot-repair_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.[/FONT]

Got this one - any ideas?

---

### Post by jerrrys on 2012-02-13
Try reinstalling [FONT=Courier New]yannubuntu

If you need further instruction, let me know.
[/FONT]

---

### Post by HiImTye on 2012-02-13
did you add the repository using
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
```or some other method? it should have fetched the authentication key automagically if you did

if you didn't then:
```
gksudo gedit /etc/apt/sources.list
```and remove the repository and then add it using the above method. alternatively, it could have its own list in /etc/apt/sources.list.d and you can just delete that file using:
```
sudo rm /etc/apt/sources.list.d/<listfile>
```

---

