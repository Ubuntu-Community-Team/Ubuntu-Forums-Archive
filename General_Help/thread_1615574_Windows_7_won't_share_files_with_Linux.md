---
title: "Windows 7 won't share files with Linux"
date: 2010-11-07
forum: General Help
---

### Post by the lemming on 2010-11-07
Hello

Earlier this year I had probs getting Windows 7 to share files with Linux over a network.  Some kind person suggested that I uninstall Windows sign-in assistant and this worked.

Recently I installed Windows Live Essentials 2011 and all seems to have gone pear shaped because I can no longer share files with Ubuntu and Windows 7.

Any ideas or suggestions would be most welcome to help me share files on a home network.

Cheers

---

### Post by Hippytaff on 2010-11-07
Would Samba work? (if your not using it already) :-)

---

### Post by 73ckn797 on 2010-11-07
If Windows will not read your Ubuntu partition you could try looking here:
[http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/). This would be for a dual boot system, however.

Samba will also do the job on a network. Look in Synaptic for Samba and I recommend also installing "system-config-samba" which is the graphical interface.

---

### Post by Morbius1 on 2010-11-07
I hate to tell you this but Windows Live Sign-in Assistant is a dependency of Windows Live Essentials 2011:

From: [http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9ba199ef-3086-4f12-970d-8745be104600](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9ba199ef-3086-4f12-970d-8745be104600)
> Windows Live Sign-in Assistant is a dependency for all programs that are part of Windows Live Essentials 2011. Until the Samba patch is passed on to us you can either uninstall Live Essentials or live without Samba.

Samba Bug Report: [https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

---

### Post by the lemming on 2010-11-07
> **Morbius1 said:**
> I hate to tell you this but Windows Live Sign-in Assistant is a dependency of Windows Live Essentials 2011:

From: [http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9ba199ef-3086-4f12-970d-8745be104600](http://www.microsoft.com/downloads/en/details.aspx?FamilyID=9ba199ef-3086-4f12-970d-8745be104600)
Until the Samba patch is passed on to us you can either uninstall Live Essentials or live without Samba.

Samba Bug Report: [https://bugzilla.samba.org/show_bug.cgi?id=7577](https://bugzilla.samba.org/show_bug.cgi?id=7577)

Hmmm, that's a bit of a bugger knowing that my problem is part of Window's Live essentials 2011 as the apps are quite useful.

Sadly I will uninstall this from my computer.

Any idea how long it will take Samba to be able to resolve this issue?

Cheers

---

### Post by svtdragon on 2010-11-29
As it turns out, this patch was released in 3.5.6 (which is available in a PPA for Natty).  

*patiently waiting for someone to repackage and push into a PPA for lucid*

---

### Post by svtdragon on 2010-11-29
Okay--so I have found a PPA that has Samba 3.5.6 ([release notes]("http://www.samba.org/samba/history/samba-3.5.6.html") say our bug is fixed) packaged in AMD64 for lucid:  [https://launchpad.net/~polslinux/+archive/ppa/+build/2024024](https://launchpad.net/~polslinux/+archive/ppa/+build/2024024)

If you want to install this package from the PPA but not all of the other packages he has, you can install only that package as follows:

Add the PPA with: 
```
sudo add-apt-repository ppa:polslinux/ppa
```
```
sudo apt-get update && sudo apt-get install samba
```

(Note that this won't install ```
smb-client
``` or any of the other recommended packages, but you can install that in the same way--and if you want it, this is the time to do it.)

Then, you can pin the PPA so that those packages are the only ones you get, by following the instructions for Karmic [here]("https://help.ubuntu.com/community/PinningHowto").

My file is located at ```
/etc/apt/preferences.d/ubuntu-smb-35-experimental
``` and contains the following:

```
Package: *
Pin: release o=LP-PPA-polslinux
Pin-Priority: 400
```

From there, do another ```
sudo apt-get update
``` and all should return to normal.  Welcome to Samba 3.5.6!  Hope that helps.

---

### Post by hurricanehrndz on 2010-12-06
any ppa for Maverick Meerkat??

---

### Post by svtdragon on 2010-12-07
I couldn't give you one by name, but you could try searching through [this list]("https://launchpad.net/ubuntu/+ppas?name_filter=samba") for a 3.5.6 version for Maverick.  Or you could try installing the Lucid or Natty package on Maverick, by forcing the installation as found [here]("http://ubuntuforums.org/showthread.php?t=62943").  There may be a newer/better way to force installation of a package from a different version, but I can't think of one offhand.

---

### Post by hurricanehrndz on 2010-12-07
Thank you.

So I downloaded the following packages and follow the instructions as listed in the link.

```
libsmbclient_3.5.6~dfsg-1ubuntu1_i386.deb 
libwbclient0_3.5.6~dfsg-1ubuntu1_i386.deb
winbind_3.5.6~dfsg-1ubuntu1_i386.deb
samba-common_3.5.6~dfsg-1ubuntu1_all.deb
samba-common-bin_3.5.6~dfsg-1ubuntu1_i386.deb 
smbclient_3.5.6~dfsg-1ubuntu1_i386.deb
```installed each one in the order list above using

```
sudo dpkg -i <package.deb>
```and then

```
sudo apt-get -f install
```all seems to be working thanks.

---

### Post by hurricanehrndz on 2010-12-08
Ok Almost there, I spoke to soon. I now have seem to have broken the network browser. I am not sure exactly what it could be, because type smb://ip in the location bar works and so does adding a printer with the full path smb://ip/printer. I am at a lost, I know it's not a big deal, but the best way to learn an OS is by breaking stuff, so I think I am well on my way.

---

### Post by hurricanehrndz on 2010-12-08
Nevermind rebooted windows 7 and all is well.

---

