---
title: "Nautilus Hide windows Files or files that match by name"
date: 2009-08-20
forum: General Help
---

### Post by BRAXS69 on 2009-08-20
Greetings, the title basically says it all, but before anyone jumps on me that linux is not gonna implement a hidden folder tag or read windows tagging, that's not what I'm asking. really i love the "dot", it makes things easier.:)

what I'm asking is if anyone knows how to configure nautilus to also treat a file/folder as hidden based by its name. 

such as **"thumbs.db"** or folders like **"System Volume Information"** files/folders that have utterly no use in Linux but needed by windows, i cant really rename and expect windows treat the same if i put the dot in front of it. 

im asking this because i use both linux and windows( i have no choice ), and constantly diving into windows drives and ntfs partitions and have to meet this in my opinion unnecessary clutter. 

any help or comments would be appreciated 
thanks... XD

---

### Post by drs305 on 2009-08-20
This is not exactly what you are looking for, but you can hide specific folders and/or files by creating a text file called ".hidden".

Open the file, add the names of any folders or files in the same directory/folder you want hidden. Save the file, then have Nautilus hide any hidden files/folders (CTRL-H). Any of the contents of .hidden will now not be displayed in Nautilus. This does not effect command line operations.

---

### Post by Marlonsm on 2009-08-20
I don't know how to hide all files in every folder, but in an specific folder, you can use the .hidden file.

For example, to hide thumbs.db in a folder, create a file named .hidden in that folder and put the name of everything you want to hide in it, like thunbs.db.

Just note that the .hidden file won't be hidden in Windows.

---

### Post by BRAXS69 on 2009-08-20
> **Marlonsm said:**
> I don't know how to hide all files in every folder, but in an specific folder, you can use the .hidden file.

For example, to hide thumbs.db in a folder, create a file named .hidden in that folder and put the name of everything you want to hide in it, like thunbs.db.

Just note that the .hidden file won't be hidden in Windows.

wow that's a handy thing to know, if only there was a globalized version.

---

