---
title: "Mysterious trash file names"
date: 2011-02-14
forum: General Help
---

### Post by whatthefunk on 2011-02-14
Im writing my first bash script.  Its function is to move files to the trash can and write a log file in the same format that the system does to allow for file restoration.  The problem is that in bash, everything works fine, but in the OpenBox window session, the files are named after the source directory, not the original name.
I've narrowed the problem down to these bits of script:

```

SOURCE="$1"
DEST=$(dirname ~/.local/share/Trash/files/filename)

FILE="$(basename "$SOURCE")"

if [ -e "${DEST}/${FILE}" ]; then

  ...code...

  mv -- "$SOURCE" "${DEST}/${FILE}.$max"
else

  ...code...

  mv -- "$SOURCE" "$DEST/${FILE}"
fi

```

So I run the script with the test file "Junk".
In bash, it moves over and its named correctly.
```

~/.local/share/Trash/files$ ls
file  file.1  Files  Files.1  **Junk**

```

The log file is also named correctly
```

~/.local/share/Trash/info$ ls
file.1.trashinfo  Files.1.trashinfo  Files.trashinfo  file.trashinfo  **Junk.trashinfo**

```

But, when I go to view the trash can in the file manager in Openbox, the file is called "Testing" which is the name of the source directory.  However, if I go to the trashcan via its full path (going to .local/, then share/) all the files are named correctly.  

I did a second test.  I simply moved a file with the mv command to  the Trash folder and then viewed it in the file manager.  The file was  named correctly.  So there is something wrong with the way that I am  naming files with my script.

Does anybody know whats going on?  Im totally stumped...  Is there some way to get the trash can to read the correct file name?
Any help would be appreciated.

---

### Post by whatthefunk on 2011-02-14
Figured it out.  The name of the file when viewed from the file manager Trash window is dependent on the last part of the path as written in the log file.  My script was only writing the log up to the directory from which the file had come from and so the Trash window was calling my file by the directory name it had come from instead of by its actual name.  Thats weird...I suppose they do that to maintain a link between the file and log file.  I guess my script will have to do that too....crap.  What started out as a simple one line mv alias is now nearly 100 lines long and growing all the time.

---

