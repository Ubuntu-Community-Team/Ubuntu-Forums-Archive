---
title: "How to manipulate iso files"
date: 2010-01-17
forum: General Help
---

### Post by Claus7 on 2010-01-17
Hello,

maybe this is a known issue, yet because I have not found a definite how, I'll give my insight on it.

What we want to do: be able to see the contents of an iso image (what files exist in the iso image) as well as being able to add data to the iso file or remove them.

In order to be able to see the contents of an iso image we have to follow a process similar of that like mounting a device. In order to do so let us assume that we have the file: *example.iso*, under */home* folder. In order to mount it we have to do:


```
mkdir /media/iso

sudo mount -t iso9660 -o loop /home/example.iso /media/iso
```

then navigate to the folder /media/iso and with:
```
ls
```
command to see the contents of the iso image.

Now let us assume that the file we have is big enough so as to write it on a disk. What we can do, is to remove some files from the iso image, yet in great care, cause we might move files that will make the image useless.

In order to do so, we have to install the program *isomaster* (go to synaptic package manager and type isomaster and the program will be displayed) and then open it (via applications->sound&video). Then, browse to where the iso image exists and with the options: remove, extract, e.t.c. do the necessary steps you want. In order to save this "new" iso image with the additions you have made, you have to save it as an iso file. Go to file, save as and your new iso file is ready to be burned.

Regards!

---

### Post by bryanagee on 2010-01-18
If using a GUI, this is all easily done with Archive Manager. Good reference for cli tho.

---

### Post by schmidtbag on 2010-01-18
you could also use isomaster.  it doesn't have live editing but its still a good and easy program to use.  its in synaptic

---

### Post by akakingess on 2010-01-18
I don't know, but Gmount-iso may do the live editing, and it too is in Synaptic.

---

