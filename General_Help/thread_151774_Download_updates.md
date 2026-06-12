---
title: "Download updates"
date: 2006-03-28
forum: General Help
---

### Post by secular on 2006-03-28
I have a little lab of 15 or so computers running Breezy, and they're identical models.

Is there a way download all updates to a network folder and then update from there?

My problem is that the network is spotty at times, and updating them all can be quite a pain.

I've searched the forum, but either there is nothing here or I used the wrong search terms.

Thanks.

---

### Post by endersshadow on 2006-03-28
[QUOTE=secular]I have a little lab of 15 or so computers running Breezy, and they're identical models.

Is there a way download all updates to a network folder and then update from there?

My problem is that the network is spotty at times, and updating them all can be quite a pain.

I've searched the forum, but either there is nothing here or I used the wrong search terms.

Thanks.[/QUOTE]

Sure, you can do:

```
sudo apt-get -d install package_to_install
```

The debs will be located in /var/cache/apt/archives.  Extract those that you want, and burn them to a disc, bring it to a computer, copy them over, and then run:

```
sudo dpkg -i *
```

Then, if you want, you can delete the files.  If you don't want to save the debs on the system, you may be able to do the dkpg -i straight from the cdrom.

---

### Post by az on 2006-03-28
You can use apt-move to create a local repository.  Make an entry in the the networked machines to look for updates on the local server, and not on the ubuntu servers.  Anything you put into your local repo will get installed if you allow for automatic updates.

Easy, huh?

---

### Post by secular on 2006-03-28
So, azz, if my Samba server is smb://abc/smiley, for example, and my updates were in smb://abc/smiley/updates, would I type the following?

```
apt-move smb://abc/smiley/updates
```

If not, what would the exact command be?

Thanks.

---

