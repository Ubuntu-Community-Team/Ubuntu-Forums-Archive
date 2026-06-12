---
title: "Extracting .tar.gz files"
date: 2011-03-22
forum: General Help
---

### Post by Spyderkid on 2011-03-22
I want to extract a .tar.gz file, but the tar command is too confusing for me to use now, could you tell me how to use tar or a different command please :)

---

### Post by wojox on 2011-03-22
Right click, Extract here.

---

### Post by Ghost_Mazal on 2011-03-22
Basic extraction command:


```
tar -xzvf /path/to/tarfilename
```

---

### Post by Spyderkid on 2011-03-23
I tried using tar -xzvf but i got errors....

```

$ tar -xzxf 128922-Colors.tar.gz Documents
tar: Documents: Not found in archive
tar: Exiting with failure status due to previous errors

```

---

### Post by WorMzy on 2011-03-23
Don't specify an output location, tar doesn't accept one.

Read through
```
man tar
```
if you want to see what options are available for use with the tar command.

---

### Post by TeoBigusGeekus on 2011-03-23
If the path is /home/yourusername/Documents and the filename is 128922-Colors.tar.gz, then
```
tar xvf ~/Documents/128922-Colors.tar.gz
```
~/: shortcut to /home/yourusername/
The z switch is not needed.
You made a mistake: you used the x switch twice.

---

### Post by tgm4883 on 2011-03-23
> **Spyderkid said:**
> I tried using tar -xzvf but i got errors....

```

$ tar -xzxf 128922-Colors.tar.gz Documents
tar: Documents: Not found in archive
tar: Exiting with failure status due to previous errors

```

Thats because Documents doesn't exist in the archive, so you can't extract it.

You want to add the '-C <directory>' option

```
man tar
```
FTW

---

### Post by sisco311 on 2011-03-23
You can use atool. It's in the repositories.

```
atool -X ~/Documents path/to/archive
```

You could use its --simulate option to learn the syntax of the various archive utilities:
```

sisco@acme:~$ atool --simulate -X ~/xtmp/ expect5.45.tar.gz 
tar xvzf expect5.45.tar.gz -C /home/sisco/xtmp/

```

For more options, check out the man page:
```
man atool
```

---

### Post by Spyderkid on 2011-03-23
[edit out]

---

### Post by sisco311 on 2011-03-23
As tgm4883 already mentioned it, you have to use the -C optin. 

Assuming that the name of archive is file.tar.gz (it's in the current working directory) and you want to extract it to ~/Documents:
```
tar xfvz file.tar.gz -C ~/Documents
```

---

### Post by Spyderkid on 2011-03-24
I used atool instead :)

---

### Post by jerome1232 on 2011-03-24
I missed where just right clicking and click extract here wasn't an option, or double clicking the archive and extracting to where you want it extracted.

---

### Post by sisco311 on 2011-03-24
> **Spyderkid said:**
> I used atool instead :)

Cool!

Don't forget to mark this thread as [SOLVED]. Thanks!

---

### Post by Spyderkid on 2011-03-25
Sorry the key bit of information was, In the command line.

---

