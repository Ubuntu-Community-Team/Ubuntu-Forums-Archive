---
title: "Cannot Install Samba"
date: 2011-05-14
forum: General Help
---

### Post by JNied on 2011-05-14
This is what I get:```
root@Jason-Lin:/# apt-get install samba
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.8~dfsg-1ubuntu2) but 2:3.5.8~dfsg-1ubuntu2.1 is to be installed
         Depends: libwbclient0 (= 2:3.5.8~dfsg-1ubuntu2) but 2:3.5.8~dfsg-1ubuntu2.1 is to be installed
E: Broken packages
root@Jason-Lin:/# apt-get install libwbclient0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwbclient0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
root@Jason-Lin:/# apt-get install samba-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
```

I've actually been getting these errors a lot lately:
"[blank] : Depends: [blank] but [blank] is to be installed"
or 
"[blank] : Depends: [blank] but [blank] is NOT to be installed"

This is a fresh 11.04 install. I grabbed a couple of the basics (alternate browsers, media players, etcetera) but other than that I haven't made any modifications or installed any strange packages.

Any help would be greatly appreciated.  Thank you in advance.


In case it helps:```
root@Jason-Lin:/# uname -a
Linux Jason-Lin 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
```

---

### Post by anjanbanerjee on 2011-07-19
Got exactly the same error installing samba. Please help...

sudo apt-get install samba smbclient
Reading package lists... Done
Building dependency tree       
Reading state information... Done
smbclient is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.8~dfsg-1ubuntu2.1) but 2:3.5.8~dfsg-1ubuntu2.2 is to be installed
         Depends: libwbclient0 (= 2:3.5.8~dfsg-1ubuntu2.1) but 2:3.5.8~dfsg-1ubuntu2.2 is to be installed
E: Broken packages

---

### Post by Surendil on 2011-07-19
try this
```
 apt-get install -f 
```

This should install all the packages you need for samba and then install samba.

---

### Post by JNied on 2011-07-19
```
apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqapt1 libqapt-runtime
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
And I'm still getting the same error when trying to install samba.

---

### Post by Surendil on 2011-07-19
Then i will advice you to purge samba-common and libwbclient0, then try to re-install

```

# apt-get purge samba-common ibwbclient0
# apt-get autoclear

```

Search if there's more samba files and delete them so you can start over again with a clean up installation.

---

### Post by JNied on 2011-07-19
When I tried [color=green]apt-get purge libwbclient0[/color], the first thing it told me was "Removing gnome".  That doesn't seem like a good thing.

Also:
[color=red]E: Invalid operation autoclear[/color]

HOWEVER, I can now successfully install samba.

I reinstalled gnome ([color=green]apt-get install gnome[/color]) and we'll see what happens after a reboot.

---

