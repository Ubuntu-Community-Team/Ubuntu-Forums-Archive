---
title: "Copy Files - Preserve Attached Notes"
date: 2010-02-14
forum: General Help
---

### Post by lannatwin on 2010-02-14
I am copying files from one machine to another over a network. The files have notes attached (right click/properties/notes).

After copying, the notes do not appear on the new copies.

How can I get the attached notes to copy along with the files?

Thank you.

---

### Post by cariboo on 2010-02-14
I would suggest have a look at man cp, it looks like the --preserve option should do what you need.

---

### Post by lannatwin on 2010-02-14
You mean to tell me I have to use the command line for this?? :roll:

---

### Post by niteshifter on 2010-02-15
Hi,

Actually ... you're just out of luck here. The "Notes" feature of GNOME (Nautilus) is not true file metadata. This:
```
cp --preserve=all src dest
```
only preserves metadata as recognized by the base file system, not the virtual one (gvfs).

The Notes (and Emblems and so forth) are kept in a database located in ~/.nautilus/metadata as XML files.

Yeah, I was rather bummed out when I found that what could be a really useful (shades of BeOS!) feature really isn't all that useful.

Edit: This will learn me: Drag 'n Drop didn't used to work. Just for the hell of it I just tried it - and it worked. The cp doesn't. Now I'm curious as to when it started working, I gave up on it in Gutsy ...
Current OS: 8.04.4 / GNOME 2.22.3 / Nautilus 2.22.5.1

Edit #2: It just clicked in for me. OP is trying to do this over a network. That won't work, the Nautilus metadata is local machine only.

---

### Post by lannatwin on 2010-02-15
So, would it be a bad idea to copy ~/.nautilus/metadata from one machine to the other? 

Tks.

---

