---
title: "How to extract a single file from a .bz2 archive?"
date: 2009-12-30
forum: General Help
---

### Post by ogromano on 2009-12-30
How can I extract a single file or folder from a tarball from the command line?

Can't seem to find this one anywhere and the man page for TAR only explains the -x option for extracting "all" the files in the archive and I don't understand very well from the man page how the -C (change to directory DIR) and -T (get names to extract or create from FILE) options work. 
The -T option might do the trick, but does it mean I have to make a txt file with the paths of the files I want to extract or should I substitute "FILE" for the path of the file to extract??

When using archive manager, I have no problem selecting one file or one folder and then dragging and dropping it into the folder I want it to be extracted to.... but I was wondering if there's a command I could run on the terminal that could give me the same result.

The reason behind this is that the .bz2 file I have is very, very large (over 30GB) :shock: ... and takes forever to load using the GUI and since I can output a list of the files in the archive to a txt file, it would be easier to just copy the address of the files or folders I wish to extract and specify them on the command line without having to load the whole file....
This is of course under the assumption that it doesn't load the whole file when you pass it this command.

Thanks for any input...

 - Ogro -

---

### Post by ogromano on 2010-01-06
bump... any takers??

---

### Post by warfacegod on 2010-01-06
When you open the archive try highlighting the file you want and hit extract. That's worked for me.

---

### Post by warfacegod on 2010-01-06
Sorry, didn't realize you wanted to do it with command line, can't help you there.

---

### Post by SecretCode on 2010-01-06
Try this ... half tested.
```
tar -xvjf archive-file.bz2 -C dir-to-put-file-in/ name.of.file
```

---

### Post by ogromano on 2010-01-06
Hi,

I tried what you suggested and apparently it only works if the file I want to extract is not within another folder. It doesn't work either if I just want to extract a complete folder. See below.

This attempt worked because the file was in the root of the archive.
> ogro@ubuntu-OR:~$ tar -xvjf ~/Downloads/ManageDiscImages_files.tar.bz2 -C ~/Downloads/ urchin.js
urchin.js
ogro@ubuntu-OR:~$
In the next two cases first I tried to extract the same file from inside another folder and in the second example I tried to extract just the folder and didn't get anywhere.

> ogro@ubuntu-OR:~$ tar -xvjf ~/Downloads/ManageDiscImages_files.tar.bz2 -C ~/Downloads/ /ManageDiscImages_files/urchin.js
tar: Record size = 8 blocks
tar: /ManageDiscImages_files/urchin.js: Not found in archive
tar: Exiting with failure status due to previous errors


ogro@ubuntu-OR:~$ tar -xvjf ~/Downloads/ManageDiscImages_files.tar.bz2 -C ~/Downloads/tmp/ /ManageDiscImages_files/
tar: Record size = 8 blocks
tar: /ManageDiscImages_files: Not found in archive
tar: Exiting with failure status due to previous errorsI'm still not quite sure what the -C switch is doing... is it allowing me to extract to a different folder or is it supposed to allow me to change directories inside the archive??

I managed doing it with GUI after about 3 days of waiting for it to load, pulling out a folder, then waiting for it to be extracted and repeating... but it was worse than pulling teeth!! I'd still like to know how to do this more efficiently.

Thanks.

---

### Post by SecretCode on 2010-01-07
Yes, -C confuses me too. It changes the directory where the extracted files will go, so it's effectively like using *cd* first (and then *cd*ing back to the original directory afterwards).

tar has some funny expectations about absolute vs relative paths and leading /s or not. Try your commands again without the leading /.

Also it depends on what the full paths are in the tar itself. Running *tar -tvjf archivename* should give you a list of files with (relative?) paths - try using the file name exactly as show in that output.

---

