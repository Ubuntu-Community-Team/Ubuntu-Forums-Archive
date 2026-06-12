---
title: "wicd not keeping connection"
date: 2011-08-04
forum: General Help
---

### Post by GlorifiedDitchDigger on 2011-08-04
Hi, I'm fairly new to ubuntu and not entirely up to speed on how to best use it (as in go behind the scenes and fix things), so I was wondering if I could find some help here:

I have Wicd Network Manager and I just moved to a house with a WPA-passphrase protected wireless network. I have entered the passphrase into the preferences of Wicd, and when I first turn on my computer it connects to the network just fine.

However, after a certain amount of time it loses the connection; when I try to reconnect (by disconnecting and connecting again), it tells me that the password is bad.

I had a similar issue the past couple weeks while I was travelling and connecting to unsecured networks at hotels - I would be able to connect, but Wicd would lose the connection periodically, without much logic to the times between kick-offs.

I'm able to connect to the internet using a wired connection through Wicd just fine, but I'm concerned over the inability to connect to wireless networks or maintain a connection over a reasonable period of time.

---

### Post by younishd on 2011-08-19
Hi, :)
> Hi, I'm fairly new to ubuntu and not entirely up to speed on how to best use it (as in go behind the scenes and fix things), so I was wondering if I could find some help here:
It's always a good idea to look for help in forums. Most of the time, you'll find an answer to your problems with ubuntu.
> I have Wicd Network Manager

You should probably mention which version of wicd you're using.
> it tells me that the password is bad.

It's a known bug of wicd.
I would suggest you to downgrade to an older version of wicd.
-- You can get older versions from here:
[http://sourceforge.net/projects/wicd/files/wicd-stable/](http://sourceforge.net/projects/wicd/files/wicd-stable/)

-- You can run it with:
```
$ wicd-client
```

-- Launchpad:
[https://bugs.launchpad.net/wicd/+bug/720439](https://bugs.launchpad.net/wicd/+bug/720439)

-- Why not Network Manager ?
[https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)


Keep doing .. ubuntu teaches us to be patient :D


YouniS

---

