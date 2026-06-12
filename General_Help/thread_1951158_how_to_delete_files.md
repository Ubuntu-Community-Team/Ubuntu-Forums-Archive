---
title: "how to delete files ?"
date: 2012-04-02
forum: General Help
---

### Post by winzip on 2012-04-02
I want to delete files under a specific directory within a zip file.

Whats the command ?


For example ,
I wish to delete all  files under "lib" diretory

Is it a correct command ?  
zip -d  archieve.zip |grep "/com/lib"


I'm not sure . Please correct me ...how do I remove  files from a directory within a zip file.

---

### Post by zeljkojagust on 2012-04-02
Why don't you unzip files, delete ones you don't need, and zip the rest again. I think it's very logical.

---

### Post by Bucky Ball on 2012-04-02
Not sure of the command but think you need a space after the pipe:
```

zip -d  archieve.zip | grep "/com/lib"
```

---

### Post by winzip on 2012-04-02
> **zeljkojagust said:**
> Why don't you unzip files, delete ones you don't need, and zip the rest again. I think it's very logical.

No.  it may not be useful for me. because ...

I  have a folder. //dont delete anything from this original folder.

I  have zipped that folder. [COLOR="Blue"]//done[/COLOR]

**[COLOR="Red"]I  want to remove few  files from that zipped folder.[/COLOR]** // [COLOR="Blue"]I'm stuck at this part[/COLOR]

I  want to do SSH transfer this zipped archieve to another destination

---

### Post by winzip on 2012-04-02
> **Bucky Ball said:**
> Not sure of the command but think you need a space after the pipe:
```

zip -d  archieve.zip | grep "/com/lib"
```

This does not work. I  have checked it.

comments please

---

### Post by Dave_L on 2012-04-02
Have you seen the examples in the man page under the description of the -d/--delete option?

This is from the man page for 10.04:

[http://manpages.ubuntu.com/manpages/lucid/en/man1/zip.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/zip.1.html)

>  -d
       --delete
              Remove (delete) entries from a zip archive.  For example:

                     zip -d foo foo/tom/junk foo/harry/\* \*.o

              will  remove the entry foo/tom/junk, all of the files that start
              with foo/harry/, and all of the files that end with .o  (in  any
              path).   Note  that  shell pathname expansion has been inhibited
              with backslashes, so that zip can see  the  asterisks,  enabling
              zip  to  match on the contents of the zip archive instead of the
              contents of the current directory.   (The  backslashes  are  not
              used  on  MSDOS-based platforms.)  Can also use quotes to escape
              the asterisks as in

                     zip -d foo foo/tom/junk "foo/harry/*" "*.o"

              Not escaping the asterisks on a system where the  shell  expands
              wildcards  could  result  in  the asterisks being converted to a
              list of files in the current directory and  that  list  used  to
              delete entries from the archive.

              Under  MSDOS,  -d is case sensitive when it matches names in the
              zip archive.  This requires that file names be entered in  upper
              case  if  they  were  zipped  by  PKZIP on an MSDOS system.  (We
              considered making this case insensitive on systems  where  paths
              were  case insensitive, but it is possible the archive came from
              a system where case does matter and the  archive  could  include
              both Bar and bar as separate files in the archive.)  But see the
              new option -ic to ignore case in the archive.

---

### Post by winzip on 2012-04-02
> **Dave_L said:**
> Have you seen the examples in the man page under the description of the -d/--delete option?

This is from the man page for 10.04:

[http://manpages.ubuntu.com/manpages/lucid/en/man1/zip.1.html](http://manpages.ubuntu.com/manpages/lucid/en/man1/zip.1.html)


>>>zip -d [COLOR="Red"]foo [/COLOR]foo/tom/junk foo/harry/\* \*.o

Is not this should be [COLOR="Red"]foo.zip[/COLOR]

---

### Post by Dave_L on 2012-04-02
> Should this be foo.zip?

The example is correct. If no extension is specified, .zip is assumed.

---

### Post by HiImTye on 2012-04-03
I believe the switch you are looking for is -m
```
       -m
       --move
              Move the specified files into the zip archive; actually, this deletes the target directories/files after making the specified zip archive. If a directory becomes empty after  removal  of  the
              files,  the  directory is also removed. No deletions are done until zip has created the archive without error.  This is useful for conserving disk space, but is potentially dangerous so it is
              recommended to use it in combination with -T to test the archive before removing all input files.
```
for instance:
```
zip -m myfile file1 file2 file3 etc
```
if you want to add files to it after creating it then you can use -a:
```
zip -a -m myfile file4 file5 file6 etc
```

---

