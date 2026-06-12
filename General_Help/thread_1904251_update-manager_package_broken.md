---
title: "update-manager package broken"
date: 2012-01-04
forum: General Help
---

### Post by balddood on 2012-01-04
Any help someone could provide would be awesome.  I have the following error message in the desktop title bar.  I'm running Ubuntu 11.10.

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 60 in source list /etc/apt/sources.list (URI)'[/B]

---

### Post by balddood on 2012-01-04
I believe I am getting this error after I typed the following command while trying to install the latest version of Thunderbird.

```
[http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main"|sudo tee -a /etc/apt/sources.list > /dev/null
```

---

### Post by plucky on 2012-01-04
Post output from a terminal for ```
cat /etc/apt/sources.list
```

---

### Post by balddood on 2012-01-04
Output:

"[I]# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb
[http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

deb
[http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

deb
[http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
[/I]"

---

### Post by plucky on 2012-01-04
> deb 
[http://downloads.sourceforge.net/pro...la/mozilla/apt](http://downloads.sourceforge.net/pro...la/mozilla/apt) all main

deb
[http://downloads.sourceforge.net/pro...la/mozilla/apt](http://downloads.sourceforge.net/pro...la/mozilla/apt) all main

deb
[http://downloads.sourceforge.net/pro...la/mozilla/apt](http://downloads.sourceforge.net/pro...la/mozilla/apt) all main
" 

Those lines are incorrect and you only need one.

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and remove two of the lines and change the other one to look like ```
deb http://downloads.sourceforge.net/pro...la/mozilla/apt all main
```

Then run ```
sudo apt-get update
``` to see if it is now ok.

Good Luck

---

### Post by spacecheck on 2012-01-04
> **balddood said:**
> Any help someone could provide would be awesome.  I have the following error message in the desktop title bar.  I'm running Ubuntu 11.10.

[B]Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 60 in source list /etc/apt/sources.list (URI)'[/B]

So, with all package mgrs closed, open up the File /etc/apt/sources.list in your editor, turn on line numbering, go to line 60, see what is incorrect in the **(URL)** and either correct it or comment out the offending line. I will point out, too, that the source address redirects in the browser (if allowed).

Good luck!

---

### Post by karthikeya.vecham on 2012-01-04
Hi, 
my package manager has gone some thing wrong with the google-talkplugin.. when i try to install any app i will be prompted with the below message..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-talkplugin needs to be reinstalled, but I can't find an archive for it.

please suggest me where to place this google-talkplugin package manually.. i am not able to install or remove any application because of this error.. please help me..

Thanks in advance

---

### Post by balddood on 2012-01-04
Ok I deleted two of the lines and edited the other then ran update and I was still getting an error so I just deleted all three lines to see if that would fix it.  After typing:

```
sudo apt-get update
```

I get the following errors at the end of the output:

```
W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

How do I just remove that ppa altogether?

---

### Post by spacecheck on 2012-01-04
I didn't see that source listed in your /etc/apt/sources.list Look to see if it's just been added? Your edited entry may just redirect to that source, yo comment it out, too, and then try another update.  Look in Software Sources, too, to see if you have it added under "Other sources". If not Look through the other files in /etc/apt/ to see if there is an entry for that source. If not, Perhaps you could grep for the pattern to find the file.

You could also look in /etc/apt/ to see if there is an earlier version of sources.list from prior to your changes, which you could then reinstate.

Good luck!

---

### Post by spacecheck on 2012-01-04
> **karthikeya.vecham said:**
> Hi, 
my package manager has gone some thing wrong with the google-talkplugin.. when i try to install any app i will be prompted with the below message..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package google-talkplugin needs to be reinstalled, but I can't find an archive for it.

please suggest me where to place this google-talkplugin package manually.. i am not able to install or remove any application because of this error.. please help me..

Thanks in advance

This is unrelated to the original post in this thread. You should start a new thread for it.

Good luck!

---

### Post by balddood on 2012-01-04
Got it all straightened out.  Thanks for the help.

---

### Post by Cookieh on 2012-01-04
You might have a hanging update left, try sudo apt-get upgrade -y
or for root just loose sudo...
 Hope this works..

---

### Post by karthikeya.vecham on 2012-01-05
please suggest me how to post a new post in this ubuntu forums..

---

### Post by spacecheck on 2012-01-05
If you want to post in "General Help" login and go to the "General Help" Forum folder:

[http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

 then click the "New thread" button.

Or, if logged in, click this link:

[http://ubuntuforums.org/newthread.php?do=newthread&f=331](http://ubuntuforums.org/newthread.php?do=newthread&f=331)

Have fun!

---

