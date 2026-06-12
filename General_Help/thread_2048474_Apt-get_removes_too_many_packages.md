---
title: "Apt-get removes too many packages"
date: 2012-08-26
forum: General Help
---

### Post by Statia on 2012-08-26
Since my serial port does not work I can't get my IR-receiver to work, so I am going to uninstall lirc and related packages from my system. When I try to remove liblircclient0, I get this:

```
$ sudo apt-get remove liblircclient0
.....
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libg15daemon-client1 libxosd2 libg15render1 lcdproc
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acidrip electricsheep gxine lcdproc-extra-drivers liblircclient0 mencoder
  mplayer mplayer-fonts mplayerthumbs smplayer smplayer-themes
  smplayer-translations vlc vlc-nox vlc-plugin-notify vlc-plugin-pulse xine-ui
0 upgraded, 0 newly installed, 17 to remove and 0 not upgraded.
After this operation, 48.4 MB disk space will be freed.
Do you want to continue [Y/n]? 
```Why would all my mediaplayers be removed when I only want to remove one library related to remote control? These mediaplayers functioned before I installed lirc and liblircclient0 and I am sure they will keep functioning once liblircclient0 is removed.
And why is lcdproc going to be removed? What has lcdproc got to do with lirc? I only recently installed it and I still need it because I got a LCD screen.
Clearly this must be some bug, or even worse a conceptual error in apt-get?
And how can I remove liblircclient0 without it taking my mediaplayers that I still wish to use?

---

### Post by Cavsfan on 2012-08-26
If you look in Synaptic, those are all dependent on that file. Why do you wish to remove it?

---

### Post by Statia on 2012-08-27
> **Cavsfan said:**
> If you look in Synaptic, those are all dependent on that file. Why do you wish to remove it?

I don't think they are all dependent on that file, I think that is where the dependencies are wrong.

This is what happened:

1. Try to get lirc to work, install lirc and liblircclient0.
2. Can't get lirc to work, decide to put an LCD on the serial port instead, so:
3. Install lcdproc and lcdproc-extradrivers.
4. Don't need lirc and liblircclient0 anymore so try to uninstall:
5. apt-get tells me it will uninstall lcdproc-extradrivers and lcdproc is no longer necessary.

This can't be right. I still want to use lcdproc and I don't need lirc or liblircclient0 to use lcdproc.

---

### Post by mc4man on 2012-08-27
gxine, mplayer, vlc-nox, xine-ui & lcdproc-extra-drivers all have a dep on liblircclient0. When you installed any of them liblircclient0 would have been installed if not already. (if you think differently then you're simply mistaken

The rest of the packages being removed have a dep on one of the above.
lcdproc was auto installed when   lcdproc-extra-drivers was installed so it is now seen as "no longer required"

---

### Post by Statia on 2012-08-27
> **mc4man said:**
> gxine, mplayer, vlc-nox, xine-ui & lcdproc-extra-drivers all have a dep on liblircclient0. When you installed any of them liblircclient0 would have been installed if not already. (if you think differently then you're simply mistaken

The rest of the packages being removed have a dep on one of the above.
lcdproc was auto installed when   lcdproc-extra-drivers was installed so it is now seen as "no longer required"

OK, I accept that liblircclient0 comes with the mediaplayers and not with lirc, but I installed lcdproc after the mediaplayers and after lirc and I am still using lcdproc. If the lcdproc-extradrivers has lirc drivers, I understand that that can go as well. But apt-get also says lcdproc is not necessary any more. That is just plain wrong, that would mean that whenever I would do an `apt-get autoremove` my LCD would stop working.

---

### Post by mc4man on 2012-08-27
You can mark packages that are "auto installed" as manually installed in synaptic. Then they won't show as 'auto removable' when the package they were installed because of is removed

Do to so search the package, highlight it, then under the package tab uncheck  "Automatically Installed"
see screen, if I click on highlighted, (removing the checkmark), it will then be seen as manually installed

Edit: when in synaptic you could under the 'Status' section > Installed (auto... see all auto marked packages &  remark as seen fit.
screen 2

---

### Post by Statia on 2012-08-27
> **mc4man said:**
> You can mark packages that are "auto installed" as manually installed in synaptic. Then they won't show as 'auto removable' when the package they were installed because of is removed

Do to so search the package, highlight it, then under the package tab uncheck  "Automatically Installed"
see screen, if I click on highlighted, (removing the checkmark), it will then be seen as manually installed

Thanks! I guess I should get me synaptic. When I know the name of a package I use apt-get, when I am searching I use Muon, as I it comes with Kubuntu.

---

### Post by mc4man on 2012-08-27
synaptic is quite useful, never used kubuntu much, when I did several yr.'s ago did install synaptic vs. whatever was default supplied which drove me crazy
(ck. edit to previous

---

### Post by cortman on 2012-08-27
You can do this in the CLI as well, with apt-mark:

```
sudo apt-mark manual package_name
```

---

### Post by Statia on 2012-09-05
I guess I have neglected to thank everyone so far, so here goes:

Thanks a lot!

---

### Post by Cavsfan on 2012-09-05
deleted

---

