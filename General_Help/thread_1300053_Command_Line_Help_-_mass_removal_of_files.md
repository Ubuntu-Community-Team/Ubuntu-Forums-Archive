---
title: "Command Line Help - mass removal of files"
date: 2009-10-24
forum: General Help
---

### Post by solwic on 2009-10-24
I have a 320GB external hard drive that has a whole bunch of files I want to get rid of.  Now, I know I can find these files in the terminal, like so:

```
sudo find /media/MyBook/ -name *filename*
```

Each file contains the same word somewhere in the file name, so that command works.  

What I want to know is, how can I use the results of that "find" command and feed it into the "rm" command to delete all those files for me?  

Any help would be greatly appreciated.  :)

---

### Post by golanbatrac on 2009-10-24
If all of the files are in the same directory, you shouldn't have to use the find command at all.

```

sudo rm -i /media/MyBook/*filename*

```

---

### Post by solwic on 2009-10-24
> **golanbatrac said:**
> If all of the files are in the same directory, you shouldn't have to use the find command at all.

```

sudo rm -i /media/MyBook/*filename*

```

They're all on the drive, but are scattered throughout different directories. That's why I used the "Find" command in the first place; I wasn't sure where they all were (my external drive is a mess, and I'm trying to clean it up today hehe). 

I'm not very familiar with the intricacies of the CLI, though, so I wanted to make sure before I inadvertently trashed the whole drive.

Will the command you gave work since the files are scattered?  And what's that "-i" option? 

Thanks. :)

---

### Post by howefield on 2009-10-24
The help page is man rm

 -i     prompt before every removal

---

### Post by sisco311 on 2009-10-24
First make sure that the find command returns the files you want to delete.

Make sure that the trash works on the partition:

create a file
```
> /media/MyBook/test-trash
```

move it to the trash:
```
trash /media/MyBook/test-trash
```

list the trash:
```
list-trash
```

if the file is in the trash move the unneeded files to the trash:
```
find /media/MyBook/ -type f -name *filename* -exec trash '{}' \;
```

to empty the trash:
```
empty-trash
```

to restore the files:
```
restore-trash
```


NOTE: you may have to install trash-cli:
```
sudo apt-get install trash-cli
```

---

