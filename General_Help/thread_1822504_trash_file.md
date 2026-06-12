---
title: "trash file"
date: 2011-08-10
forum: General Help
---

### Post by lazerking9 on 2011-08-10
I'm writing a script that tidies up my system before it shuts down. One of the things I would like it to do is clear my Trash..
```
 rm /path/to/trash/* 
```
 but I can't find the path to the trash. Anybody know where it is?

---

### Post by kvaadithya on 2011-08-10
Please check: /home/<your-username>/.local/share/Trash.

This directory contains 2 sub-folders: files and info. files stores the actual files that you moved to the trash, while info stores metadata about each file in the files folder (including where the file was deleted from, etc.).

So, in your script, you should have something like:

```

$ rm -rf /home/<your username>/.local/share/Trash/files/*
$ rm -rf /home/<your username>/.local/share/Trash/info/*

```

Hope this helps!

---

### Post by lazerking9 on 2011-08-12
Thanks alot! That worked great!

---

### Post by raja.genupula on 2011-08-12
> **kvaadithya said:**
> Please check: /home/<your-username>/.local/share/Trash.

This directory contains 2 sub-folders: files and info. files stores the actual files that you moved to the trash, while info stores metadata about each file in the files folder (including where the file was deleted from, etc.).

So, in your script, you should have something like:

```

$ rm -rf /home/<your username>/.local/share/Trash/files/*
$ rm -rf /home/<your username>/.local/share/Trash/info/*

```

Hope this helps!


i tried as you said but i got this 

assassin@genupulas:~$ rm -rf /home/assassin/.local/share/Trash/files/*
assassin@genupulas:~$ rm -rf /home/assassin/.local/share/Trash/info/*

i mean nothing i got , i have some data in trash i.e a folder .but i got no info .

---

### Post by kvaadithya on 2011-08-12
Why would you expect to get any info?

rm -rf just deletes everything in the specified directory; it wouldn't ordinarily give you information about the files it is deleting. If you want more info, try rm -rvf instead of rm -rf.

Check the trash icon on the desktop after the rm commands; it should be empty.

---

### Post by raja.genupula on 2011-08-12
no not empty man 
rm -rvf /home/assassin/.local/share/Trash/files/*

---

### Post by Wim Sturkenboom on 2011-08-13
```

fortyfourgalena@desktop-01:~$ rm -rvf /home/fortyfourgalena/.local/share/Trash/info/*
removed `/home/fortyfourgalena/.local/share/Trash/info/01 - Love is the Drug.ogg.trashinfo'
removed `/home/fortyfourgalena/.local/share/Trash/info/02 - End of the Line.ogg.trashinfo'
removed `/home/fortyfourgalena/.local/share/Trash/info/03 - Sentimental Fool.ogg.trashinfo'
removed `/home/fortyfourgalena/.local/share/Trash/info/04 - Whirlwind.ogg.trashinfo'
removed `/home/fortyfourgalena/.local/share/Trash/info/05 - She Sells.ogg.trashinfo'
removed `/home/fortyfourgalena/.local/share/Trash/info/06 - Could it Happen to Me.ogg.trashinfo'
...
...

```
Ran the one on 'files' before the above and it actually emptied the trash (icon went empty).

Check who owns the files in your thrash.

---

### Post by raja.genupula on 2011-08-13
aah! finally got it , thanks to all .

```
assassin@genupulas:~$ rm -rvf /home/assassin/.local/share/Trash/info/*
removed `/home/assassin/.local/share/Trash/info/Screenshot.png.trashinfo'

```

---

### Post by JonasPed on 2011-08-13
> **raja.genupula said:**
> ```
assassin@genupulas:~$ rm -rvf /home/fortyfourgalena/.local/share/Trash/files/*

``````
assassin@genupulas:~$ rm -rvf /home/fortyfourgalena/.local/share/Trash/info/*

```

i have created some file and placed it to trash and then tried your command . i got nothing

Looks like you are logged in as assassin. Would it not be rm -rvf /home/**assassin**/.local/share/Trash/info/* instead?

---

