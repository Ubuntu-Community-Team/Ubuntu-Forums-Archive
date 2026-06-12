---
title: "Deleted USB files on Ubuntu?"
date: 2011-02-22
forum: General Help
---

### Post by wonderwoman on 2011-02-22
I was wondering where my deleted USB files go on Ubuntu?
I was reading that they are transferd to my C drive??
Is this true and why?
Thanks

Edit: sorry for the confusion. 
When I delete a file from a usb drive I see it in my trash foldet on my desktop. Does that mean that the file is moved to the computers local drive? 
I did not import any files to the hard drive. They were only on the usb drive.
 what I mean to ask is, is the files I delete on my usb drive get moved to the computers local drive (hard drive)

---

### Post by Hoopz on 2011-02-22
I am just guessing here (don't know alot linux yet) but maybe it's putting the files in the trash? ???

---

### Post by JC Cheloven on 2011-02-22
Sorry, your question doesn't seem to have much sense to me. If it's not a joke, could you please be more specific? As for now:
 
> **wonderwoman said:**
> I was wondering where my deleted USB files go on Ubuntu?
As far as I know there's not such thing as "usb files". ¿What do you mean? Files stored in an external usb disk/pendrive should, in principle, behave as any other file. When deleted are placed in the trash bin.

> I was reading that they are transferd to my C drive??
Is this true and why?

There's no "C drive" in linux. If you have a windows partition over there, and you mean that, deleted files in linux don't go there anyway. 

JC

---

### Post by ewaynec on 2011-02-22
"Good Grief", Don't complicate the issue. A simple question begs a simple answer, which is; The USB drive has a "trash" on it, (hidden) and that is where they go.

---

### Post by wonderwoman on 2011-02-22
> **JC Cheloven said:**
> Sorry, your question doesn't seem to have much sense to me. If it's not a joke, could you please be more specific? As for now:
 

As far as I know there's not such thing as "usb files". ¿What do you mean? Files stored in an external usb disk/pendrive should, in principle, behave as any other file. When deleted are placed in the trash bin.



There's no "C drive" in linux. If you have a windows partition over there, and you mean that, deleted files in linux don't go there anyway. 

JC

I made an edit for hopefully better understanding

---

### Post by wonderwoman on 2011-02-22
> **ewaynec said:**
> "Good Grief", Don't complicate the issue. A simple question begs a simple answer, which is; The USB drive has a "trash" on it, (hidden) and that is where they go.
so they dont get moved to a different drive when I delete?

---

### Post by JC Cheloven on 2011-02-23
> **wonderwoman said:**
> I made an edit for hopefully better understanding

Thanks, It's more clear now :)

When you "delete" a file from nautilus (the file manager) with the "del" key, it's not actually deleted but moved to a temporary place in the same device as the file was. That place is called the trash. If it's an external usb disk or pendrive, you are given the option to "empty the trash" when you unmount (or extract securely, or whatever it's eventually named) the usb device. Answering "yes" actually deletes the files and liberates the space in that device. Answering "no", the files will remain in the trash, and will be still accesible the next time you use the device.

You can right-click the trash at any time to empty the trash from the popup menu, though.

You can also use (with care) Shift-Del to delete the file right away, without passing to the trash.

Hope this helps

---

