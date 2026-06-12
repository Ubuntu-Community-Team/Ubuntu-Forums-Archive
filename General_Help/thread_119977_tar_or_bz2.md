---
title: "tar or bz2"
date: 2006-01-20
forum: General Help
---

### Post by closeyourwindows on 2006-01-20
I am having problems using tar -cvfj <filename> <directory> and was looking for some suggestions.  what is the best way to do a backup.  I did see the threads on here but I get the same errors no matter what. 
```
tar: Error exit delayed from previous errors 
``` 

[http://www.ubuntuforums.org/showthread.php?t=119310&highlight=backup+home](http://www.ubuntuforums.org/showthread.php?t=119310&highlight=backup+home)

[http://www.ubuntuforums.org/showthread.php?t=35087&highlight=backup+home](http://www.ubuntuforums.org/showthread.php?t=35087&highlight=backup+home)

but I was hoping that someone could shed a little light on this process. what I am attempting is backing up the .icons .themes .wine so that that I can reinstall ubuntu 5.10 because I no longer have wireless access and no longer have access to samba, (a different thread)

I have been able to create tars and Zips in fedora and was wondering if anything is different

---

### Post by GeneralZod on 2006-01-20
Please type the exact command you are giving, together with all resulting output.

---

### Post by closeyourwindows on 2006-01-20
```
nate@solo:~/Desktop/backups$ sudo tar -cvzf backup4.tar.gz .themes .icons. wine
```
the directories were copied to a folder on the desktop

---

### Post by 5-HT on 2006-01-20
Not positive, but I believe that the -f option needs to be at the end (tar -cvzf for a gzip archive, tar -cvjf for a bz2).
I find it best to just copy everything I want in the tarball to a folder, and then just tar the folder itself.

HTH

*EDIT: Ya beat me to it, so you got it to work?

---

### Post by GeneralZod on 2006-01-20
[QUOTE=closeyourwindows]```
nate@solo:~/Desktop/backups$ sudo tar -cvzf backup4.tar.gz .themes .icons. wine
```
the directories were copied to a folder on the desktop[/QUOTE]

I don't see anything wrong here (except that you are trying to copy a file/ folder called ".icons**.**" - is that right?); can you post the *complete* output, please? Also, please post the output of 

```

ls -l 

```

separately.

---

### Post by closeyourwindows on 2006-01-20
```
nate@solo:~$ tar -czf backup0.tar.gz /home/nate/Desktop/backups/
tar: Error exit delayed from previous errors
nate@solo:~$
```

I am not sure why but I can do this command if it is on file but not a directory..

---

### Post by GeneralZod on 2006-01-20
[QUOTE=closeyourwindows]```
nate@solo:~$ tar -czf backup0.tar.gz /home/nate/Desktop/backups/
tar: Error exit delayed from previous errors
nate@solo:~$
```

I am not sure why but I can do this command if it is on file but not a directory..[/QUOTE]

Odd.  Does  backup0.tar.gz exist already? What is the output of 

```

ls -l /home/nate/Desktop/backups/

```

Also, try the tar command with a v in between the z and the f, and post the output of that e.g.

```

tar -czvf backup0.tar.gz /home/nate/Desktop/backups/

```

---

### Post by lamego on 2006-01-20
I am afraid your backup maybe corrupt, please list its contents first with:

tar -tzvf backup0.tar.gz

If you get an error, check if the file is in fact a gzipped tar with the command:
  file backup0.tar.gz

---

### Post by shane2peru on 2006-01-20
I thought this was about tar or bz2....  I found this nice post on backing up and restoring.  [http://www.ubuntuforums.org/showthread.php?t=81311&highlight=backup+restore](http://www.ubuntuforums.org/showthread.php?t=81311&highlight=backup+restore) 
I have used this method a few times nad it has worked like a charm.  The only other thing is that you need to put the destination at the end of the command.  Hope this helps.

Shane

---

### Post by closeyourwindows on 2006-01-20
it does show in the home directory and it is 1 GB in size so to show the -v would take up some space.  

this was the file that gave me the error but wheb I did this:
```
tar -tzvf backup0.tar.gz
-rwxrwxr-x nate/nate 505331712 2005-10-13 14:40:03 home/nate/Desktop/backups/vmware/Xpress 6.5/Xpress6.5.iso
nate@solo:~$

```
I also got about 500 other files but the last one was that and that was the one that put out the error
so I tried other files and folders and I can do some like this:
```
nate@solo:~$ tar -cvzf backup1.1.tar.gz Desktop/altbackup/
Desktop/altbackup/
Desktop/altbackup/globe-yellow.xcf
Desktop/altbackup/globe-red-selected.xcf
Desktop/altbackup/globe-red.xcf
Desktop/altbackup/globe-purple.xcf
Desktop/altbackup/globe-orange.xcf
Desktop/altbackup/globe-green.xcf
Desktop/altbackup/globe-blue.xcf

```
and others I cant like this:

well, I was trying to make it malfunction but I see a pattern now.  is it possible to tar an iso file?

---

### Post by GeneralZod on 2006-01-21
[QUOTE=closeyourwindows]
well, I was trying to make it malfunction but I see a pattern now.  is it possible to tar an iso file?[/QUOTE]

You can tar any file you want.

Do you have enough space on your /home/nate partition?

---

### Post by Zalbor on 2006-01-21
Does the graphical tool work? It's in Applications>Accessories. Even if you definitely want to use a terminal command, at least this will let you know if it's something you are doing wrong or something wrong with the system.

---

