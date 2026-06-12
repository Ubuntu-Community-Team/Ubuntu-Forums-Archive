---
title: "Zipping Multiple Files into Multiple Archives from Terminal"
date: 2010-12-02
forum: General Help
---

### Post by rfry11 on 2010-12-02
After learning that the VisualBoy Advance from the Ubuntu repositories can load .ZIP archived ROM files, I'm interested in archiving all of my ROM files into .ZIP files.

Does anyone know a good terminal command to get this done quickly and efficiently?

To better describe what I'm asking, I want every ROM file (.GBC files) in its own .ZIP file. 

Example:
Put the files "007 - The World is Not Enough (UE).gbc", "Catwoman (U).gbc", and "International Rally (U).gbc" into zip archives entitled "007 - The World is Not Enough (UE).gbc.zip", "Catwoman (U).gbc.zip", and "International Rally (U).gbc.zip"

By my calculations this will reduce the file size by half, and would greatly help me. I won't individually zip them if there's no easy way to do it, it's not worth 400mb of extra space for an afternoon's work.

---

### Post by HiImTye on 2010-12-02
you could try something like
```
ls | grep gbc | zip -9
```

---

### Post by rfry11 on 2010-12-02
I'm getting an error when I run this command.


```
$ ls | grep gbc | zip -9

zip error: Invalid command arguments (cannot write zip file to terminal)
```

Am I lacking something in my install, or inputting the command incorrectly?

EDIT:

Just searched for my error on Google, and found [this page]("http://zotline.com/shownote.zot/NoteNum/4419.html"), where it says that I have to "give the name of the zipfile you want to create on your command line.". Any way to have the zip program generate names based off of the file's names?

---

### Post by mdgtptrl on 2010-12-02
your best bet may be to write a shell script to do it using foreach and basename to generate new filenames, and pass those to zip

```
#!/bin/bash

files=`find *.gbc`

for file in $files
do
   newname="`basename $file .gbc`.zip"
   zip $newname $file
done

```

---

### Post by rfry11 on 2010-12-02
Thanks a lot for the idea of using a bash script, but unfortunately yours doesn't seem to work. 
When I run it inside the directory, I get a lot of these sorts of errors:

```
zip error: Nothing to do! (Duel.zip)
	zip warning: name not matched: Stories

zip error: Nothing to do! (Stories.zip)
	zip warning: name not matched: (U).gbc

zip error: Nothing to do! ((U).zip)
	zip warning: name not matched: Zebco

zip error: Nothing to do! (Zebco.zip)
	zip warning: name not matched: Fishing!

zip error: Nothing to do! (Fishing!.zip)
	zip warning: name not matched: (U).gbc

zip error: Nothing to do! ((U).zip)
	zip warning: name not matched: Zoboomafoo

zip error: Nothing to do! (Zoboomafoo.zip)

zip error: Invalid command arguments (short option '.' not supported)
	zip warning: name not matched: Playtime

zip error: Nothing to do! (Playtime.zip)
	zip warning: name not matched: in

zip error: Nothing to do! (in.zip)
	zip warning: name not matched: Zobooland

zip error: Nothing to do! (Zobooland.zip)
	zip warning: name not matched: (U).gbc
```


I don't really know enough about bash to know what the problem is, but I've been looking around trying to learn how it all works.

Do you know why it wouldn't be working?

---

### Post by SeijiSensei on 2010-12-02
Perhaps you don't have zip installed?  (sudo apt-get install zip)

---

### Post by rfry11 on 2010-12-02
Just checked - I've got the newest version.

---

### Post by DaithiF on 2010-12-03
the script above won't work for files with spaces in the names (of which you have plenty).

an improved version would be something like:

```
#!/bin/bash

for file in *.gbc
do
  zip "${file}.zip" "$file" 
done

```

---

### Post by KiLaHuRtZ on 2010-12-03
How about a one line'r ... ;)

```
ls /path/to/your/roms | grep .gbc | while read file; do zip "${file}".zip "${file}"; done
```

---

### Post by DaithiF on 2010-12-03
why use 2 external commands ls and grep to do what the shell itself can do?

```
for file in *.gbc; do zip "${file}.zip" "$file"; done

```

---

### Post by KiLaHuRtZ on 2010-12-03
No wrong way to do it. :-k That's the beauty of *NIX!

You could compile a file list first and use cat instead of ls and pipe that into a while loop.

---

### Post by KiLaHuRtZ on 2010-12-03
Or, use caution, ...

```
locate .gbc | while read file; do zip "${file}".zip "${file}"; done
```

---

### Post by rfry11 on 2010-12-03
Wow guys, thanks a lot.

I started from the last post, made by KiLaHuRtZ, but unfortunately his command...

```
locate .gbc | while read file; do zip "${file}".zip "${file}"; done
```

...failed to do anything, no errors or anything.

However, DaithiF's command...

```
for file in *.gbc; do zip "${file}.zip" "$file"; done
```

...works perfectly, and did exactly what I was looking for!

I did not test the other two that you guy's posted, I think DaithiF's command is as simple as you can get, and it'll definitely help out if I ever have a problem like this again.

And, thanks a lot, and I'm going to mark this as solved.

---

### Post by KiLaHuRtZ on 2010-12-03
Glad to hear it!  DaithiF's is simpler for a single directory.  The last one I posted should find all files with ".gbc" included in the string and zip them.  Since it didn't work for you, my guess is that you power down often and may need to update the DB for the system to find them.  Hence, run this first...

```
sudo updatedb
locate .gbc | while read file; do zip "${file}".zip "${file}"; done
```

---

### Post by rfry11 on 2010-12-04
Ah yes, your command does work now. Thanks a lot for explaining that little problem.

Just to simplify for anyone stumbling over this in the future:

If all of the files you want to Zip are located in one directory, run this command:

```
for file in *.gbc; do zip "${file}.zip" "$file"; done
```

...And if the files you want to Zip are located in various directories, run this command:

```
sudo updatedb
locate .gbc | while read file; do zip "${file}".zip "${file}"; done
```


In the event you want to Zip files that are not .GBC files, replace .GBC with their file extension.

And of course, a lot of thanks to KiLaHuRtZ and DaithiF!

---

