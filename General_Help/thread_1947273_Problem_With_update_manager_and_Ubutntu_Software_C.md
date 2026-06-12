---
title: "Problem With update manager and Ubutntu Software Center"
date: 2012-03-26
forum: General Help
---

### Post by Sissy8788 on 2012-03-26
Hello all!I'm new user of Ubuntu and new to this forum,

As the title says I have a problem with update manager and Ubuntu 

software center I tried to add a ppa repository

[HTML]sudo add-apt-repository ppa:webupd8team/unstable[/HTML]

After this command I get:


[HTML]You are about to add the following PPA to your system:
 Unreleased / Git / Backports
 This PPA currently holds unreleased / git builds for different applications like Turpial, mc, Audacious.

PPA for WebUpd8: http://www.webupd8.org


 More info: https://launchpad.net/~webupd8team/+archive/unstable
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.DqJhG0h9d8 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 7B2C3B0889BF5709A105D03AC2518248EEA14886
gpg: requesting key EEA14886 from hkp server keyserver.ubuntu.com
gpg: key EEA14886: "Launchpad VLC" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1[/HTML

But then when I try to update with this command


[HTML]sudo apt-get update[/HTML]

I got this error

[HTML]E: Type 'n' is not known on line 3 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
E: The list of sources could not be read.[/HTML]

And after that Update manager and software center won't work.

When I open the update manager it keeps giving me errors.

What can I do?

Thank you in advance for any help you can provide.

---

### Post by matt_symes on 2012-03-26
Hi

You could just delete the wine ppa but, if you post it back here, we should be able to fix it instead..

From the terminal type

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

Post the output back here between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

EDIT. Seems you can already use code tags.

Kind regards

---

### Post by Sissy8788 on 2012-03-26
> **matt_symes said:**
> Hi

You could just delete the wine ppa but, if you post it back here, we should be able to fix it instead..

From the terminal type

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

Post the output back here between code tags like this

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
n

```

to get output like this

```
output
```

EDIT. Seems you can already use code tags.

Kind regards

Thank you very much for your time and your help,

this is what i get when I enter this command!

Regards :)

---

### Post by Sissy8788 on 2012-03-26
Sorry  for the messes, as I said I'm new! I will fix it!!

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
n

```

This is what I get!Sorry again for the mess!

---

### Post by gsgleason on 2012-03-26
Edit that file and remove the line with the 'n'

---

### Post by Sissy8788 on 2012-03-26
> **gsgleason said:**
> Edit that file and remove the line with the 'n'

I know it will sound stupid but, it's the first time I use Linux.

How can I edit the file?:|

---

### Post by jerome1232 on 2012-03-26
```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

---

### Post by Sissy8788 on 2012-03-26
> **jerome1232 said:**
> ```
gksu gedit /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

Thank you for this, but it still the same and now it gave more errors when I tried to do this command:

```
apt-get update
```

```
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/webupd8team-unstable-oneiric.list
E: The list of sources could not be read.

```

---

### Post by matt_symes on 2012-03-26
Hi

Or a sed one liner to delete the line 3.

```
sudo sed -i 3d /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```

EDIT: Please see next post.

Kind regards

---

### Post by matt_symes on 2012-03-26
Hi 

> webupd8team-unstable-oneiric.list

You have a problem with another source file. Let's have a look at all of them.

Please post the output of 

```
grep ^ /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by jerome1232 on 2012-03-26
edit: I didn't fully read the post, didn't notice it was another sources.list file.

---

### Post by Sissy8788 on 2012-03-26
> **matt_symes said:**
> Hi 



You have a problem with another source file. Let's have a look at all of them.

Please post the output of 

```
grep ^ /etc/apt/sources.list.d/*
```

Kind regards

Thank you again for your time,this is what I get

```
/etc/apt/sources.list.d/aegirxx-googlemail-gnome-shell-extensions-oneiric.list:deb http://ppa.launchpad.net/aegirxx-googlemail/gnome-shell-extensions/ubuntu oneiric main
/etc/apt/sources.list.d/aegirxx-googlemail-gnome-shell-extensions-oneiric.list:# deb-src http://ppa.launchpad.net/aegirxx-googlemail/gnome-shell-extensions/ubuntu oneiric main
/etc/apt/sources.list.d/aegirxx-googlemail-gnome-shell-extensions-oneiric.list.save:deb http://ppa.launchpad.net/aegirxx-googlemail/gnome-shell-extensions/ubuntu oneiric main
/etc/apt/sources.list.d/aegirxx-googlemail-gnome-shell-extensions-oneiric.list.save:# deb-src http://ppa.launchpad.net/aegirxx-googlemail/gnome-shell-extensions/ubuntu oneiric main
/etc/apt/sources.list.d/ayatana-scrollbar-team-release-oneiric.list:deb http://ppa.launchpad.net/ayatana-scrollbar-team/release/ubuntu oneiric main
/etc/apt/sources.list.d/ayatana-scrollbar-team-release-oneiric.list:# deb-src http://ppa.launchpad.net/ayatana-scrollbar-team/release/ubuntu oneiric main
/etc/apt/sources.list.d/ayatana-scrollbar-team-release-oneiric.list.save:deb http://ppa.launchpad.net/ayatana-scrollbar-team/release/ubuntu oneiric main
/etc/apt/sources.list.d/ayatana-scrollbar-team-release-oneiric.list.save:# deb-src http://ppa.launchpad.net/ayatana-scrollbar-team/release/ubuntu oneiric main
/etc/apt/sources.list.d/cardapio-team-unstable-oneiric.list:deb http://ppa.launchpad.net/cardapio-team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/cardapio-team-unstable-oneiric.list:# deb-src http://ppa.launchpad.net/cardapio-team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/cardapio-team-unstable-oneiric.list.save:deb http://ppa.launchpad.net/cardapio-team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/cardapio-team-unstable-oneiric.list.save:# deb-src http://ppa.launchpad.net/cardapio-team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/conkyhardcore-ppa-oneiric.list:# deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/conkyhardcore-ppa-oneiric.list:# deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/conkyhardcore-ppa-oneiric.list.save:# deb http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/conkyhardcore-ppa-oneiric.list.save:# deb-src http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-ppa-oneiric.list:# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-ppa-oneiric.list:# deb-src http://ppa.launchpad.net/docky-core/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-ppa-oneiric.list.save:# deb http://ppa.launchpad.net/docky-core/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-ppa-oneiric.list.save:# deb-src http://ppa.launchpad.net/docky-core/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-stable-oneiric.list:deb http://ppa.launchpad.net/docky-core/stable/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-stable-oneiric.list:# deb-src http://ppa.launchpad.net/docky-core/stable/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-stable-oneiric.list.save:deb http://ppa.launchpad.net/docky-core/stable/ubuntu oneiric main
/etc/apt/sources.list.d/docky-core-stable-oneiric.list.save:# deb-src http://ppa.launchpad.net/docky-core/stable/ubuntu oneiric main
/etc/apt/sources.list.d/elementaryart-elementary-dev-oneiric.list:deb http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu oneiric main
/etc/apt/sources.list.d/elementaryart-elementary-dev-oneiric.list:# deb-src http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu oneiric main
/etc/apt/sources.list.d/elementaryart-elementary-dev-oneiric.list.save:deb http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu oneiric main
/etc/apt/sources.list.d/elementaryart-elementary-dev-oneiric.list.save:# deb-src http://ppa.launchpad.net/elementaryart/elementary-dev/ubuntu oneiric main
/etc/apt/sources.list.d/emesene-team-emesene-stable-oneiric.list:deb http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu oneiric main
/etc/apt/sources.list.d/emesene-team-emesene-stable-oneiric.list:# deb-src http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu oneiric main
/etc/apt/sources.list.d/emesene-team-emesene-stable-oneiric.list.save:deb http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu oneiric main
/etc/apt/sources.list.d/emesene-team-emesene-stable-oneiric.list.save:# deb-src http://ppa.launchpad.net/emesene-team/emesene-stable/ubuntu oneiric main
/etc/apt/sources.list.d/flozz-flozz-oneiric.list:deb http://ppa.launchpad.net/flozz/flozz/ubuntu oneiric main
/etc/apt/sources.list.d/flozz-flozz-oneiric.list:# deb-src http://ppa.launchpad.net/flozz/flozz/ubuntu oneiric main
/etc/apt/sources.list.d/flozz-flozz-oneiric.list.save:deb http://ppa.launchpad.net/flozz/flozz/ubuntu oneiric main
/etc/apt/sources.list.d/flozz-flozz-oneiric.list.save:# deb-src http://ppa.launchpad.net/flozz/flozz/ubuntu oneiric main
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu oneiric-getdeb apps
/etc/apt/sources.list.d/getdeb.list.save:deb http://archive.getdeb.net/ubuntu oneiric-getdeb apps
/etc/apt/sources.list.d/gloobus-dev-covergloobus-oneiric.list:deb http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-covergloobus-oneiric.list:# deb-src http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-covergloobus-oneiric.list.save:deb http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-covergloobus-oneiric.list.save:# deb-src http://ppa.launchpad.net/gloobus-dev/covergloobus/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-gloobus-preview-oneiric.list:deb http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-gloobus-preview-oneiric.list:# deb-src http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-gloobus-preview-oneiric.list.save:deb http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu oneiric main
/etc/apt/sources.list.d/gloobus-dev-gloobus-preview-oneiric.list.save:# deb-src http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu oneiric main
/etc/apt/sources.list.d/gnome3-team-gnome3-oneiric.list:deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/gnome3-team-gnome3-oneiric.list:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/gnome3-team-gnome3-oneiric.list.save:deb http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/gnome3-team-gnome3-oneiric.list.save:# deb-src http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/google-chrome.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-chrome.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-chrome.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-chrome.list.save:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/google-talkplugin.list.save:### THIS FILE IS AUTOMATICALLY CONFIGURED ###
/etc/apt/sources.list.d/google-talkplugin.list.save:# You may comment out this entry, but any other modifications may be lost.
/etc/apt/sources.list.d/google-talkplugin.list.save:deb http://dl.google.com/linux/talkplugin/deb/ stable main
/etc/apt/sources.list.d/inameiname-stable-oneiric.list.save:deb http://ppa.launchpad.net/inameiname/stable/ubuntu oneiric main
/etc/apt/sources.list.d/janvitus-gnomestracciatella-oneiric.list.save:# deb-src http://ppa.launchpad.net/janvitus/gnomestracciatella/ubuntu oneiric main
/etc/apt/sources.list.d/jconti-gnome3-oneiric.list:deb http://ppa.launchpad.net/jconti/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/jconti-gnome3-oneiric.list:# deb-src http://ppa.launchpad.net/jconti/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/jconti-gnome3-oneiric.list.save:deb http://ppa.launchpad.net/jconti/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/jconti-gnome3-oneiric.list.save:# deb-src http://ppa.launchpad.net/jconti/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/lars-opdenkamp-pvr-depends-oneiric.list~:ain
/etc/apt/sources.list.d/leolik-leolik-oneiric.list:deb http://ppa.launchpad.net/leolik/leolik/ubuntu oneiric main
/etc/apt/sources.list.d/leolik-leolik-oneiric.list:# deb-src http://ppa.launchpad.net/leolik/leolik/ubuntu oneiric main
/etc/apt/sources.list.d/leolik-leolik-oneiric.list.save:deb http://ppa.launchpad.net/leolik/leolik/ubuntu oneiric main
/etc/apt/sources.list.d/leolik-leolik-oneiric.list.save:# deb-src http://ppa.launchpad.net/leolik/leolik/ubuntu oneiric main
/etc/apt/sources.list.d/liquorix.list:# deb http://liquorix.net/debian sid main
/etc/apt/sources.list.d/liquorix.list:# deb-src http://liquorix.net/debian sid main
/etc/apt/sources.list.d/liquorix.list.save:# deb http://liquorix.net/debian sid main
/etc/apt/sources.list.d/liquorix.list.save:# deb-src http://liquorix.net/debian sid main
/etc/apt/sources.list.d/me-davidsansome-clementine-dev-oneiric.list:deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu oneiric main
/etc/apt/sources.list.d/me-davidsansome-clementine-dev-oneiric.list:# deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu oneiric main
/etc/apt/sources.list.d/me-davidsansome-clementine-dev-oneiric.list.save:deb http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu oneiric main
/etc/apt/sources.list.d/me-davidsansome-clementine-dev-oneiric.list.save:# deb-src http://ppa.launchpad.net/me-davidsansome/clementine-dev/ubuntu oneiric main
/etc/apt/sources.list.d/medibuntu.list:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list:deb http://packages.medibuntu.org/ oneiric free non-free #Medibuntu - Ubuntu 11.10 "oneiric ocelot"
/etc/apt/sources.list.d/medibuntu.list:# deb-src http://packages.medibuntu.org/ oneiric free non-free #Medibuntu (source) - Ubuntu 11.10 "oneiric ocelot"
/etc/apt/sources.list.d/medibuntu.list.save:## Please report any bug on https://bugs.launchpad.net/medibuntu/
/etc/apt/sources.list.d/medibuntu.list.save:deb http://packages.medibuntu.org/ oneiric free non-free #Medibuntu - Ubuntu 11.10 "oneiric ocelot"
/etc/apt/sources.list.d/medibuntu.list.save:# deb-src http://packages.medibuntu.org/ oneiric free non-free #Medibuntu (source) - Ubuntu 11.10 "oneiric ocelot"
/etc/apt/sources.list.d/miserware.list:# deb https://download.miserware.com/linux/deb oneiric main
/etc/apt/sources.list.d/miserware.list.save:# deb https://download.miserware.com/linux/deb oneiric main
/etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu oneiric main
/etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu oneiric main
/etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list.save:deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu oneiric main
/etc/apt/sources.list.d/nilarimogard-webupd8-oneiric.list.save:# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu oneiric main
/etc/apt/sources.list.d/n-muench-vlc-oneiric.list:deb http://ppa.launchpad.net/n-muench/vlc/ubuntu oneiric main
/etc/apt/sources.list.d/n-muench-vlc-oneiric.list:deb-src http://ppa.launchpad.net/n-muench/vlc/ubuntu oneiric main
/etc/apt/sources.list.d/n-muench-vlc-oneiric.list.save:deb http://ppa.launchpad.net/n-muench/vlc/ubuntu oneiric main
/etc/apt/sources.list.d/n-muench-vlc-oneiric.list.save:deb-src http://ppa.launchpad.net/n-muench/vlc/ubuntu oneiric main
/etc/apt/sources.list.d/panthora-coverchooser-ppa-oneiric.list:deb http://ppa.launchpad.net/panthora/coverchooser-ppa/ubuntu oneiric main
/etc/apt/sources.list.d/panthora-coverchooser-ppa-oneiric.list:# deb-src http://ppa.launchpad.net/panthora/coverchooser-ppa/ubuntu oneiric main
/etc/apt/sources.list.d/panthora-coverchooser-ppa-oneiric.list.save:deb http://ppa.launchpad.net/panthora/coverchooser-ppa/ubuntu oneiric main
/etc/apt/sources.list.d/panthora-coverchooser-ppa-oneiric.list.save:# deb-src http://ppa.launchpad.net/panthora/coverchooser-ppa/ubuntu oneiric main
/etc/apt/sources.list.d/pinta-maintainers-pinta-stable-oneiric.list:deb http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu oneiric main
/etc/apt/sources.list.d/pinta-maintainers-pinta-stable-oneiric.list:# deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu oneiric main
/etc/apt/sources.list.d/pinta-maintainers-pinta-stable-oneiric.list.save:deb http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu oneiric main
/etc/apt/sources.list.d/pinta-maintainers-pinta-stable-oneiric.list.save:# deb-src http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu oneiric main
/etc/apt/sources.list.d/playdeb.list:deb http://archive.getdeb.net/ubuntu oneiric-getdeb games
/etc/apt/sources.list.d/playdeb.list.save:deb http://archive.getdeb.net/ubuntu oneiric-getdeb games
/etc/apt/sources.list.d/playonlinux.list:deb http://deb.playonlinux.com/ oneiric main
/etc/apt/sources.list.d/playonlinux.list.save:deb http://deb.playonlinux.com/ oneiric main
/etc/apt/sources.list.d/pmcenery-ppa-oneiric.list.save:#deb-src http://ppa.launchpad.net/pmcenery/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ppa-gnomeshell-meta.list.save:#deb-src http://ppa.launchpad.net/jan-hoffmann/gnome-shell/ubuntu oneiric main
/etc/apt/sources.list.d/shnatsel-zram-oneiric.list:deb http://ppa.launchpad.net/shnatsel/zram/ubuntu oneiric main
/etc/apt/sources.list.d/shnatsel-zram-oneiric.list:# deb-src http://ppa.launchpad.net/shnatsel/zram/ubuntu oneiric main
/etc/apt/sources.list.d/shnatsel-zram-oneiric.list.save:deb http://ppa.launchpad.net/shnatsel/zram/ubuntu oneiric main
/etc/apt/sources.list.d/shnatsel-zram-oneiric.list.save:# deb-src http://ppa.launchpad.net/shnatsel/zram/ubuntu oneiric main
/etc/apt/sources.list.d/sources.list:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:# newer versions of the distribution.
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list.d/sources.list:## distribution.
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list.d/sources.list:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list.d/sources.list:## review or updates from the Ubuntu security team.
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list.d/sources.list:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list.d/sources.list:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list.d/sources.list:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list.d/sources.list:## security team.
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list.d/sources.list:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list.d/sources.list:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list.d/sources.list:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list.d/sources.list:## or updates from the Ubuntu security team.
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list.d/sources.list:## 'partner' repository.
/etc/apt/sources.list.d/sources.list:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list.d/sources.list:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:## Uncomment the following two lines to add software from Ubuntu's
/etc/apt/sources.list.d/sources.list:## 'extras' repository.
/etc/apt/sources.list.d/sources.list:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list.d/sources.list:## developers who want to ship their latest software.
/etc/apt/sources.list.d/sources.list:deb http://packages.linuxmint.com/ lisa main import backport romeo #LinuxMint
/etc/apt/sources.list.d/sources.list:# deb-src http://packages.linuxmint.com/ lisa main import backport romeo #LinuxMint
/etc/apt/sources.list.d/sources.list:# deb http://download.learnfree.eu/repository/skss / #SKSS
/etc/apt/sources.list.d/sources.list:# deb-src http://download.learnfree.eu/repository/skss / #SKSS
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:#==================================
/etc/apt/sources.list.d/sources.list:# Paissad Repository (pms-linux)  =
/etc/apt/sources.list.d/sources.list:#==================================
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:#=============
/etc/apt/sources.list.d/sources.list:# mediainfo  =
/etc/apt/sources.list.d/sources.list:#=============
/etc/apt/sources.list.d/sources.list:deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu oneiric main
/etc/apt/sources.list.d/sources.list:
/etc/apt/sources.list.d/sources.list:#==================================
/etc/apt/sources.list.d/sources.list:# Paissad Repository (pms-linux)  =
/etc/apt/sources.list.d/sources.list:#==================================
/etc/apt/sources.list.d/sources.list:deb http://deb.paissad.net/ unstable main contrib non-free
/etc/apt/sources.list.d/sources.list:# deb-src http://deb.paissad.net/ unstable main contrib
/etc/apt/sources.list.d/sources.list:deb http://packages.pulse-eight.net/ubuntu oneiric stable
/etc/apt/sources.list.d/sources.list.save:# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:# newer versions of the distribution.
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:## Major bug fix updates produced after the final release of the
/etc/apt/sources.list.d/sources.list.save:## distribution.
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
/etc/apt/sources.list.d/sources.list.save:## team. Also, please note that software in universe WILL NOT receive any
/etc/apt/sources.list.d/sources.list.save:## review or updates from the Ubuntu security team.
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
/etc/apt/sources.list.d/sources.list.save:## team, and may not be under a free licence. Please satisfy yourself as to 
/etc/apt/sources.list.d/sources.list.save:## your rights to use the software. Also, please note that software in 
/etc/apt/sources.list.d/sources.list.save:## multiverse WILL NOT receive any review or updates from the Ubuntu
/etc/apt/sources.list.d/sources.list.save:## security team.
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:## N.B. software from this repository may not have been tested as
/etc/apt/sources.list.d/sources.list.save:## extensively as that contained in the main release, although it includes
/etc/apt/sources.list.d/sources.list.save:## newer versions of some applications which may provide useful features.
/etc/apt/sources.list.d/sources.list.save:## Also, please note that software in backports WILL NOT receive any review
/etc/apt/sources.list.d/sources.list.save:## or updates from the Ubuntu security team.
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:## Uncomment the following two lines to add software from Canonical's
/etc/apt/sources.list.d/sources.list.save:## 'partner' repository.
/etc/apt/sources.list.d/sources.list.save:## This software is not part of Ubuntu, but is offered by Canonical and the
/etc/apt/sources.list.d/sources.list.save:## respective vendors as a service to Ubuntu users.
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:## Uncomment the following two lines to add software from Ubuntu's
/etc/apt/sources.list.d/sources.list.save:## 'extras' repository.
/etc/apt/sources.list.d/sources.list.save:## This software is not part of Ubuntu, but is offered by third-party
/etc/apt/sources.list.d/sources.list.save:## developers who want to ship their latest software.
/etc/apt/sources.list.d/sources.list.save:deb http://packages.linuxmint.com/ lisa main import backport romeo #LinuxMint
/etc/apt/sources.list.d/sources.list.save:# deb-src http://packages.linuxmint.com/ lisa main import backport romeo #LinuxMint
/etc/apt/sources.list.d/sources.list.save:# deb http://download.learnfree.eu/repository/skss / #SKSS
/etc/apt/sources.list.d/sources.list.save:# deb-src http://download.learnfree.eu/repository/skss / #SKSS
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:#==================================
/etc/apt/sources.list.d/sources.list.save:# Paissad Repository (pms-linux)  =
/etc/apt/sources.list.d/sources.list.save:#==================================
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:#=============
/etc/apt/sources.list.d/sources.list.save:# mediainfo  =
/etc/apt/sources.list.d/sources.list.save:#=============
/etc/apt/sources.list.d/sources.list.save:deb http://ppa.launchpad.net/shiki/mediainfo/ubuntu oneiric main
/etc/apt/sources.list.d/sources.list.save:
/etc/apt/sources.list.d/sources.list.save:#==================================
/etc/apt/sources.list.d/sources.list.save:# Paissad Repository (pms-linux)  =
/etc/apt/sources.list.d/sources.list.save:#==================================
/etc/apt/sources.list.d/sources.list.save:deb http://deb.paissad.net/ unstable main contrib non-free
/etc/apt/sources.list.d/sources.list.save:# deb-src http://deb.paissad.net/ unstable main contrib
/etc/apt/sources.list.d/sources.list.save:deb http://packages.pulse-eight.net/ubuntu oneiric stable
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-oneiric.list:deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu oneiric main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-oneiric.list:# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu oneiric main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-oneiric.list.save:deb http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu oneiric main
/etc/apt/sources.list.d/stebbins-handbrake-snapshots-oneiric.list.save:# deb-src http://ppa.launchpad.net/stebbins/handbrake-snapshots/ubuntu oneiric main
/etc/apt/sources.list.d/super_os_respository.list:deb http://hacktolive.org/repo/archive/ oneiric main restricted multiverse universe partner #Super OS repository
/etc/apt/sources.list.d/super_os_respository.list.save:deb http://hacktolive.org/repo/archive/ oneiric main restricted multiverse universe partner #Super OS repository
/etc/apt/sources.list.d/telepathy-ppa-oneiric.list:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/telepathy-ppa-oneiric.list:# deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/telepathy-ppa-oneiric.list.save:deb http://ppa.launchpad.net/telepathy/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/telepathy-ppa-oneiric.list.save:# deb-src http://ppa.launchpad.net/telepathy/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/tualatrix-next-oneiric.list:deb http://ppa.launchpad.net/tualatrix/next/ubuntu oneiric main
/etc/apt/sources.list.d/tualatrix-next-oneiric.list:# deb-src http://ppa.launchpad.net/tualatrix/next/ubuntu oneiric main
/etc/apt/sources.list.d/tualatrix-next-oneiric.list.save:deb http://ppa.launchpad.net/tualatrix/next/ubuntu oneiric main
/etc/apt/sources.list.d/tualatrix-next-oneiric.list.save:# deb-src http://ppa.launchpad.net/tualatrix/next/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list:deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list:# deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list.save:deb http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-mozilla-security-ppa-oneiric.list.save:# deb-src http://ppa.launchpad.net/ubuntu-mozilla-security/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list~:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list~:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.save:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list.save:n
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list:deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list:# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list.save:deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main
/etc/apt/sources.list.d/ubuntu-x-swat-x-updates-oneiric.list.save:# deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list:deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list.save:deb http://ppa.launchpad.net/webupd8team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-gnome3-oneiric.list.save:# deb-src http://ppa.launchpad.net/webupd8team/gnome3/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-themes-oneiric.list:deb http://ppa.launchpad.net/webupd8team/themes/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-themes-oneiric.list:# deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-themes-oneiric.list.save:deb http://ppa.launchpad.net/webupd8team/themes/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-themes-oneiric.list.save:# deb-src http://ppa.launchpad.net/webupd8team/themes/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list:deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list:deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list:ain
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list.save:# deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list.save:# deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list:# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list.save:deb http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-y-ppa-manager-oneiric.list.save:# deb-src http://ppa.launchpad.net/webupd8team/y-ppa-manager/ubuntu oneiric main
/etc/apt/sources.list.d/yannubuntu-boot-repair-oneiric.list:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu oneiric main
/etc/apt/sources.list.d/yannubuntu-boot-repair-oneiric.list:# deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu oneiric main
/etc/apt/sources.list.d/yannubuntu-boot-repair-oneiric.list.save:deb http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu oneiric main
/etc/apt/sources.list.d/yannubuntu-boot-repair-oneiric.list.save:# deb-src http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu oneiric main

```

Regards

---

### Post by matt_symes on 2012-03-26
Hi

Blimey :) That is an impressive number of sources you have there.

For you initial problem...

```
sudo sed -i 3d /etc/apt/sources.list.d/webupd8team-unstable-oneiric.list
```

```
sudo apt-get update
```

I will scan the rest in a second.

EDIT:

I could not see much else wrong but i may have missed something.

You're using the liquorix kernel ?

Kind regards

---

### Post by jerome1232 on 2012-03-26
> **matt_symes said:**
> Hi

Blimey :) That is an impressive number of sources you have there.

For you initial problem...

```
sudo sed -i 3d /etc/apt/sources.list.d/webupd8team-unstable-oneiric.list
```

```
sudo apt-get update
```

I will scan the rest in a second.

Kind regards

He just needed to add an "m" to the line so it said "main" instead of "ain", you should really read what it is your deleting before simply deleting it.

---

### Post by Sissy8788 on 2012-03-26
> **matt_symes said:**
> Hi

Blimey :) That is an impressive number of sources you have there.

For you initial problem...

```
sudo sed -i 3d /etc/apt/sources.list.d/webupd8team-unstable-oneiric.list
```

```
sudo apt-get update
```

I will scan the rest in a second.

Kind regards

Well, I didn't actually install Linux, My boyfriend did and I had 

no problem til now.Though there is no way he can help me.Or else 

I wouldn't be here :P 

Anyway I got again an error.

```
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension
N: Ignoring file 'Untitled Document 1' in directory '/etc/apt/sources.list.d/' as it has no filename extension

```

Regards :)

---

### Post by matt_symes on 2012-03-26
Hi

> **jerome1232 said:**
> He just needed to add an "m" to the line so it said "main" instead of "ain", you should really read what it is your deleting before simply deleting it.

```
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list:deb http://ppa.launchpad.net/webupd8team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list:deb-src http://ppa.launchpad.net/webupd8team/unstable/ubuntu oneiric main
/etc/apt/sources.list.d/webupd8team-unstable-oneiric.list:ain
```

It was on the third line by itself. It needed deleting.

Kind regards

---

### Post by matt_symes on 2012-03-26
Hi

Check the document is empty.

```
cat /etc/apt/sources.list.d/Untitled\ Document\ 1
```

If it is then delete it with

```
sudo rm /etc/apt/sources.list.d/Untitled\ Document\ 1
```

or if you want to keep it

```
sudo mv /etc/apt/sources.list.d/Untitled\ Document\ 1 ~
```

to move it into your home folder.

Kind regards

---

### Post by Sissy8788 on 2012-03-26
> **matt_symes said:**
> Hi

Check the document is empty.

```
cat /etc/apt/sources.list.d/Untitled\ Document\ 1
```

If it is then delete it with

```
sudo rm /etc/apt/sources.list.d/Untitled\ Document\ 1
```

or if you want to keep it

```
sudo mv /etc/apt/sources.list.d/Untitled\ Document\ 1 ~
```

to move it into your home folder.

Kind regards

It worked!!Thank you so very much for your time and the help of 
course :)

EDIT: Now wine doesn't work :S

Regards :D

---

### Post by matt_symes on 2012-03-26
Hi

> EDIT: Now wine doesn't work :S

Start a new thread in the wine sub-forum, unless it's related to updating. :D

Kind regards

---

### Post by Sissy8788 on 2012-03-26
> **matt_symes said:**
> Hi



Start a new thread in the wine sub-forum, unless it's related to updating. :D

Kind regards

I wish I knew :D Anyway thank you again for everything!You really

helped me way too much :D Now both Software Center and update 

manager work!!

EDIT: Should I mark the thread as solved?:)

Redards :)

---

