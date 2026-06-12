---
title: "/opt/google/chrome/google-chrome can't remove"
date: 2010-01-09
forum: General Help
---

### Post by gregconquest on 2010-01-09
I have Google Chrome installed on my DELL ubuntu 8.04 mini9:
Google Chrome 4.0.249.43
The path to Chrome is /opt/google/chrome/google-chrome

I cannot uninstall Chrome. Neither **"Add/Remove Applications"** nor **"Synaptic Package Manager"** lists chrome or chromium as being installed.

Trying **Terminal**, neither:```
sudo dpkg -r google-chrome
```nor```
sudo apt-get remove google-chrome
```can even find it (nor does it find chromium-browser or google-unstable).

I am trying to remove / uninstall and then reinstall google chrome because my **Update Manager** is giving me an error which is due to google chrome, I think:```
Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.
```

Can anyone help me, please?

Thank you.
Greg Conquest

---

### Post by ibuclaw on 2010-01-09
Can you post the output of the following commands?
```
grep -nsR "google" /etc/apt
```
and
```
sudo apt-key list
```
Regards
Iain

---

### Post by gregconquest on 2010-01-09
```
grep -nsR "google" /etc/apt
```yields:```
/etc/apt/sources.list.d/google-chrome.list:1:deb http://dl.google.com/linux/deb/ stable main
Binary file /etc/apt/trusted.gpg matches
```

and

```
sudo apt-key list
```yields:```
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   2048R/D73CDC22 2008-08-07
uid                  Canonical Archive Automatic Signing Key <ftpmaster@canonical.com>

pub   1024D/7FAC5991 2007-03-08
uid                  Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   2048g/C07CB649 2007-03-08
```

---

### Post by ibuclaw on 2010-01-09
OK. To remove the Google Repository - you would do the following then.
```

sudo rm /etc/apt/sources.list.d/google-chrome.list
sudo apt-key del 7FAC5991

```

Then run:
```
sudo apt-get update
```
And try removing chrome again.

If you are having difficulties locating the package name, you can use dpkg to find it.
```
dpkg -S /opt/google
```
and dpkg will **Search** for all packages that install into the /opt/google directory and print them out like so:
> **name-of-package**: /opt/google
Regards
Iain

---

### Post by gregconquest on 2010-01-09
Great! This is working, tinivole. I followed what you wrote, and everything was working fine. Still, there were no instances of "google-chrome" from Add/Remove or Synaptic or apt-get remove or dpkg -r... So, running dpkg -S /opt/google finally gave the full name:

**google-chrome-beta**

Then```
sudo dpkg -r google-chrome-beta
```finally got rid of it.

Thank you for the help. I think there must be quite a few other people in the same situation as me who should find this thread useful. I wonder why google has left the chrome beta users stranded like this . . . 

I still need to do a bit more cleaning up and confirming all this after a reboot, so please check back later, but right now **all is looking good **:-)

---

### Post by Guitardude182 on 2010-02-23
I'm having this same problem and I followed this solution, but it does not work for me. When I try to uninstall chrome-unstable it still tells me "E: google-chrome-unstable: cannot remove file "/opt/google/chrome/product_logo_48.png".
I don't blame them for telling me this because I don't even have a /opt directory under my root directory? So what's up with this? Any ideas?

---

