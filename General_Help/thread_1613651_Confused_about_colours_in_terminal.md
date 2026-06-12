---
title: "Confused about colours in terminal"
date: 2010-11-04
forum: General Help
---

### Post by ianc1 on 2010-11-04
When I do ls at the command prompt I obviously get the directory listing for the current directory which has some colour coding.  White for files, blue for directories and red for something else (maybe archives - I can't remember).

I have a few directories which contain jpegs from a number of digital cameras.  One produces file names ending in JPG (upper case) and the other jpg (lower case).  The JPG files appear in white as I expected but the jpg files appear in a light purple when I do the ls command.

I can understand white as the JPG files are, well, files, but what's the purple for?

Any ideas?

Thanks

Ian

---

### Post by Vaphell on 2010-11-04
my guess is that it detects images by the case sensitive .jpg and shows them in a different color. mp3s are cyan and so on (though on my box they are mostly green because of the executable flag, i guess i messed up something during the import from ntfs)

---

### Post by coffeecat on 2010-11-04
If you look in your ~/.bashrc file you'll see that ls is aliased to 'ls --color'. The --color option uses the LS_COLORS environment variable. To read more, type 'dircolors -p' in a terminal. Even better, do:

```
dircolors -p > Desktop/dircolors
```... to get a text file called dircolors on your desktop which you can study at your leisure. You'll see that various filename types are assigned to different colo[SIZE=4][COLOR=Red]u[/COLOR][/SIZE]rs :wink:, but that all are all-lowercase. I haven't looked closely enough to be sure, but I guess that any filetype that is not listed defaults to white. And bearing in mind  that in Unixland, JPG is not the same as jpg.

---

### Post by ianc1 on 2010-11-07
Thanks all.  The code to determine all the colours is a great help.  I'm still a little bemused as when I rename the *.JPG files to *.jpg  they still do not appear the same colour as the original *.jpg files.  I was aware of the case sensitiveness of the os but it had obviously slipped my mind.

Thanks

---

### Post by efflandt on 2010-11-07
It could be a permissions issue.  Files that came from a FAT32 partition may appear to have 777 permission with write and execute bits set for everyone because FAT32 has no concept of file permissions.  Files with execute permission may be a different color/  You might try **chmod 644 *.jpg** in that directory and see if that makes a difference.

---

### Post by ianc1 on 2010-11-08
Ah and I thought you could have had a point there, unfortunately however the permissions of the *.JPG files (now renamed as *.jpg) and the *.jpg files are identical:  -rw-r--r--.

I know its not an issue as such as I can still read, edit and save the files but I would like to get to the bottom of this.

---

