---
title: "How to Delete Un-Identified Characters File?"
date: 2011-03-01
forum: General Help
---

### Post by jaya28inside on 2011-03-01
Hello everyone...! :KS

I just found out that I did mistake.
I transfer 1 file into the Ubuntu Linux,
but that File has a strange character. Take a look at the picture screenshot taken.

[[img]http://s3.postimage.org/pp5k353fa/How_To_Delete_Un_Identified_Characters.png[/img]](http://postimage.org/image/vw02hk1w/full/)
[free image hosting](http://www.postimage.org/)

Explanation: 

1) The file name is *unknown*, take a look at the WinRAR Archive (left window)
2) The file name recognized in Ubuntu without any name, thus it appeared as Empty (right window: putty program). And via Command Line Interface, it appeared as Question Marks... A lot of Question Marks... Oh My God.


Anyway, how could I remove that file?
Since I dunno what to type, even the name I can't type it. :(

---

### Post by jwcalla on 2011-03-01
What does it look like in Nautilus?  Can you select it and delete it?

---

### Post by jaya28inside on 2011-03-03
> **jwcalla said:**
> What does it look like in Nautilus?  Can you select it and delete it?

Hah, nautilus? wats dat? never tried...
anyway, I don't have GUI...

it's all CLI (command line interface),
so i should get it done via Command only.

anyway, wat's the clue that I could achieved? :(

---

### Post by apmcd47 on 2011-03-03
```
rm -i *
```should prompt you to delete every file in the current directory. Type _n_ to all the files you want to keep and _y_ to the file with the peculiar characters.

Tar up the directory first, in case of finger trouble :)

Andrew

---

### Post by jaya28inside on 2011-03-03
> **apmcd47 said:**
> ```
rm -i *
```should prompt you to delete every file in the current directory. Type _n_ to all the files you want to keep and _y_ to the file with the peculiar characters.

Tar up the directory first, in case of finger trouble :)
Andrew

**Exactly**,...! Nice shot...!  :D

Yes by using that command it will delete all the files within that current directory, 
and guess what? The Question Marks or the un-identified characters now seems identified... lol.

Take a look at this screenshot...
Instead of Question Marks, now it's identified....
as numerical form naming... 
```
\322\361\341\275\277 \274?\264 
```

[ [img]http://www.4freeimagehost.com/resized/cc5dc64c2410.png[/img]](http://www.4freeimagehost.com/show.php?i=cc5dc64c2410.png)

Problem solved! :D thanks, **apmcd47**.

---

### Post by Habitual on 2011-03-03
To find the inode number of a file, list the directory with the -i option:

```
ls -i
```
2064227 test

2064227 is the inode number of the file ‘test’.
Use the find command to delete the file by it’s inode number:
```
find . -inum 2064227 -exec rm {} \;
```

done.

---

