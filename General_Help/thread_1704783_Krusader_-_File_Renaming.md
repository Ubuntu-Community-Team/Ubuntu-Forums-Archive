---
title: "Krusader - File Renaming"
date: 2011-03-11
forum: General Help
---

### Post by indytim on 2011-03-11
My working filemanager is Krusader.  I've been running it for several years quite successfully in the Gnome environment ( Ubuntu & Mint ).  With the recent build of Mint 10 (Ubuntu 10.10) I lost the ability to rename files in Krusader.  I did a posting on the Krusader boards but it seems they've gone semi-dark.

I suspect I'm missing a library.  Would appreciate any help in identifying the offending (or missing) library.

Please withhold any responses to move to other filemanagers.

TIA,

IndyTim / DataMan

---

### Post by nomko on 2011-03-11
> **indytim said:**
> My working filemanager is Krusader. I've been running it for several years quite successfully in the Gnome environment ( Ubuntu & Mint ). With the recent build of Mint 10 (Ubuntu 10.10) I lost the ability to rename files in Krusader. I did a posting on the Krusader boards but it seems they've gone semi-dark.
 
I suspect I'm missing a library. Would appreciate any help in identifying the offending (or missing) library.
 
Please withhold any responses to move to other filemanagers.
 
TIA,
 
IndyTim / DataMan
 
For Linux Mint related issues it's better to go to the Linux Mint forum: [http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by kellemes on 2011-03-11
> **indytim said:**
> My working filemanager is Krusader.  I've been running it for several years quite successfully in the Gnome environment ( Ubuntu & Mint ).  With the recent build of Mint 10 (Ubuntu 10.10) I lost the ability to rename files in Krusader.  I did a posting on the Krusader boards but it seems they've gone semi-dark.

I suspect I'm missing a library.  Would appreciate any help in identifying the offending (or missing) library.

Please withhold any responses to move to other filemanagers.

TIA,

IndyTim / DataMan

Also using Krusader myself, never found anything better..

Anyway, can you please describe how it's not working?
You can right-click -> rename? What's exactly not working?

---

### Post by indytim on 2011-03-11
rename both right click as well as <f9> (I think <f9> - duty bound on Windows at the moment).

Tx,

IndyTim / DataMan

---

### Post by Yellow Pasque on 2011-03-11
If you start krusader from the terminal, does it give any error messages when you try to rename?

---

### Post by kellemes on 2011-03-11
> **indytim said:**
> rename both right click as well as <f9> (I think <f9> - duty bound on Windows at the moment).

Tx,

IndyTim / DataMan

f9 may be default, don't know.. I have different keybindings..
I don't have a rename-app. (like krename) installed for Krusader and it works fine..
Still you may install krename, enter path in Krusader ->  Settings -> Configure Krusader -> Dependencies -> krename.. and see if it works.

---

### Post by indytim on 2011-03-12
krename is installed and I've got it configured within krusader to point to
```

/usr/bin/krename

```

What's got me frazzled is that Krusader permits the rename (no errors), it just isn't sticking.

Also tried running it straight from the terminal with same results.

TX,

IndyTim / DataMan

---

### Post by kellemes on 2011-03-12
Don't get it :confused:
Google and also Krusader's Forum and Bugtracker aren't really helpful in this matter..

I know it sucks but have you tried removing (or renaming) the configuration-files/folders of Krusader, see if that fixes this?
[locations]("http://www.krusader.org/handbook/config_files.html")

Else.. Remove/purge and reinstall.

If that doesn't work you can assume there is something wrong with this build.. I guess..
Personally I'm on Arch using Krusader Version 2.3.0-beta1 "New Horizons" and have no issues..
Maybe you can try to upgrade your version of Krusader to something newer.

Sorry for having no solution..

---

