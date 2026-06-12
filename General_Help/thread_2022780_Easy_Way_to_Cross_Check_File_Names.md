---
title: "Easy Way to Cross Check File Names?"
date: 2012-07-11
forum: General Help
---

### Post by mamamia88 on 2012-07-11
I had to format my pc the other day and was in the process of converting my music collection to flac.  Before I did so I batch converted all my flacs to mp3 for portable use.  I also backed up on my external harddrive.   Now here's my problem.     My mp3 player has a file count roughly 60 files more than what banshee shows from my external hd backup.  is there a way that i can crosscheck the file names on my portable media player and on my computer and get a list of filenames that aren't on my computer?

---

### Post by papibe on 2012-07-11
Hi mamamia88.

If you mount your mp3 player as storage device, you can compare directories using diff.

For instance:
```
diff /media/MP3/library  ~/Music
```
Adjust the paths so the comparison makes sense for you.

You can do a similar work using a GUI tool called Meld, it is on the Software Center.

Hope it helps,
Regards.

---

### Post by mamamia88 on 2012-07-11
> **papibe said:**
> Hi mamamia88.

If you mount your mp3 player as storage device, you can compare directories using diff.

For instance:
```
diff /media/MP3/library  ~/Music
```
Adjust the paths so the comparison makes sense for you.

You can do a similar work using a GUI tool called Meld, it is on the Software Center.

Hope it helps,
Regards. thanks i'll try that edit problem with that is that i'm trying to compare flacs to mp3.  is there a option to ignore file extension?

---

### Post by sudodus on 2012-07-11
If you can connect your portable player via USB and mount the partition with mp3 files, you can use the command line tools.

Try the following command, that will find files with the extensions mp3 and MP3 in the current directory and its subdirectories

```
find . -iname *.MP3 | wc -l
```

And if you run only ```
find . -iname *.MP3
``` you get a list, that you can sort and compare to the corresponding list in your computer.

---

### Post by mamamia88 on 2012-07-11
> **sudodus said:**
> If you can connect your portable player via USB and mount the partition with mp3 files, you can use the command line tools.

Try the following command, that will find files with the extensions mp3 and MP3 in the current directory and its subdirectories

```
find . -iname *.MP3 | wc -l
```

And if you run only ```
find . -iname *.MP3
``` you get a list, that you can sort and compare to the corresponding list in your computer.

that command is only giving me a file count

---

### Post by steeldriver on 2012-07-11
how about something like 

```
for file in $(find *mp3dir *-iname '*.mp3'); do [[ $(find *flacdir *-iname $(basename "${file%.mp3}.flac")) ]] || echo "$file"; done
```substitute your actual mounted dirs for *mp3dir* and *flacdir *

---

### Post by houseworkshy on 2012-07-11
One very handy gui tool for sorting out redundant file names and duplicates, and other lint, is FSlint which is in the repositories.

---

### Post by sudodus on 2012-07-12
> **mamamia88 said:**
> that command is only giving me a file count
The second one works, and it should be modified with quotes like this
```
find . -iname "*.MP3"
```
And if you run that command in both directories to be compared, and you [FONT="Courier New"][SIZE="3"]sort[/SIZE][/FONT] the lists, you can compare them with [FONT="Courier New"][SIZE="3"]diff[/SIZE][/FONT].

Example:
In the old directory
```
find . -iname "*.mp3"|sort>~/old.txt
```
In the new directory
```
find . -iname "*.mp3"|sort>~/new.txt
```
And look for differences (~ is your home directory)
```
diff ~/old.txt ~/new.txt
```

If there is no output from the diff command, the two list files are the same (the same file names in both). Of course this does not check that the files are the same.

If you need to check that the files are the same (have the same binary content), use *papibe*'s solution! It gives more information but is slower.

*Edit: If you need to check and update (synchronize) the two directories, you can use the program rsync. In the manual, there are good explanations and examples.*
```
man rsync
```

*Edit2:* Or if the directory structure differs, you can compare the files without the relative paths:

In the old directory
```
find . -iname "*.mp3" -exec basename {} \;|sort>~/old.txt
```
In the new directory
```
find . -iname "*.mp3" -exec basename {} \;|sort>~/new.txt
```
And look for differences (~ is your home directory)
```
diff ~/old.txt ~/new.txt
```

---

### Post by nothingspecial on 2012-07-12
*Thread moved to **General Help**.*

---

