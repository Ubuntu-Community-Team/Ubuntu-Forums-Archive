---
title: "Filezilla Freezes downloading to a file server"
date: 2011-10-25
forum: General Help
---

### Post by steveodeevo on 2011-10-25
Hello,

For a while now I have been experiencing freezes in filezilla on ubuntu when downloading websites via FTP, it seems that for some reason it will do so many files and then just go grey for a few seconds before carrying on.

Now my PC isn't an issue as its a hex core 4gb 1TB HDD beast, however I am thinking my setup might be, I have a firewall box running on an AMD64 4200 dual core 4GB 1TB HDD setup which doubles as a fileserver.

Both PCs run ubuntu linux, one is on 10.04 and the other is on 11.10, however this problem has been bugging me for a while since before version 10.

My firewall box is running Firestarter which doubles up as firewall and internet share to the rest of the network.

My main workstation PC connects to this using CIFS shares, setup in my FSTAB, and mounted on startup, mainly to enable programs such as eclipse IDE to work over the network.

An example of my share setup in the fstab is below
```

//192.168.2.5/www  /media/server  cifs  username=username,password=password  0  0

```So my line of thinking is that either my shares setup is timing out somehow and causing this freeze, or somehow my firewall setup is doing it?

Anyone got any ideas?

---

