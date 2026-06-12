---
title: "Virtualbox Dependency Issue"
date: 2011-09-18
forum: General Help
---

### Post by dstrout on 2011-09-18
I tried to install Virtualbox OSE today, and I got the following errors:

```

The following packages have unmet dependencies:

virtualbox-ose-qt: Depends: libgcc1 (>= 1:4.1.1) but 1:4.5.2-8ubuntu4 is to be installed
                   Depends: libqt4-network (>= 4:4.5.3) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libqt4-opengl (>= 4:4.7.0~rc1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.7.2-0ubuntu6.2 is to be installed
                   Depends: libstdc++6 (>= 4.5) but 4.5.2-8ubuntu4 is to be installed
                   Depends: virtualbox-ose (= 4.0.4-dfsg-1ubuntu4.1) but 4.0.4-dfsg-1ubuntu4.1 is to be installed

```I am on a nearly clean install of Ubuntu 11.04 64-bit. When I saw this, I tried running an apt-get update and then installing, but no dice. any idea what could be causing these weird dependency errors? According to this, I actually have everything I need! There was some more text on the error dialog, so I have attached a screenshot. Any ideas?

---

### Post by varunendra on 2011-09-19
Which package did you select to install? Make sure all the repositories are selected in Settings > Repositories in Synaptic.

Alternatively, you can either download ind install the deb package directly or even better, choose to add a repository from [virtualbox]("http://www.virtualbox.org/wiki/Linux_Downloads")'s website and then install virtualbox instead of virtualbox-ose.

---

### Post by dstrout on 2011-09-19
After some further investigation, it turned out the problem was with the package "libqtgui4". This was a requirement to install VirtualBox (all editions: OSE, the VirtualBox repo, and the VirtualBox website .deb). However, some of the dependencies of libqtgui4 could not be found. I had to manually download and install libvncserver0, libdbusmenu-qt2, appmenu-qt, libmng1, and libaudio2 from packages.ubuntu.com. I don't know if all these packages were in some repo that I didn't have enabled, but once I manually installed them I was able to install VirtualBox. I guess this is solved now, but if anyone knows if there is a repo I should have installed the above packages from, let me know so I can keep everything up to date.

---

### Post by varunendra on 2011-09-20
I have seen a few threads recently where installing google-earth or a third party software created their own versions of libqtgui4 and configured all the aliases/symbolic links to that version so that even though the original liqtgui4 was there, all the calls to it were directed to the other version which other applications that depend upon libqtgui4 did not accept. VLC and VirtualBox are two of many such apps.

One solution was to simply uninstall google-chrome or the other problematic software. But I could not figure out how to fix it while keeping them. Those cases were  different to yours in at least one aspect that even manually reinstalling the required packages did not help while in your case it did.

Here's the link to the thread where I first encountered this issue: [http://ubuntuforums.org/showthread.php?t=1733161](http://ubuntuforums.org/showthread.php?t=1733161)

And by the way, libqtgui4 and its dependencies are already parts of Ubuntu's official repository. So if yours is a similar case of such any culprit application, then I don't think adding any other repository would help.

---

