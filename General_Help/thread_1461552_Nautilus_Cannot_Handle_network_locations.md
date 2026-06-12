---
title: "Nautilus Cannot Handle network locations?"
date: 2010-04-24
forum: General Help
---

### Post by Shadow12313 on 2010-04-24
I am trying to view a share I have on a windows computer but nautilus claims it can't handle that.  I tried it in dolphin and found the file but when I tried to open it gedit claims it cannot handle smb locations either!

Any help would be greatly appreciated.

---

### Post by Shadow12313 on 2010-04-24
UPDATE: I got open office to open the file but, why can't gedit, and why can't nautilus handle network locations.

Maybe KDE is just better than gnome :/

---

### Post by Jim.Crutchfield on 2010-10-01
I'm having the same problem, using Ubuntu 10.04.  Other threads tell me to install gvfs-backends, but it's already installed.  I reinstalled it with Synaptic, but it didn't change anything.  Any other suggestions?

---

### Post by Jim.Crutchfield on 2010-10-01
I just realized that I only have this problem when I start Nautilus as root.

I followed the instructions at [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/) and set up Samba users for my regular login name and for root, and I can browse the network fine using my regular username; but I still get the error when I'm trying to browse as root.

What am I missing?

Thanks for any help.

---

### Post by Darkness Des on 2010-10-01
You don't have it set up as root, only for your username. And browsing as root is NOT recommended. At anytime.

Edit:

Yeah, okay, ignore what I just said. Remember, kids: READ BEFORE YOU POST!

---

### Post by Jim.Crutchfield on 2010-10-01
> **Darkness Des said:**
> You don't have it set up as root, only for your username. And browsing as root is NOT recommended. At anytime.

Edit:

Yeah, okay, ignore what I just said. Remember, kids: READ BEFORE YOU POST!

Thanks for responding, but not sure what you're telling me.  I wanted to browse the network as root because I thought that might let me move some files from my Windows machine to my Linux machine, which Nautilus wasn't letting me do as me.

---

### Post by spcwingo on 2010-10-01
Do you have samba, smbclient, and smbfs installed?  I'm not sure if all of those are necessary, but you could start there to see how it goes.

---

### Post by dcstar on 2010-10-02
Try this as a Launcher command:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

BTW, installing the **nautilus-gksu** package works ok too, and you may need all the **gvfs** packages installed.

---

### Post by LanoxxthShaddow on 2010-11-27
[edit] reopend a new thread

---

### Post by techknowledge on 2012-01-16
> **Darkness Des said:**
> You don't have it set up as root, only for your username. And browsing as root is NOT recommended. At anytime.

Edit:

Yeah, okay, ignore what I just said. Remember, kids: READ BEFORE YOU POST!


I have read this and it all made sense now as to how I could solve my "nautilus cannot handle network" problem
 instead of calling to [COLOR="Red"]gksudo nautilus "network:///"[/COLOR]
fixed issue by calling nautilus [COLOR="Lime"]"network:///"[/COLOR]
via [COLOR="DarkOrange"]terminal[/COLOR]/[COLOR="DarkOrange"]run application[/COLOR] in [COLOR="Lime"]Ubuntu 32-Bit Desktop Edition 11.04 Natty Narwhal, Ubuntu 32-Bit Desktop Edition 10.04 Lucid  and Ubuntu 32-Bit Desktop Edition 11.10 Oneiric Ocelot [/COLOR]

I'm still noobish to these bloggings/Q&A forums but I believe I could be a great help to the community,
                                        [COLOR="DarkRed"]Tech-Knowledge-E[/COLOR].
[COLOR="Green"](Health+Knowledge=Wealth)[/COLOR]

---

### Post by coffeecat on 2012-01-18
Old thread.

Closed.

---

