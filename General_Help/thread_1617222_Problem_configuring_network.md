---
title: "Problem configuring network"
date: 2010-11-09
forum: General Help
---

### Post by ordidoc on 2010-11-09
Brand new installation of Ubuntu Studio, seems that i'm going to use it for audio and i already use another distro (PCLinuxOS) for the everyday work so i know a bit about Linux but now i cannot configure any network connection, either with cable or wireless. 

I did not configure network when i installed it and for some kind of reason it's not working when i try to configure it to access the web. Is there anything that you can recommend to do to make it work?

Thanks for your time

---

### Post by skillet-thief on 2010-11-09
You probably should give some more information. To start with, the output from:

```
$ sudo ifconfig
```

---

### Post by ordidoc on 2010-11-09
skillet-thief, i'll do that later on today, got to go for now and i'm not on Ubuntu, i have many hard drive that i use with my laptop and i'm not using the right one for now so i'll do that today and post it later.

Thanks

---

### Post by stinkeye on 2010-11-09
> **ordidoc said:**
> I did not configure network when i installed it and for some kind of reason it's not working when i try to configure it to access the web. Is there anything that you can recommend to do to make it work?

I did the same thing when installing ubuntu_studio.

You need run the ubuntu studio cd and install all the packages
in **/pool/main/n/network-manager**.
Just double click on the file and if it fails, take a note of the dependency needed and install that file first.

Then install network-manager-gnome in /pool/main/n/network-manager-applet
I can't remember now but I think I had to install another package to do with policykit.
Possibly **policykit-1-gnome** and/or **policykit-desktop-privileges**.

---

### Post by ordidoc on 2010-11-09
Thanks for the replies, i'll use the CD and install all the packages as recommended and see what it does.

---

### Post by ordidoc on 2010-11-09
Well, more problems, this is the error message that i get when i try to install network

Network autoconfiguration fail
Your network is probably not usign DHCP protocol. Alternatively, the DHCP server may be slow or some network hardware is not working properly.

Strange enough, all the distro's that i installed on my laptop were almost installing the network automatically, i just had to put the password for the wireless and that's was it but with this one it's a no go.

I know that i don't have any problems with my hardware so any suggestion about to to make it work will be welcome. 

Thanks again

---

### Post by ordidoc on 2010-11-10
Anyone on this please :)

---

### Post by skillet-thief on 2010-11-10
What does ```
$ sudo ifconfig
``` give you?

---

### Post by ordidoc on 2010-11-10
Sorry if i take time to answer, i'm busy with some other computers.

Finally, the solution was to install Ubuntu with the network cable plug into the laptop, everything is working fine now and i'm able to use internet. 

Thanks for your time :)

---

