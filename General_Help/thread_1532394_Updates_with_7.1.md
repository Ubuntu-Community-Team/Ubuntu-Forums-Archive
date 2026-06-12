---
title: "Updates with 7.1"
date: 2010-07-16
forum: General Help
---

### Post by AndyInNYC on 2010-07-16
I am using 7.1 on my home server.  The machine has a 3ware 9500 card in it and all is working well and the sharing/permissions/etc are all as I'd like them to be.

The automatic updates tells me that there are 47 updates available.

When I attempt to let the updates install, the machine tells me that the the upgrades can't be authenticated.  When I click to install, I get the message:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-16-generic_2.6.22-16.62_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-16-generic_2.6.22-16.62_i386.deb)
  404 Not Found [IP: 91.189.92.167 80]

I haven't upgraded to a newer version, because when i tried that in the past the install completely failed (didn't like my hardware).  I have an Asus M2NPV-VM motherboard.

Thanks for any help in fixing my problem(s).


Andrew

---

### Post by ajgreeny on 2010-07-16
7.10 is not supported any more and has not been for over a year.

I don't think you can update it any more unless you move to a newer version.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by digitalcitizenx on 2010-07-16
Maybe it's time to backup all of your data and reinstall a newer version - do not upgrade from the update manager or apt - totally reinstall.

This should give you the best overall experience.

10.04 is a Long Term Support version of Ubuntu - so it should treat you well for many years to come.

---

### Post by snowpine on 2010-07-16
If you edit your /etc/apt/sources.list and change all of the URLS to "old-releases.ubuntu.com" you should be able to apply the 47 updates and bring your computer current as of April 2009, the date that 7.10 reached its "end of life". 

For example, this:

```
http://archive.ubuntu.com/blahblahblahblah
```

becomes:

```
http://old-releases.ubuntu.com/blahblahblahblah
```

I highly recommend installing 10.04 as mentioned above so that your system is not horribly outdated and you have recent bug fixes and security patches. However, if you are happy with your current setup and security is a non-concern, you can certainly continue to use 7.10, keeping in mind it is no longer supported in any way. ;)

---

### Post by imbjr on 2010-07-16
> **snowpine said:**
> If you edit your /etc/apt/sources.list and change all of the URLS to "old-releases.ubuntu.com" you should be able to apply the 47 updates and bring your computer current as of April 2009, the date that 7.10 reached its "end of life".

I do not think that will work. For example:

[http://old-releases.ubuntu.com/releases/gutsy/](http://old-releases.ubuntu.com/releases/gutsy/)

contains only links to old ISOs etc, but no repo material such as deb package.s

---

### Post by gmargo on 2010-07-16
> **imbjr said:**
> I do not think that will work. For example:

[http://old-releases.ubuntu.com/releases/gutsy/](http://old-releases.ubuntu.com/releases/gutsy/)

contains only links to old ISOs etc, but no repo material such as deb package.s

Actually it will work (adjusted for the security site).
The deb packages can be found in [http://old-releases.ubuntu.com/ubuntu/pool/](http://old-releases.ubuntu.com/ubuntu/pool/)
The package lists are under [http://old-releases.ubuntu.com/ubuntu/dists/](http://old-releases.ubuntu.com/ubuntu/dists/)

Use this for a minimal Gutsy /etc/apt/sources.list file:
```

deb http://old-releases.ubuntu.com/ubuntu/ gutsy-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy-updates  main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ gutsy          main restricted universe multiverse


```

---

