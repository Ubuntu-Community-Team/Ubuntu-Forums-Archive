---
title: "tar.gz and file property notes"
date: 2009-12-14
forum: General Help
---

### Post by Raos on 2009-12-14
I've been using tar.gz archives to backup and transfer files, but I've found that notes I've added to files in the properties have been stripped when they come back out of the archive.  Is there some way I can tar files without losing notes that I've added?

---

### Post by Raos on 2009-12-19
Is there not any way I can get files in and out of a tar archive with property notes attached to the file?

---

### Post by x33a on 2009-12-19
could you please explain your problem in detail.

please mention the steps or post the script (if any), you are using for the backup.

---

### Post by 3rdalbum on 2009-12-19
The OP is talking about when you attach a note to a file by right-clicking the file and going to Properties, and then clicking the Notes tab.

I can't seem to figure out where the notes are stored either; can anyone shed some light on it?

---

### Post by Raos on 2009-12-19
3rdalbum is correct on the notes.  To archive, I'm just right clicking on folders and selecting compress to generate an archive of them.

---

### Post by x33a on 2009-12-19
after some searching i found this:

> Both emblems and notes are stored in XML files, one per directory, in              ~/.nautilus/metafiles/. To be more accurate, a *reference* to              the emblems is stored in the XML file                                                                The emblem icons are in          /usr/share/pixmaps/nautilus/Bluecurve/ (in Fedora Core 5).         In each XML file, there is a tag called <keyword> and emblems are          stored in the "name" property. Each emblem assigned creates a new          <keyword> tag.  Notes are stored in the <file> tag in the          "annotation" property.  Here is a snippet of a metafile with the cool          emblem and a note:
                  <file name="workfile.txt" timestamp="1147178708" annotation="this is          a note added to the workfile.txt file."><keyword          name="cool"/></file>                                    In addition to information about emblems and notes, the metafiles store         things like window size, location, view mode, and backgrounds.
source:```
http://www.linuxboxadmin.com/articles/tools-and-utilities/nine-things-you-should-know-about-nautilus.html
```

so these notes are stored in these metafiles under the annotation tag.

---

### Post by Raos on 2009-12-29
Interesting, but might that have recently changed?  I first noticed the notes problem when transferring files from my old laptop (running Jaunty) to my new laptop (Karmic), and looking back at the old hard-drive the metafiles are all there with the annotations, but .nautilus on the Karmic box is just empty.

---

### Post by x33a on 2009-12-29
might be possible. i can't verify it since i am not using ubuntu. maybe something to do with gnome 2.28.

---

