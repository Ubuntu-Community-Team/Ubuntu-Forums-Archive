---
title: "How do I restore data from a Brasero DVD?"
date: 2010-03-26
forum: General Help
---

### Post by rva1945 on 2010-03-26
Lets' say I burn a DVD with folders and files from my Ubuntu partition (just some folders) an ISO file is created in the DVD.

Then if I need to recover the files, what do I have to do, Brasero again, or which application will read files from the ISO file?

Thanks

---

### Post by cjhabs on 2010-03-26
> **rva1945 said:**
> Lets' say I burn a DVD with folders and files from my Ubuntu partition (just some folders) an ISO file is created in the DVD.

Then if I need to recover the files, what do I have to do, Brasero again, or which application will read files from the ISO file?

Thanks

The following command should do the trick:
mount -o loop -t iso9660 name_of.iso /mountpoint

---

### Post by NoXiS on 2010-03-27
The main question here is why an ISO image is being burned onto your DVD.

An ISO file is a disc image file, you could think of it like a virtual DVD.

When you open brasero and create a new data project, and drag the stuff you want to backup into this project, the files should be burnt directly onto the disc, not an ISO image.

When you burn an ISO image onto a disc, you really should be using the 'burn disc image' option in brasero (or any other burning software). This doesn't burn the ISO image file onto the disc, but rather the contents of the ISO image (which means that the files will be directly accessible when you stick the disc in.

Also for mounting ISO image files, an easier way for most people would be to use an image mounting utility like AcetoneISO ( [http://www.getdeb.net/software/AcetoneISO](http://www.getdeb.net/software/AcetoneISO) ). Don't think it's in the normal repositories.

edit:

It is in the normals repos, look for acetoneiso.

---

### Post by rva1945 on 2010-03-27
Well as I am still new to Linux I have some doubts, that's the reason I often ask for help. But in this case, as soon as I inserted a blank DVD, the CD/DVD creator utility kicked in and after burning the files, an accesible DVD was the result.

Thanks

---

