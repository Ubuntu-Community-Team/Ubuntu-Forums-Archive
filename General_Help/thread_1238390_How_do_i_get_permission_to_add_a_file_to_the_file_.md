---
title: "How do i get permission to add a file to the file system?"
date: 2009-08-12
forum: General Help
---

### Post by JohneG on 2009-08-12
I want to add a plugin for Rhythmbox to add an Equalizer. I have downloaded the plugin and found directions. They say to unpack the file into the plugin folder which is located at -

/usr/lib/rhythmbox/plugins

Everytime i try to copy it over i get the message -

"There was an error moving the file into /usr/lib/rhythmbox/plugins."

In show more details it says "Error moving file: Permission denied"

So how do i get permission to copy the file over? Please give as much details as you can as i'm only new. Thanks :)

---

### Post by P4man on 2009-08-12
easiest is probably opening a nautilus window with admin rights. open a terminal or press alt + f2 and type:

```
gksudo nautilus
```

The you can drag and drop or copy the files.

If you find you need this often and you don't like typing, there are nautilus extentions which give you a "right click, open as admin" menu which IMHO should be included by default to begin with. I'll look it up if you're interested.

---

### Post by ajgreeny on 2009-08-12
> **P4man said:**
> easiest is probably opening a nautilus window with admin rights. open a terminal or press alt + f2 and type:

```
gksudo nautilus
```The you can drag and drop or copy the files.

If you find you need this often and you don't like typing, there are nautilus extentions which give you a "right click, open as admin" menu which IMHO should be included by default to begin with. I'll look it up if you're interested.
The plugin is **gksu-nautilus**, and I agree, it would make sense to include it as a default in Ubuntu; it is already there in Linux Mint, and has been for a few versions of that Ubuntu derivative, I think.

---

