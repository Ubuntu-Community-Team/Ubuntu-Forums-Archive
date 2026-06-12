---
title: "Cryptkeeper does not work under 12.04"
date: 2012-08-17
forum: General Help
---

### Post by MatsSoderhall on 2012-08-17
I just installed cryptkeeper from Ubuntu Software Center.

When starting the program the icon does not appear in the tray.
I can see the process in the process viewer. If i start the program from a terminal window i get no error message.

Some forums recommend the following string:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']"
```
But it does not help me....

Anyone have solved this?

---

### Post by cryptotheslow on 2012-08-17
I believe you use dconf rather than gconf.

Cryptkeeper works fine for me this way....

Install Dconf Editor from the software centre (or Synaptic Package Manager), fire it up and navigate to:

desktop > unity > panel

And edit the systray-whitelist entry to include "cryptkeeper" or "all".

Currently mine contains this:
```
['JavaEmbeddedFrame', 'Wine', 'scp-dbus-service', 'Update-notifier', 'truecrypt', 'xchat', 'cryptkeeper']
```

---

### Post by Cushie on 2012-09-18
I followed the above directions and my system is configured similar in 12.04, but I can't get access the the encrypted folder. I have tried several times to certify I know the password, each time I get the error
 'the stash (folder?) could not be mounted, invalid password'. and can't get round this or get my files back!
I have checked my user name in 'fuse' group as suggested elsewhere.

Have you any suggestion to help me out?

---

### Post by guyaloni on 2012-12-31
I also followed these steps carefully, after i saw that in several places different people recommend the same process.

However, **for me it doesn't work neither.**

I have the icons of Skype and DropBox on the right side of the top-bar, and I added 'Cryptkeeper' to the white-list as mentioned.

When I launch Cryptkeeper I can see it in the System Monitor but the icon does not appear.

Any help please???

---

