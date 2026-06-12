---
title: "I can't find a .txt file!! :("
date: 2010-07-08
forum: General Help
---

### Post by t0p on 2010-07-08
I'm looking for a file on my computer.  It's in .txt format, and was created/last modified on Wed 7 Jul or Thu 8 Jul.  It's either in my /home folderr, ot possibly /media/disk.  But I can't find it!!  The command

```

sudo find / -name *.txt

```
creates a huge, unwieldy list that I can't get through.
What do I need to do?

---

### Post by Telengard C64 on 2010-07-08
> **t0p said:**
> It's either in my /home folderr, ot possibly /media/disk.

I'm pretty sure you don't have to search the entire system if you know the file was in one of those two dirs. Find will accept multiple paths to search from. Also, you need to quote that wildcard character so your shell doesn't eat it.

```
$ find $HOME /media/disk -name \*.txt
```

Another thing to try is grep recursively. For this to work you need to remember some text from inside the file.

```
$ cd /media/disk
$ grep -iR 'TEXT YOU REMEMBER' *
```

---

### Post by prshah on 2010-07-08
> **t0p said:**
> It's in .txt format, and was created/last modified on Wed 7 Jul or Thu 8 Jul

Try ```
sudo find / -iname "*.txt" -atime -2 -type f
```

"atime" indicates access time. This will still list a whole bunch of files, since indexing and other utilites will access files. Rather than search "/" I'd suggest you try two searches, one on "/home" and one on "/media".

If you remember part of the contents of the file, you can additionally use grep to search more effectively; eg```
find ~ -iname "*.txt" -atime -2 -type f -execdir grep -i "sometext" "{}" \;
```

Please post back if you need a detailed explanation of the commands.

---

