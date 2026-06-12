---
title: "SAGU ! ~ A Thoeretical Production"
date: 2006-05-30
forum: General Help
---

### Post by Arandomcow5 on 2006-05-30
Here it is everyon, SAGU, a code that updates and upgrades your entire machine in 4 letters : SAGU

I developed this because, in short, im a minimalist. It is named "SAGU" because that is the acronym for sudo apt-get update and sudo apt-get upgrade. Although, the code itself uses Aptitude. So in reality, it should be SAU, but SAGU sounds way cooler.

This is what you do:

**1. Create a new word document:**
With your favorite word editor (I prefer gedit), make a new file named "sagu". Input this code into the newly created file:
```
#!/bin/sh
sudo -v
echo ''
echo 'Updating...'
echo ''
echo ''
sudo aptitude update -q -y -q
echo ''
echo ''
echo 'Done Updating, Now Upgrading...'
echo ''
echo ''
sudo aptitude upgrade -q -y -q
echo ''
echo ''
echo 'Finished Upgrading.  Enjoy!'
echo ''
exit 0
#Developed by Pen Pen Productions and Thoeretica Limited
```

**2. Move the file**
Now that you have the sagu file all done, move it to your /usr/bin/ directory

**3. Make the file executable**
Last, but not least, make the file executable. Open a terminal and type in:
*sudo chmod a+x /usr/bin/sagu*

And your all set! To run it, just type "sagu" into a terminal. It will update and upgrade everything, and is a whole lot faster than typing out both "sudo apt-get upgrade" and "sudo apt-get update", or "sudo aptitude upgrade" and "sudo aptitude update".

---

