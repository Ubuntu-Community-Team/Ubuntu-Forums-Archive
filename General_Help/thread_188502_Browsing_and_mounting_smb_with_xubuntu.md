---
title: "Browsing and mounting smb with xubuntu"
date: 2006-06-04
forum: General Help
---

### Post by moopere on 2006-06-04
Hi Folks,

This problem has been driving me nuts for months now.  I've tried everything there is to try...or so it seems :D, linneighborhood, jags, xsmbrowser, etc etc etc.

If you use Kubuntu you will be smiling at me right now because in kde land there is the excellent smb4k which can even talk CIFS and works really really well (browse all smb groups, find what you want mount it with individual user/pass per share if you want).

Now, I would just use smb4k in xubuntu land if it didn't drag in 150MB of KDE with it (!!), its pretty integrated into kde and doesn't appear to work all that well outside of the KDE DE (uses kde wallet etc).

I've tried xffm, it causes a bunch of pretty useless junk to appear in your menu system - this aside though it does a reasonable job of surfing the shares on your network (though not w2k3 server - need CIFS for that) but I can't find a GUI way to mount anything from xffm.

In surfing around ubuntuforums it really appears that serious samba ppl are still mouting their shares by hand (command line) - surely this is not our only choice in 2006?

So, what are we all using to browse samba networks and talk to win2K and 2k3 server shares?

Cheers,
Craig

---

### Post by givré on 2006-06-04
Configuring by hand your /etc/samba/smb.conf is i think the only way in ubuntu and xubuntu for the moment. I hope it will be change in the following release.

---

### Post by moopere on 2006-06-04
[QUOTE=givré]Configuring by hand your /etc/samba/smb.conf is i think the only way in ubuntu and xubuntu for the moment. I hope it will be change in the following release.[/QUOTE]

Swat works for configuring samba, or did last time I tried it (Dapper RC) after having been broken for a long time during the dapper test cycle.  I can deal pretty well with configuring the local machines.  

What drives me crazy though is having to stuff around during the 'using' of network resources via samba.  Windows OS's have done this as easy as pie since at least 1994 (NT4), I can't believe we're still doing this stuff by hand in 2006 on anything that isn't KDE.

I'm a network admin, so spend a lot of my time dealing with connectivity things that maybe others don't cause I don't hear a lot of screaming about this in ubuntu land.  

Whilst I _can_ config all this stuff in fstab or by scripts hanging off buttons on the panel, (my) users just hate this sort of stuff and frankly so do I, theres an easier way...browse then mount/unmount, KDE does it, MACOS/OSX does it, Windows since NT4 (at least) has done it.

Arrgghhh.  I'm off to freshmeat.net to see if I can't learn python and fix one of the broken pygtk apps over there :mrgreen: 

Cheers,
Craig

---

### Post by TuxCrafter on 2006-07-05
I also have xubuntu installed on some clients pc's. I use the command line to mount network shares and then browse them with lunar (I think I spell that wrong)

I have not jet found a good solution using smb shares on linux. Even the command line cifs mount are not bug free or save. (lost some document, linux did not do a buffer check on the share)

---

### Post by foxy123 on 2006-07-06
xffm has a samba plugin which allows you to mount samba shares with right-click. It used to work for me when I was compiling xfce from svn. But now I use xffm from repository and for some reason it does not mount samba shares. I have not looked into it though.

EDIT: well it works fine on my Desktop but not on the laptop. If you open xffm you'll see SMB Network, which is xfsamba4 browser. Go in there, right-click on your share and choose Mount. It will ask you for your user name and password. You can then put it in xffm preferences to avoid entering it every time. xfsamba4 will create a directory in your /tmp and mount your samba share there.

---

