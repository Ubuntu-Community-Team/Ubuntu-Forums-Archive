---
title: "Launching firefox 3.5"
date: 2009-12-24
forum: General Help
---

### Post by luke0927 on 2009-12-24
OK because of all the freezing I had to remove 9.10 and go back to 9.04.  I want to put on FF 3.5.6 I downloaded the tarbal an tried to find the install through there....finally did it through command line

Here is what i used

luke@luke-desktop:/$ sudo apt-get install firefox-3.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.5 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But when I lauch firefox and go to help about it still shows 3.0.16 what do i need to do to make it point to the new 3.5, I'm assuming that is what it is?

Thanks for the help

---

### Post by abhilashm86 on 2009-12-24
see in terminal, which version is being used? ```
firefox -v
```
it should reflect as same in firefox help......

---

### Post by luke0927 on 2009-12-24
luke@luke-desktop:~$ firefox -v
Mozilla Firefox 3.0.16, Copyright (c) 1998 - 2009 mozilla.org


I can go the the extracted 3.5 folder and run ./firefox and it will launch the new 3.5...just have to figure out how to make it run when i start firefox from the shortcut and make it the version when you run the firefox -v

---

### Post by running_rabbit07 on 2009-12-24
To install the tarball, place it in your home folder then copy and paste this command ```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` in a terminal. I got the instructions from [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

I do see that there is a problem if you can't install with the command that you are using. Check System>Administration>Software Sources to make sure the repositories are checked.

---

### Post by luke0927 on 2009-12-24
> **running_rabbit07 said:**
> To install the tarball, place it in your home folder then copy and paste this command ```
if [[ ! -f /usr/bin/firefox ]]; then sudo apt-get update && sudo apt-get install firefox; fi && if [[ -e ~/.mozilla ]]; then cp -R ~/.mozilla ~/.mozilla.backup; fi && sudo tar -jxvf firefox-3*.tar.bz2 -C /opt && rm firefox-3*.tar.bz2 && sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup && sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins && sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` in a terminal. I got the instructions from [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

I do see that there is a problem if you can't install with the command that you are using. Check System>Administration>Software Sources to make sure the repositories are checked.


That didn't work got some errors...anything else I have the 3.5.6 tarbal downloaded and extracted and can launch 3.5.6 from the directory there has to be an easy way to make the system use it as the installed version

---

### Post by bodhi.zazen on 2009-12-24
"firefox" is /usr/bin/firefox

If you look, it is a link =)

```
ls -l /usr/bin | grep firefox
```

so you can make a series of symlinks =)

Do you know how to do that ?

see also :

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

---

### Post by luke0927 on 2009-12-24
No I'm just really a basic user I'll read through it and see if I can figure out how to make it link


luke@luke-desktop:~$ ls -l /usr/bin | grep firefox
lrwxrwxrwx 1 root   root         11 2009-12-23 23:45 abrowser -> firefox-3.0
lrwxrwxrwx 1 root   root         11 2009-12-23 23:45 abrowser-3.0 -> firefox-3.0
lrwxrwxrwx 1 root   root         11 2009-12-24 00:29 abrowser-3.5 -> firefox-3.5
lrwxrwxrwx 1 root   root         11 2009-12-23 23:45 firefox -> firefox-3.0
lrwxrwxrwx 1 root   root         32 2009-12-23 23:45 firefox-3.0 -> ../lib/firefox-3.0.16/firefox.sh
lrwxrwxrwx 1 root   root         31 2009-12-24 00:29 firefox-3.5 -> ../lib/firefox-3.5.6/firefox.sh
luke@luke-desktop:~$

---

### Post by luke0927 on 2009-12-24
OK I see that under application/internet I do have a link to it, its called Shiretoko for the build name...should I just run it this way or should it be set to where when you launch firefox it starts that version.

---

### Post by bodhi.zazen on 2009-12-24
Looking at what you posted, it appears you should be able to run the new firefox with

```
firefox-3.5
```I would update your menu and launchers =)

so you can 

```
sudo unlink /usr/bin/firefox
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox

sudo unlink /usr/bin/abrowser
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/abrowser
```

---

### Post by luke0927 on 2009-12-24
That did it thanks!  Just so I know did I do it right I just didn't know how to set up the links or would there have been an eaiser way?

---

### Post by John Bean on 2009-12-24
> **luke0927 said:**
> That did it thanks!  Just so I know did I do it right I just didn't know how to set up the links or would there have been an eaiser way?

IMO, yes. Put a link named "firefox" in the bin directory of your home folder (create one if it doesn't exist) and point it at firefox 3.5. That way anything that runs "firefox" (rather than using the full path) will run your link first, and this includes the existing launchers.

If you had to create the bin directory you may have to log out and back in again so the path gets updated by the login scripts.

---

