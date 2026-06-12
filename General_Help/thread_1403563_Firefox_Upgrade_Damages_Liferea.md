---
title: "Firefox Upgrade Damages Liferea"
date: 2010-02-10
forum: General Help
---

### Post by Bugs318 on 2010-02-10
I have upgraded my firefox to the Mozilla Build version 3.6 and following that, my liferea seems broken.  It will no longer display previews of threads and I get error messages when trying to open links directly from it in Firefox.

I have tried uninstalling and reinstalling liferea to no avail

Can anyone help fix these problems?  Otherwise, can someone help me figure out how to ensure liferea doesn't start at boot?

Thanks in advance!

---

### Post by rnerwein on 2010-02-10
hi
about 3 hours ago i downloaded the firefox 3.6 too - from:
[http://www.mozilla.com/de/](http://www.mozilla.com/de/)
( every step i did in a root shell )
before downloading i did:
mkdir ~/firefox
download the ziped tarfile to ~/firefox
cd ~/firefox
bzip2 firefox-3.6.tar
tar xvf firefox-3.6.tar
cp -r firefox /opt
cd /usr/bin
ls -l firefox
( notice the link if you want to fall back  ! )
rm firefox
ln -s /opt/firefox/firefox firefox
cd ~/richi

that's all
start firefox   ---> works out of the box - no problems (i just use the new version )
much luck
ciao

---

### Post by lovinglinux on 2010-02-10
> **Bugs318 said:**
> I have upgraded my firefox to the Mozilla Build version 3.6 and following that, my liferea seems broken.  It will no longer display previews of threads and I get error messages when trying to open links directly from it in Firefox.

I have tried uninstalling and reinstalling liferea to no avail

Can anyone help fix these problems?  Otherwise, can someone help me figure out how to ensure liferea doesn't start at boot?

Thanks in advance!

If you installed the Mozilla build by simply extracting it to /opt or somewhere else, it shouldn't be messing with anything. I don't know how Liferea works,but if it requires Firefox to work, then it should be using the default version of it.

To prevent Liferea from starting at boot, remove it from the startup list "Administration >> Preferences >> Startup Applications"

---

### Post by Bugs318 on 2010-02-10
Thanks!  Links at least open in Firefox now, and this build seems better integrated with Hardy now somehow.

That said however, I am still having numerous problems with Liferea that began with this upgrade and any help would be most appreciated:

1) The preview area remains blank when any headline is clicked on, thereby denying me a preview

2) Whenever I load liferea, it automatically starts Firefox and sends it to a page listed in the address bar as "file:///" and it displays my root filesystem in the main browser area.

3) Whenever any headline gets clicked on or highlighted, it opens a new tab (or window if unopened) in firefox, regardless of how my preferences are set.  Furthermore, that new tab lists the url as "file:///" and displays my file-system, rather than displaying the link.  I can open the linked headlines in Firefox properly however by right-clicking and selecting "Launch item in browser"  or I can open it it a new tab in liferea by right-clicking on each as well, but I would prefer if: 1) this was the only way the browser was launched and 2) If I could read my news in the preview pane within liferea as I used to!

I have tried 3 different installation processes for Firefox and have uninstalled and reinstalled liferea countless times to no avail.  It seems it has become hopelessly broken once first attempting the upgrade and I am not certain how to fix it.

Help would be GREATLY appreciated!  Thanks again in advance!

---

### Post by Bugs318 on 2010-02-10
Note that liferea does link directly to Firefox, but doesn't seem to work the same anymore.

Note also that liferea is not listed as an app. in startup applications, but loads anyway (which I wouldn't mind if it was still working as it used to and if it didn't automatically load a firefox window).

---

### Post by Bugs318 on 2010-02-10
Downloaded an upgraded version of liferea from sourceforge instead of repositories and it works fine now!

---

