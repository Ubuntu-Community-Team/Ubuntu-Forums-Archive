---
title: "Unity not starting after upgrade"
date: 2011-05-31
forum: General Help
---

### Post by simon303 on 2011-05-31
I ran update-manager earlier today and when I next booted I was told I had insufficient hardware to run unity -- despite it running just fine before the update.  Now every time I boot I don't get the message, but it still won't run unity.

I have tried running /usr/lib/nux/unity_support_test -p to see what the problem is and get the following:

```

simon@simon-desktop:~$ /usr/lib/nux/unity_support_test -p
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  138 (NV-GLX)
  Minor opcode of failed request:  4 ()
  Resource id in failed request:  0x1ff
  Serial number of failed request:  32
  Current serial number in output stream:  32
simon@simon-desktop:~$ 

```

I'm running 11.04 64bit with the Nvidia 270.41.06 driver (required to get my GeForce 560Ti working)

Here is a list of everything that was updated, but I think most of them shouldn't affect this.

[LIST]
[*]libpam0g
[*]libpam-modules-bin
[*]libpam-modules
[*]libpam-runtime
[*]dnsutils
[*]bind9-host
[*]libisc62
[*]libdns69
[*]libisccc60
[*]libisccfg62
[*]liblwres60
[*]libbind9-60
[*]gnome-nettool
[*]xserver-common
[*]xserver-xorg-core
[/LIST]

I have tried downgrading them by forcing versions in synaptic but I keeps on wanting to remove large numbers of other packages that depend on them.

---

### Post by DinoT1985 on 2011-05-31
if you re-login does Unity work? if so, you need to alter your dmrc file. GDM isn't remembering your settings.

```
sudo gedit /var/cache/gdm/[USER]/dmrc
```and edit Session=gnome to Session=ubuntu.

Do the same for /home/USER/.dmrc

then restart.

---

### Post by simon303 on 2011-05-31
I have tried logging out and then back in, but it still logs in as if classic was selected.

In both of those files Session=une.

What concerns me is /usr/lib/nux/unity_support_test -p used to pass all tests, now it doesn't.

---

### Post by crispy010 on 2011-06-01
Joined the forum to say that I'm having the exact same problem as the OP.  Did an update last night, booted this morning and unity wouldn't start.  At first I thought it had been removed, but after resetting gnome I got a popup that said my hardware couldn't run it.

When I run "/usr/lib/nux/unity_support_test -p" I get the same error, too.  I'm on a Nvidia gtx 260.

I'm reinstalling nvidia's driver and software now, we'll see if it fixes anything.

---

### Post by crispy010 on 2011-06-01
Reinstalling nvidia's xserver app seems to have fixed things.

---

### Post by simon303 on 2011-06-02
I have found that reinstalling the drivers fixed the issue too.  Reverting the packages had no effect so it seems some part of the graphics card drivers is broken as part of the upgrade.

---

