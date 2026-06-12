---
title: "Ubuntu Software Center stopped working, need help troubleshooting"
date: 2010-06-21
forum: General Help
---

### Post by Kurtosis on 2010-06-21
Hi all, I just installed 10.04, then went through Software Center installing a bunch of stuff.

Around the point where I got to Winefish, the installation failed, everything hung, I had to click the red X on the remaining installations, and exit USC.

Now USC doesn't work.  I can start it up, but when I click Install on any app, nothing happens.  The Install button greys out for a second or two, then return to normal.  No su password box, no installation.

When Winefish failed, a crash report notification appeared in the menu bar, so I filed with Launchpad - basically tex-common package failed to install, and that's a Winefish dependency.  I've since used Synaptic to 'Completely Remove' Winefish and all its dependencies.

But USC still doesn't work.  Any idea what's breaking it?

PS - Synaptic and apt-get both work fine.

---

### Post by Smart Viking on 2010-06-21
Hi first try this:

```
gksudo software-center
```This should launch ubuntu software center with the superuser.

If that doeant work, lets try to reinstall software center:

```
sudo apt-get remove software-center
```The above will remove, the next will install it again:

```
sudo apt-get install software-center
```

I just entered all the above commands myself, so it is seems to be safe. :)

EDIT: You will not lose your installed software, onle software-center for a little while. :)

---

### Post by Kurtosis on 2010-06-21
Thanks Viking.  Since posting that, I installed Adobe Air 2 using Adobe's [knowledge base article]("http://kb2.adobe.com/cps/521/cpsid_52132.html#ins_air2_64bit_ubuntu904") on how to install 32bit Air on 64bit Linux systems.

It works, and I installed a few Air applications (Tweetdeck, OptionsXpress Xtend, StockTwits, Shufflr) and have been running them this morning with no problems.  

However, now the package system thinks the Software Index is broken, specifically references those four Air applications, wants to fix them, and won't do anything else until they're fixed.

[IMG]http://imgur.com/KT5OE.png[/IMG]
[IMG]http://imgur.com/6ByUt.png[/IMG]

All four of those Air apps were installed /opt, fwiw.  

Looks like I've gotta fix this first b/f I can try your suggestions.  However I don't really understand what is going on here.  What exactly does the package manager mean by 'fix' these broken dependencies?  Delete them, or something else?

---

### Post by Smart Viking on 2010-06-21
I am quoting from the man pages of "apt-get", i cant know if it will remove your packages or not to run "sudo apt-get install -f", you will have to judge yourself. or someone else who knows more.

```
     -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.

```

I hope this helps a little. :)

---

### Post by Kurtosis on 2010-06-22
Thanks Smart, I went ahead and ran the 'Fix Broken' in Synaptic, which removed all the Adobe Air apps but at least solved all the problems.  USC worked again.  At least until it hung trying to install Audacity.  

I just don't think I'm going to bother with USC anymore.  It seems unreliable, prone to failure, and not very good about giving informative error messages that help you find and fix or avoid the problem.

---

