---
title: "GUI app to delte data permentantly"
date: 2010-09-15
forum: General Help
---

### Post by rmcellig on 2010-09-15
Is there a GUI solution to permanently destroying data on my external HD? I know there are some command line options but I am looking for a GUI solution.

---

### Post by Nythain on 2010-09-15
permanently destroying as in... deleting without going to the trash first? or permanently destroying as in, "shredding" the data so it cant ever be recovered?

---

### Post by rmcellig on 2010-09-15
I am selling one of my external HD's so I want to permanently destroy all the data on it.

---

### Post by SavageWolf on 2010-09-15
I think just reformatting it would suffice, but I'm not sure...

---

### Post by endotherm on 2010-09-15
bleachbit has options to shred data, and a free space wipe option. probably a good bet

---

### Post by rmcellig on 2010-09-15
On my Mac I can zero the data as an option to formatting the drive. I'm looking for something similar in Ubuntu.

---

### Post by ajgreeny on 2010-09-15
Have a go at ```
dd if=/dev/zero of=/dev/sdx
``` Just make absolutely sure you get the correct **of=/dev/sdx** because if you get it wrong you are in big trouble and could wipe the wrong disk.

It is probably best done from a live CD or USB with just the one hard disk installed, then there is little chance of zeroing the wrong device.

You should also have a look at ```
man shred
```in terminal.  I am not aware of any apps with a gui to do this, but really it is not needed for simple activities like securely wiping a disk.

---

### Post by jmszr on 2010-09-15
rmcellig,

This should be of interest to you: [http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html) .

Also, Darik's Boot and Nuke: [http://www.dban.org/](http://www.dban.org/) might work well for your needs.

++1: It is probably best done from a live CD or USB with just the one hard disk installed, then there is little chance of zeroing the wrong device.- ajgreeny

---

