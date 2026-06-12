---
title: "Removing duplicate files"
date: 2009-11-09
forum: General Help
---

### Post by Neezer on 2009-11-09
So, I think there is a command line way to do this....

I got a music folder from a friend, and there are a lot of duplicate files in it. Is there a command I can use to remove any file that is a duplicate even if it is in a different folder?

On a side note, there are also a lot of album art files that I don't want. I tried things like 
```

rm *.jpg
rm -r *.jpg
rm -R *.jpg

```

actually I didn't use the rm code, I used the ls code to see what I was going to remove first, but nothing came up.

Any suggestions?

---

### Post by bchurchill on 2009-11-09
For the album art, try doing this:

find -name "*.jpg" -print0 | xargs -0 echo

It should list all the files you want to remove.  If indeed you decide you actually want to remove them all (be sure!) you can run

find -name "*.jpg" -print0 | xargs -0 rm

The 'find' command will recursively find all the files ending in .jpg.  The xarg command passes the results on to another program.  Hence, echo displays them all, and rm removes them all.  The reason 'rm -r *.jpg' does not work is that rm -r is used to recursively delete entire folders, not to recursively search for files to delete.  Hope that helps!

----------

The duplicate files issue seems trickier in my opinion.  I think the find command could help you out here as well, but I'm not exactly sure.  It may take some clever scripting, but here's a place to start:

find -type f -print0 | xargs -0 -n1 du | sort | cut -f2-

This will place files that are of the same size next to each other, so duplicates should show up next to each other as well.  It should run quickly.  A more precise method will get exact duplicates, but could take much longer to run if you have a lot of music: 

find -type f -print0 | xargs -0 -n1 md5sum | sort | cut -f2-

The "-type f" option specifies only files will be found (not directories).  du finds the size of a file.  sort takes the output from du and sorts it (so the files are sorted by size).  cut -f2- removes the filesizes from the list.  At least now identical files of the same size should be next to each other, and maybe from this you can come up with a way to remove the ones  you want.... good luck!

---

### Post by Neezer on 2009-11-09
So I got all kinds of stuff when I used the find code for the .jpg files.....It would take me weeks to read through it all....

I am in /media/My Passport/Music.

I have lots of Pictures in /media/My Passport/"a few other folders with pictures"

If I run the remove code in the /media/My Passport/Music directory, will I remove any files that are higher up on the tree than the music directory?

---

### Post by bchurchill on 2009-11-09
If you run the remove code in /media/My Passport/Music it will not remove any higher up files; in particular your pictures in /media/My Passport will be fine.

A nicer way to preview the files before deletion is just

find -name "*.jpg"

you don't need to read through all of them - just get a sense for what's being deleted.  It should be exactly the files you want to delete.

---

### Post by Neezer on 2009-11-09
Worked great!!! Thank You!

I know some people like it, but I don't have any need or want for album art...now on to the hard task of removing duplicate files...

The problem with your method of listing them by filesize is that they are all songs that are probably pretty close to each other in size.

But I'm determined to learn how to do this via command line rather than hours of looking through folders manually and clicking to delete.

again, thanks a lot for the fast response and the help.

---

### Post by Neezer on 2009-11-09
Well, I think I found the answer to finding the duplicates!

I used fdupes from this site
[http://embraceubuntu.com/2005/10/08/find-duplicate-copies-of-files/](http://embraceubuntu.com/2005/10/08/find-duplicate-copies-of-files/)

just used 
```

sudo apt-get install fdupes

```

then
```

nathan@lappy:~$ fdupes -R /media/'My Passport'/Music > dupes.txt
nathan@lappy:~$ gedit dupes.txt

```

worked like a charm for finding them. But it didn't delete any of them so I have been going through checking to make sure they are duplicates and it seems to work really well. I didn't find any on the list that weren't duplicates.

I did find some license files that I wasn't sure if I could delete though....There was a folder called License Backup

It has 4 different files in it named:
drmv1key.bak
drmv1lic.bak
drmv2key.bak
drmv2lic.bak

Can I delete these files???

---

### Post by Bonster on 2009-11-10
i use fslint, is a gui to remove dupes files ..etc

---

