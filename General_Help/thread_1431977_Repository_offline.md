---
title: "Repository offline"
date: 2010-03-17
forum: General Help
---

### Post by amouhi on 2010-03-17
Hello,

I haven't internet in my Ubuntu installed laptop.
so, i try to download an on-line repository to my USB key and transfer it to my laptop.
I added the repository from Software sources, i reload packages list... everything it's OK until i want to  install a package with synaptic i had this error:
W:Failed fetch for package /home/repository/dists/karmic/pool/main/a/xxx.deb
file not found.

Please if someone had an idea about what can be the problem. help me!

Thanks,

---

### Post by ajgreeny on 2010-03-17
I would have expected that to work, but as it hasn't, try copying the .deb files from their current folder into /var/cache/apt/archives and do the installation again.  That certainly should work, as I have done it in the past, and it's really only what aptoncd does easier.  You may also need to disable all the online repositories that are enabled by default, as that may otherwise confuse the system.

It would also be worth looking into aptoncd in more detail if the downloading PC is running ubuntu.

---

### Post by amouhi on 2010-03-19
Hello,

All what i downloaded is  these files (such explained in the community documentation [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)) :

[LIST]
[*]Release.txt
[*]Release.gpg
[*]Contents-i386.gz
[*]Packages.bz2              
[*]Packages.gz               
[*]Release
[/LIST]
do i need to download also the .deb files? i don't think so.

Thanks

---

### Post by stinkeye on 2010-03-19
You might want to try [**_[COLOR="DarkRed"]Keryx 0.92.4 (Offline Installer For APT-based Systems)[/COLOR]_**]("http://www.webupd8.org/2010/03/keryx-0924-offline-installer-for-apt.html")

---

