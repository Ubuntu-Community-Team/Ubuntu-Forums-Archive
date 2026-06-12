---
title: "iPhone 3gs with ios 5"
date: 2012-01-28
forum: General Help
---

### Post by onilink422 on 2012-01-28
I searched around for about an hour, but I think I would do better with personalized help.. Bottom line, when I plug in my iPhone 3gs with ios 5 on my Ubuntu 11.04 Distro, I don't see anything on my Desktop. 
i would be happy if a smarter Linux user would help me to do some Terminal Magic. 
If you need me to post any outputs I will gladly do that. 
My System does not see the iPhone anywhere.

---

### Post by rorschachwalter on 2012-02-02
You probably need to install a later version of libimobiledevice (and perhaps related packages, such as libgpod, libplist, etc). You can add pmcenery's ppa to get these packages for natty:[FONT=monospace]

[/FONT]deb [http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu) natty main

If that doesn't work, Debian testing has updated versions of these packages, so you can Google for something like "debian packages libimobiledevice2", download the packages, then install them using gdebi or dpkg (for instance, run "sudo dpkg -i /path/to/libimobiledevice2-1.1.1" or something similiar).

Hope that helps.

BUT, you most likely won't be able to sync your iPhone anymore, since iOS5 is not supported by the current stack. Regardless of what you may find online, libgpod DOES NOT WORK with iOS 5. You'll be able to mount the phone in Nautilus, and it'll probably show up in Rhythmbox, but it won't let you transfer songs to the device. You will, however, be able to grab photos off of it, for instance.

---

### Post by Darkstar447 on 2012-04-01
I too am having great difficulty trying to get my 3GS to mount. Three days ago it was there, and now there is no evidence of it being connected visually, but lsusb shows it being connected. I have tried just about every install of libimobile with no results, and this issue is starting to give me an aneurysm as the phone is no more than a glorified paperweight now.

---

### Post by idoitprone on 2012-04-01
> **Darkstar447 said:**
> I too am having great difficulty trying to get my 3GS to mount. Three days ago it was there, and now there is no evidence of it being connected visually, but lsusb shows it being connected. I have tried just about every install of libimobile with no results, and this issue is starting to give me an aneurysm as the phone is no more than a glorified paperweight now.

according to their blog [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/), they are still working on io5 support

If i were you, next time, I wont upgrade your software. Well apple have a tendency of not caring about performance, privacy, or security in their products. In fact, they went slower, security is mixed bag, and privacy. lol Most of their so-called "security updates" are patches to thaw modder's access to run homebrew apps or to sync whatever computer they feel like it, like this case.

---

