---
title: "Screenlets"
date: 2011-07-01
forum: General Help
---

### Post by sjorsv on 2011-07-01
I tried to install screenlets for my 11.04 ubuntu laptop
so i typed in 
[HTML]sudo apt-get install screenlets[/HTML]
then the output was:
[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 screenlets : Depends: python-beautifulsoup but it is not installable
              Recommends: python-evolution but it is not installable or
                          python-gnome2-desktop but it is not installable
              Recommends: python-rsvg but it is not installable or
                          python-gnome2-desktop but it is not installable
E: Broken packages
root@sjors-Inspiron-1012:~# sudo apt-get install screenlets-pack-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 screenlets-pack-all : Depends: screenlets (>= 0.1.2-9) but it is not going to be installed
                       Recommends: python-gnome2-extras but it is not installable
                       Recommends: python-dateutil but it is not installable
                       Recommends: python-gdata (>= 2.0.10) but it is not going to be installed
E: Broken packages
root@sjors-Inspiron-1012:~# 
[/HTML]

---

### Post by sjorsv on 2011-07-01
i typed this stuff in the terminal just so you know

---

### Post by CharlesA on 2011-07-01
Try running this:

```
sudo apt-get install -f
```

---

### Post by sjorsv on 2011-07-01
i typed in the command and this was the output:[HTML]Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  ubuntuone-control-panel libgdata1.7-cil libmono-zeroconf1.0-cil
  libgkeyfile1.0-cil gir1.2-soup-2.4 python-ubuntuone-control-panel
  libubuntuone1.0-cil libgtk-sharp-beans-cil libtaglib2.0-cil libgudev1.0-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/HTML]
then i tried installing screenlets but i got the same error messege
as before

---

### Post by CharlesA on 2011-07-01
Ok, try this then:

```
sudo apt-get update
```

Then try to reinstall it.

---

### Post by sjorsv on 2011-07-01
i typed it in and this is part of the output it looks important
[HTML]W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nautilus-security/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nautilus-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nautilus-security/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/nautilus-security/universe/binary-i386/Packages  404  Not Found [IP: 91.189.92.166 80]

W: Failed to fetch http://ppa.launchpad.net/nilarimogard/test3/ubuntu/dists/natty/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/nilarimogard/test3/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nautilus-updates/restricted/binary-i386/Packages  404  Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nautilus-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nautilus-updates/multiverse/binary-i386/Packages  404  Not Found [IP: 91.189.88.30 80]

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/nautilus-updates/universe/binary-i386/Packages  404  Not Found [IP: 91.189.88.30 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/HTML]
the i tried to install screenlets and once more got the same error message as in my first post

P.S id just like to take moment and say thank you for helping me out because i no things will work out

---

### Post by CharlesA on 2011-07-01
Did you modify your sources.list file manually?

nautilus should be natty.

[http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/](http://archive.ubuntu.com/ubuntu/dists/natty-updates/universe/binary-i386/)

---

### Post by Frogs Hair on 2011-07-01
If you can't get that version to work , the link has a PPA that includes bug fixes for 11.04 .
[http://www.linuxnov.com/install-screenlets-0-1-4-in-ubuntu-11-04-natty-narwhal-ppa/](http://www.linuxnov.com/install-screenlets-0-1-4-in-ubuntu-11-04-natty-narwhal-ppa/)

---

### Post by sjorsv on 2011-07-01
i dont no what did it but im downloading screenlets right now thanks so much
what i did that might have been it was change all the ppas that said nautilus to natty and add the ppa they used as an example when you open sources.list and click add ppa

---

