---
title: "Viewing/Deleting 8,000 jpg files"
date: 2010-07-30
forum: General Help
---

### Post by mikmikmikmik on 2010-07-30
Hi, I need to see if any of these 8,000 jpg file hogging up my home directory(:() have anything besides a green or grey screen with a few words. All of the files start with the same few characters: "99-20100721" has a few more and then ".jpg" Any ideas?

If not, then how about an easy way to delete them all in one foul swoop? with out deleting the other jpgs i have in my home directory?

Thanks in advance

---

### Post by jtarin on 2010-07-30
[Possibly what the Dr. ordered.]("http://lowfatlinux.com/linux-find.html")

Or to be totally safe [move them]("http://www.computerhope.com/unix/umv.htm") to another dirctory for viewing then use the "rm" command on the directory after your satisfied.

---

### Post by mikmikmikmik on 2010-07-30
Hi, I need to see if any of these 8,000 jpg file hogging up my home directory(:cry:)can be deleted in one foul swoop  with out deleting the other jpgs i have in my home directory?

Thanks in advance

EDIT:
they all start with  "99-20100721"

---

### Post by BenAshton24 on 2010-07-30
Well unless the jpgs you want to delete share a certain characteristic which can be used to differentiate them from the ones you want to keep, there isn't really anything you can do. Are the jpgs that you want to delete in a different directory? Are they larger than the ones that you want to keep? Do they have a common element in their filenames? etc.

---

### Post by gastly on 2010-07-30
Are the files that you want to delete in the same directory as the files you don't want to delete? ;)
If the files to be deleted have a pattern in their names like "abc_123.jpg", you can delete the files with the find command.

[color=red]**First test out the find command without -delete option, just to see if the files listed are the ones you want to delete**[/color]

```

# First try this
find $HOME/folder -name "abc_*.jpg" -type f -depth

#If the output is the name of files that you want to delete, then do this:
find $HOME/folder -name "abc_*.jpg" -type f -delete

```

---

### Post by overdrank on 2010-07-30
Threads merged.

---

### Post by mikmikmikmik on 2010-07-30
I've executed the command:```

find . -name 99-201* -exec mv {} "Desktop/test/" \;
```
(they all start with 99-201) and it is still running, but when i look at the folder test on my desktop it only has the file i put in there before i ran the command.

---

### Post by mikmikmikmik on 2010-07-30
and the command:
 ```
find $HOME/ -name "99-201*.jpg" -type f -depth
```

but then after that it says:
```
find: warning: you have specified the -depth option after a non-option argument -name, but options are not positional (-depth affects tests specified before it as well as those specified after it).  Please specify options before other arguments.
```

---

### Post by jtarin on 2010-07-30
If you are in the folder where all the files are and there are no subdirectories that contain said files, then you don't need the option depth.

---

