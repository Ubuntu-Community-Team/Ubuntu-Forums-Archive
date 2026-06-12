---
title: "How to extract multiple rar files at once ?"
date: 2010-09-11
forum: General Help
---

### Post by Dl1981 on 2010-09-11
Can anyone help me find a software similiar to [http://www.extractnow.com/](http://www.extractnow.com/) whit gui for ubuntu ?

 or some kind of nautilus script ?

---

### Post by WorMzy on 2010-09-11
[LIST=1]
[*]Select all archives
[*]right click one
[*]choose "extract here"
[*]there is no step 4
[/LIST]

---

### Post by howefield on 2010-09-11
If you haven't already got rar and unrar, install them with the terminal command..

```
sudo apt-get install rar unrar
```

and then navigate to where your rar files are and use the following command.  

```
for f in *.rar;do unrar e $f;done
```

Extracted from [http://www.howtogeek.com/howto/ubuntu/unzip-or-unrar-many-files-at-once-in-linux/](http://www.howtogeek.com/howto/ubuntu/unzip-or-unrar-many-files-at-once-in-linux/)

---

### Post by Dl1981 on 2010-09-11
[@ howefield]("http://ubuntuforums.org/member.php?u=186490")

 will that work whit for example.

 s01 of tvshow xxxx

 s01.ep1
s01.ep2
etc...

 will it unrar all the folders at once, or will i need to enter each episode folder to extract them ?

 Thats the essence of extract-now

---

### Post by howefield on 2010-09-11
> **Dl1981 said:**
> will it unrar all the folders at once, or will i need to enter each episode folder to extract them ?

It will extract all the rar files in the folder that you run it.

Let's say you have a folder with all the episodes in it - in rar format. Run the command and they will all be extracted.

WorMzys way also works, using archive manager, (again assuming you have rar and unrar installed).

---

### Post by Dl1981 on 2010-09-12
just perfect my friends, perfect *****

---

### Post by nooodles on 2011-03-14
Thanks Thread - it didn't occur to me that rar/unrar was not installed by default.  
Corrupted RAR is no longer corrupted. :popcorn:

---

### Post by Aquix on 2011-03-14
If it's video then you can play the *.rar file directly when unrar package is installed.

---

### Post by magnetic651 on 2011-03-27
None of these solutions are working for me.  I have installed rar and unrar, but I cannot select the files and right click and choose extract.  I get an error message when trying:

for f in *.zip;do unzip “$f”;done

unzip:  cannot find or open “XXX, “XXX.zip or “XXX.ZIP.

for every file.

Suggestions?  Help?

---

### Post by magnetic651 on 2011-03-27
If I try "unzip *.zip" I get:

caution: filename not matched:  XXX.zip

---

### Post by beew on 2011-03-27
> **magnetic651 said:**
> None of these solutions are working for me.  I have installed rar and unrar, but I cannot select the files and right click and choose extract.  I get an error message when trying:

for f in *.zip;do unzip “$f”;done

unzip:  cannot find or open “XXX, “XXX.zip or “XXX.ZIP.

for every file.

Suggestions?  Help?

You have to cd into the directory where you store your files. If they are on the desktop then you have to first run
```

cd Desktop
```

Note the capital D.

---

### Post by magnetic651 on 2011-03-27
Yes, I am in the directory where the files are located.

ls lists the files I want extracted, being in the wrong directory is not the problem.

---

### Post by magnetic651 on 2011-03-27
Krusader did the trick.

---

