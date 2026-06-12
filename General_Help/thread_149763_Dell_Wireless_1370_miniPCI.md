---
title: "Dell Wireless 1370 miniPCI"
date: 2006-03-24
forum: General Help
---

### Post by thetragedyofhumor on 2006-03-24
](*,)  sums it up.

I have a Dell Inspiron 2200 notebook with a Dell Wireless 1370 miniPCI card, and im having a hard time finding out how to get it to work. Im runing Ubuntu 5.10.

I dont realy know what to do or say, aside that the only solution i have seen so far is to download the windows driver and use ndiswrapper. Problem with that being that i dont know how to use ndiswrapper, and even if i did, it wasnt included in the Ubuntu package. I searched the Broadcom website for "linux 1370" and it came up with a few links, but they dont give a specific model name, just 'raid 2.1.0'. The RPMs on the site are for Redhat4 Fedora4 and Suse9 but i dont know if i can make any of those work with my system. The readme on the site also said somthing about needing Gcc to compile somthing, but again thats somthing unincluded in the package i downloaded, and i have no idea where to get software for this distro.

Im realy very lost and very new to Linux, but if someone would walk me through how to get this setup, and explain what each step does, id be extremely grateful.

Thank you much.

---

### Post by Jagot on 2006-03-24
I had a smiliar problem a little while ago.

Use Synaptic to download ndiswrapper (think it might be called ndiswrapper-utils but I'm not in Ubuntu at the moment - it should be fairly obvious anyway), then follow the thread below:

[http://ubuntuforums.org/showthread.php?t=120383](http://ubuntuforums.org/showthread.php?t=120383)

---

### Post by thetragedyofhumor on 2006-03-24
that seems like it may work, but i have a problem right off the bat: the ndiswrapper file on the ubuntu_5.10 cd is a [dot]deb file, and i dont know how to work with that. one would think that a [dot]deb would be used with debian, as it even has the debian logo on the icon, but im completely clueless

i probibly should have mentioned that i dont have any way to download anything with my nix machine, as i cant get it online, or get it to comunicate at all with my windows machine

---

