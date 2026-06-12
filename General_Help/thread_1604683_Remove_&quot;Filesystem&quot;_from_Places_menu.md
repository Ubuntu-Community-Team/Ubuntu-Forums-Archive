---
title: "Remove &quot;Filesystem&quot; from Places menu?"
date: 2010-10-24
forum: General Help
---

### Post by FatalKeystroke on 2010-10-24
Does anyone know of a way to remove "Filesystem" from the places menu?

---

### Post by coffeecat on 2010-10-24
If you mean 'Computer', I don't know. Filesystem itself is not in a default Places menu, so I assume you would have added it as a bookmark. If so, open any Nautilus window > Bookmarks menu > Edit Bookmarks.

---

### Post by FatalKeystroke on 2010-10-24
I'm sorry, I said places, I meant the Nautilus sidebar.

---

### Post by coffeecat on 2010-10-24
I see what you mean. Sorry - but I don't know, and a google search didn't throw anything up.

I could be wrong, but I think the problem is that Nautilus lists everything mounted in /etc/fstab there as well as any detected but unmounted partitions, and other stuff like Network. So 'File System' would correspond to the '/' mount line in fstab.

I couldn't see anything in gconf-editor either that would help.

Out of interest, why would you want to remove that? Is it to hide it from less privileged account holders?

---

### Post by FatalKeystroke on 2010-10-24
Yes, I want to hide it from certain accounts, mainly the guest account, but others as well.
I have a few users who can barely operate Windows but are using said Linux PC and I want to make sure that they cannot accidentally get to anything but the basics, i.e. ~/, Firefox, Open Office, GIMP, MPlayer, etc.
I've got pretty much everything taken care of except this one item.

The thing is, I don't want them to wind up in /etc or something by accident. In my experience, Windows people think that they can click on anything and change whatever they want without causing any damage (And they always think they know what they're doing).

---

### Post by coffeecat on 2010-10-24
If you create user accounts without administrative privileges they may be able to browse the system and even read files, but they won't be able to change or delete anything owned by root. To stop them being able to browse other users' home folders, you'd need to have them in different main groups, but  this is the default in Ubuntu anyway.

---

