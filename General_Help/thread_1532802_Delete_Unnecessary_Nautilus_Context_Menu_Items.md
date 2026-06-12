---
title: "Delete Unnecessary Nautilus Context Menu Items"
date: 2010-07-17
forum: General Help
---

### Post by JustinR on 2010-07-17
Hey everybody,

I've been using Ubuntu for quite some time now and my context menu has become cluttered with a lot of applications that I don't use or menu items that I have never used - and most likely won't use.

So I want to remove them, or at least disable them.

So, after searching Google (irrelevant or old results) so then I tried Google with "site:www.ubuntuforums.org" but nobody has had their problem solved.

So has their been any solutions to this? Thank you. :)

Edit: I've looked through GConf-Editor, found nothing, and have looked through the directories .Cache/.Config/.Local/.Nautilus in my home diretory and nothing came up of relevance in the first three and the .Nautilus directory was empty.

---

### Post by JustinR on 2010-07-21
Sorry for bumping - it would be nice to get rid these annoying context menu items.

---

### Post by caseyb on 2010-07-31
I would like to accomplish the same thing.  If I right-click on a directory, I get **twenty** (!) context menu options.  That's the default (in Lucid) and is excessive.


[LIST=1]
[*]Open
[*]Browse Folder (does the same thing as Open, so why is it here?)
[*]Open with Other Application... (why would I open a directory with another application?)
[*]Cut
[*]Copy
[*]Paste Into Folder (get rid of it)
[*]Make Link
[*]Rename...
[*]Copy to > (get rid of it)
[*]Move to > (get rid of it)
[*]Move to Trash
[*]Stretch Icon... (get rid of it)
[*]Restore Icon's Original Size (get rid of it)
[*]Send To... (get rid of it)
[*]Encrypt
[*]Sign
[*]Synchronize on Ubuntu One (get rid of it)
[*]Compress...
[*]Sharing Options (available as a tab in Properties, so why have it here again?)
[*]Properties
[/LIST]

---

### Post by Sm0ke42o on 2010-08-06
Bump for solution on this.

I removed python 3.1 a while back and the context menu item remains. Kind of obnoxious that I have a menu item for a version of python I no longer use but no menu item for the version I *am* currently using. 

I though perhaps nautilus actions would allow me do it but I guess its only for adding items, unless I'm missing something.

Plenty of hits on google regarding this but I have yet to find any solutions.

---

### Post by Nuxala on 2010-09-12
To remove send to (and I think sharing options)

Go to Ubuntu Software Center an click "installed software" and search:

nautilus-sendto
 nautilus-sendto-empathy
nautilus-share

and remove them and restart ubuntu

---

### Post by alecz20 on 2011-04-12
> **Nuxala said:**
> To remove send to (and I think sharing options)

Go to Ubuntu Software Center an click "installed software" and search:

nautilus-sendto
 nautilus-sendto-empathy
nautilus-share

and remove them and restart ubuntu

If I try to remove nautilus-sendto, I get this:
To be removed:
    -> Ubuntu-desktop  :shock:

I guess it's so tied to ubuntu, that it cannot be removed
... So much about modularity...):P

---

### Post by mc-rpg on 2011-11-26
> **alecz20 said:**
> If I try to remove nautilus-sendto, I get this:
To be removed:
    -> Ubuntu-desktop  :shock:

I guess it's so tied to ubuntu, that it cannot be removed
... So much about modularity...):P

ubuntu-desktop is a metapackage, if you uninstall it it won't "uninstall" your entire desktop :) just that the meta package will appear as uninstalled, but you're desktop will remain just like it was.

Bump because I'd really like to remove those unwanted context menu items.

---

### Post by alecz20 on 2011-11-26
> **mc-rpg said:**
> ubuntu-desktop is a metapackage, if you uninstall it it won't "uninstall" your entire desktop :) just that the meta package will appear as uninstalled, but you're desktop will remain just like it was.

Bump because I'd really like to remove those unwanted context menu items.

Actually, I remember remobing that package once, and the taskbars wouldn't appear when booting.

Maybe I'll give it a try again.

---

