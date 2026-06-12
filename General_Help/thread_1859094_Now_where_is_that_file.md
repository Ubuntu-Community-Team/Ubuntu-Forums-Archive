---
title: "Now where is that file?"
date: 2011-10-13
forum: General Help
---

### Post by stillcen on 2011-10-13
the specific problem is that the "Movie Player" has a bunch of usless and broken things under its list of movies.
    -went to "Movie Player" help to discover it was/is called totem.
went to synaptic and removed the 8 installed listings,  then reinstalled.
    All the junk is still on the list...grump.
Went to properties to try to discover were the program is hanging out on the hard drive. and could not find a fild path
    did a search for totem and still could not find out where the program was lurking. (search program Beagle 0.3.9)
   Tried the bludging method  and look through the file system,  no luck.

Any suggestions as how to delete, delete, delete.



The gerneral issue,  About 1/2 the time i can not find out where a file is.  Even under properties file paths are not always listed.  I am/was used to DOS 2.11,  leaving me with the innate need to know where every thing is.  My friend who set me up with unbuntu just says, let it go man.   I get the difference between DOS and Unbuntu file placement but; frustrating living with my ignorance.

---

### Post by smurphy_it on 2011-10-13
Try some of the following:

```
dpkg --get-selections |grep totem
```
Above command will see if totem has been installed through your package manager.  If it has, it should indicate it is "installed".

If installed, do a: 
```
which totem
```
That should point to the binary (assuming your PATH is setup right).

Otherwise, I'd do a search for it:
```
sudo find / -name totem
```

Cheers

---

### Post by WasMeHere on 2011-10-13
Hello stillcen,

I was also around at the time of DOS, Norton Commander, autoexec.bat and config.sys. It takes some time to learn the filesystem of linux and the command line tools, but believe me, it has actually been around longer (unix), and it is more powerful. If you really want to find a file, use *find*. See ```
man find
``````
find . -name \*.jpg
``` looks in the directory tree of the current directory. To avoid error output because you have not read access, run as superuser.
```
sudo find / -name totem
``` looks in all directories, but for executable files in $PATH it is faster to use
```
which totem
```

Have fun finding out about linux :-)
Olle

---

### Post by stillcen on 2011-10-13
Thanks for replies i have new tools to find files,  now if i just know what they all did.


enjoy

stillcen

---

### Post by crdlb on 2011-10-13
What "list of movies" are you talking about? The recent files list under the Movie menu? If so, that is stored in ~/.local/shared/recently-used.xbel

---

