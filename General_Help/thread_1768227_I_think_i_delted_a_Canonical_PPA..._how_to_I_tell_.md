---
title: "I think i delted a Canonical PPA... how to I tell/ get it back?"
date: 2011-05-26
forum: General Help
---

### Post by Kruger2147 on 2011-05-26
I was uninstalling some applications by deleting their ppa's in the software center, and I think I may have deleted a ppa from canonical. How do I tell and/or get it back. Some of my updates arent working and i have the red triangle with ! in the middle in my notification bar.

I'm running Natty 32bit

---

### Post by Ghost|BTFH on 2011-05-26
```
deb:http://archive.canonical.com/ubuntu natty partner
```

Is for Canonical Partners (If you don't see that one listed, add it)

```
deb:http://extras.ubuntu.com/ubuntu natty main
```

Is for Independent (If you don't see that one listed, add it)

The rest are on the Ubuntu Software tab and are simply check and uncheck to add or remove.

Just make sure to reload your packages after changing repositories.

Hope that helps!

Cheers,
Ghost|BTFH

---

### Post by 4Orbs on 2011-05-26
My updates aren't working either. Maybe we are about to get the first big update since Natty's release?

---

### Post by Kruger2147 on 2011-05-26
thank you.

BTW they dont work with ```
deb:http...
``` you have to put a space so it looks like ```
deb http...
``` thank you.

to reload my packages, I just run the updater?

---

### Post by Ghost|BTFH on 2011-05-27
There's a little arrow looking refresh button on the left-hand side of Synaptic Package Manager.  Click to reload.

Cheers,
Ghost|BTFH

---

### Post by Kruger2147 on 2011-05-27
After I added those two repositories and refreshed I got this: 
[IMG]http://i.imgur.com/Dlr5V.jpg[/IMG]

Here is all the code from the error page.

```
Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
Failed to fetch http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
Failed to fetch http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead. 
```

What do i do now? 

Thank you for helping. I'm a bit of a newb.

---

### Post by linuxinstalledfromhdd on 2011-05-27
If for some reason you can't get to work, or there isn't a good work-around solution, I would suggest reisntalling and trying to follow a step-by-step guide to get your repositories configured.  Here's a good one you can try:

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

Works like a charm everytime.

---

### Post by gandaran on 2011-05-27
> Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)/dists/natty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
the cd repository you should disable it in software sources, theres no reason to keep it enabled or you will have to put the ubuntu live cd in the dvd drive every time you update the package list.
the others could be a temporally down server or just some typing error when adding the PPA or even those PPA don't really work for natty 11.04, try removing them then update and if all is well add the PPA again.

---

### Post by Kruger2147 on 2011-05-27
OK, sorry for the stupid question. How do I disable the CD repository?

---

### Post by gandaran on 2011-05-27
> **Kruger2147 said:**
> OK, sorry for the stupid question. How do I disable the CD repository?
in synaptic package manager menu bar look for repositories, I'm not on ubuntu now so cant tell exactly where.

---

### Post by plucky on 2011-05-27
```
Failed to fetch http://ppa.launchpad.net/lorenzo-car...source/Sources 404 Not Found
```

I cannot find that PPA in the Launchpad Index list.


> Failed to fetch [http://ppa.launchpad.net/songbird-da...source/Sources](http://ppa.launchpad.net/songbird-da...source/Sources) 404 Not Found

There isn't a PPA for Natty or Maverick.

See [Here](http://ppa.launchpad.net/songbird-daily/ppa/ubuntu/dists/)

Disable them in "Software Sources" and the "404 Not Found" errors should go away.

Good Luck

---

