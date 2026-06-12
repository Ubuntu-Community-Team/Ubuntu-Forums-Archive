---
title: "Removing Docky anchor icon."
date: 2011-01-30
forum: General Help
---

### Post by megzaz on 2011-01-30
Hi,

I'm an absolute beginner at Ubuntu. Have just installed Docky and I am trying to remove the anchor icon. Searches elsewhere have told me that this is possible by navigating to “*apps/docky-2/docky/items/DockyItem*” in the gconf-editor and unchecking “*ShowDockyItem*.

However, the folder 'DockyItem' does not appear in gconf-editor and no matter where I look throughout the Docky 2 folders I cannot find the entry "ShowDockyItem".

Thanks
Megan

A little more info - I installed Ubuntu 10.10 yesterday from a 64-bit installation CD on a new partition.

---

### Post by howefield on 2011-01-30
I'd guess you need to update your version of Docky.

If you want to do this, open a terminal and copy the following command...

```
sudo add-apt-repository ppa:docky-core/ppa
``` 

Then do a 

```
sudo apt-get update
```

Apply the updates to your system to get the newer Docky, and you'll find the preference this time.

---

### Post by megzaz on 2011-01-30
That didn't seem to work. Any other suggestions?

---

### Post by megzaz on 2011-01-30
Scratch that. Tried a fresh install and then the updates were successful.

Thanks very much!

---

### Post by howefield on 2011-01-30
Thanks for the update and you're welcome.

---

### Post by MiOiM on 2011-03-31
Hi!

I am also using Ubuntu 10.10 64bits, and I am having the same problem with docky and its update. I mean, I have installed docky 2.0.13 and have the repositories installed, but i don't get any new update. I don't have the ShowDockyItem line and it doesn't work once I include it.

Your solution is to reinstall, but I don't understand if you mean to reinstall docky or the whole ubuntu. I can't afford reinstalling ubuntu, as I have installed and configured many details and if you mean to reinstall docky, will I have to reinstall the theme also?

Thank you in advance.

---

