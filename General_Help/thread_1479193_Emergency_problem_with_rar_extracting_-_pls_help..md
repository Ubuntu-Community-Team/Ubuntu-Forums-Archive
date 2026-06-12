---
title: "Emergency problem with rar extracting - pls help."
date: 2010-05-10
forum: General Help
---

### Post by spokoen on 2010-05-10
[B]Emergency problem with rar extracting - pls help.

[/B]Hello my friends. I'm with the last version of Ubuntu. I have installed "unrar", but again i have problems when extracting rar files! When i press right click i see the progress of extracting, but after that NO files displayed at the folder. So extracting, so no one files comes up. Please help me - emergency!

---

### Post by joeknoodle on 2010-05-10
> **spokoen said:**
> [B]Emergency problem with rar extracting - pls help.

[/B]Hello my friends. I'm with the last version of Ubuntu. I have installed "unrar", but again i have problems when extracting rar files! When i press right click i see the progress of extracting, but after that NO files displayed at the folder. So extracting, so no one files comes up. Please help me - emergency!

Maybe try to unpack to a new folder, and move files where necessary.

---

### Post by spokoen on 2010-05-10
I tried to extract them to a new folder. I've installed "ark", but i still have the same problem!
I see the hole progress of extracting, but in the end no files in the folder! What did i have to do?

---

### Post by Portmanteaufu on 2010-05-10
Could you please try running unrar from the command line? If something is going wrong at the end of the extraction, the error message will show up there and it will be easier for us to help you. 

Steps:

Move the .rar file to your home directory. (Places -> Home)

Click Applications --> Accessories --> Terminal. You should see a prompt open. Type:

```

unrar -e yourfile.rar

```

Copy/paste what it prints out in a post. Thanks!

---

### Post by spokoen on 2010-05-10
Please write again the command if the filename is a.rar and it is in the folder documents.
I write unrar -e a.rar, but it is wrong.

ton@ton-lpt:~$ unrar -x a.rar

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/ton/a.rar

Extracting  prezentaciq.pyrva.kurs.korekciq.pptx                      Failed    
Extracting  prezentaciq.kolegium.25.11.09.pptx                        Failed    
Extracting  prezentaciq.original.za.korekciq.pptx                     Failed    
3 Failed

---

### Post by Portmanteaufu on 2010-05-10
Please post the output of:

```

cd ~/Documents
ls -l
unrar -e a.rar

```

This will show us the file permissions on a.rar in your Documents folder and then try to extract it.

---

### Post by Portmanteaufu on 2010-05-10
> **spokoen said:**
> 
unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


This looks like it's a very old version of unrar. The current version in the repositories is version 3.9, made in 2009.

How did you install unrar?

---

### Post by spokoen on 2010-05-10
ton@ton-lpt:~$ cd Documents
ton@ton-lpt:~/Documents$ ls -l
total 307948
-rw-r--r-- 1 ton ton  14735830 2009-12-27 01:18 a.rar
-rw-r--r-- 1 ton ton 237666116 2008-11-21 00:07 CM_Dx_Tx_09.pdf
-rw-r--r-- 1 ton ton      9860 2010-05-09 21:41 lab4.gif
-rw-r--r-- 1 ton ton      9474 2010-05-09 21:41 lab5.gif
-rw-r--r-- 1 ton ton     12519 2010-05-09 21:41 lab6.gif
-rw-r--r-- 1 ton ton      5804 2010-05-09 21:41 lab7.gif
-rw-r--r-- 1 ton ton    265344 2010-05-09 21:40 labora2007.jpg
-rw-r--r-- 1 ton ton  62611411 2009-11-22 14:51 pediatric infectious diseases.pdf
drwxr-xr-x 2 ton ton      4096 2010-05-10 20:03 snimki prezentaciq
ton@ton-lpt:~/Documents$ unrar -e a.rar
unrar: invalid option -- 'e'
Try `unrar --help' or `unrar --usage' for more information.
ton@ton-lpt:~/Documents$

---

### Post by spokoen on 2010-05-10
pls help!

---

### Post by Portmanteaufu on 2010-05-10
Oops, it's:
```
unrar e a.rar
```

There's no '-' in front of the e.

---

### Post by spokoen on 2010-05-10
ton@ton-lpt:~$ cd Documents
ton@ton-lpt:~/Documents$ ls -l
total 308032
-rw-r--r-- 1 ton ton  14735830 2009-12-27 01:18 a.rar
-rw-r--r-- 1 ton ton 237666116 2008-11-21 00:07 CM_Dx_Tx_09.pdf
-rw-r--r-- 1 ton ton      9860 2010-05-09 21:41 lab4.gif
-rw-r--r-- 1 ton ton      9474 2010-05-09 21:41 lab5.gif
-rw-r--r-- 1 ton ton     12519 2010-05-09 21:41 lab6.gif
-rw-r--r-- 1 ton ton      5804 2010-05-09 21:41 lab7.gif
-rw-r--r-- 1 ton ton    265344 2010-05-09 21:40 labora2007.jpg
-rw-r--r-- 1 ton ton  62611411 2009-11-22 14:51 pediatric infectious diseases.pdf
-rw-r--r-- 1 ton ton     84480 2010-05-10 21:53 prezentaciq_djml.ppt
drwxr-xr-x 2 ton ton      4096 2010-05-10 20:03 snimki prezentaciq
ton@ton-lpt:~/Documents$ unrar e a.rar

unrar 0.0.1  Copyright (C) 2004  Ben Asselstine, Jeroen Dekkers


Extracting from /home/ton/Documents/a.rar

Extracting  prezentaciq.pyrva.kurs.korekciq.pptx                      Failed    
Extracting  prezentaciq.kolegium.25.11.09.pptx                        Failed    
Extracting  prezentaciq.original.za.korekciq.pptx                     Failed    
3 Failed
ton@ton-lpt:~/Documents$ ^C
ton@ton-lpt:~/Documents$ 

I have installed it from system tools -> Ubuntu software center

---

### Post by Portmanteaufu on 2010-05-10
Try installing unrar-nonfree.

```

sudo apt-get install unrar-nonfree

```

It may be more robust than the freebie version. Run it as:

```

unrar-nonfree e a.rar

```

---

### Post by spokoen on 2010-05-10
It happened! :)
thank u very much !!!
Just a few questions:
1. why in the right click menu i still see "open with unp" although i have removed it ?!
2. why when i press right click -> extract here it do nothing, and when i write in terminal it works ?!
3. that non-free version what it really means? do i have to pay, does it needs pass ?!
thank u again !

---

### Post by Portmanteaufu on 2010-05-10
> **spokoen said:**
> 
It happened! :) thank u very much !!!


Hurray! :D No problem.

> **spokoen said:**
> 
Just a few questions:
1. why in the right click menu i still see "open with unp" although i have removed it ?!
2. why when i press right click -> extract here it do nothing, and when i write in terminal it works ?!
3. that non-free version what it really means? do i have to pay, does it needs pass ?!
thank u again !


[LIST=1]
[*]I'm not sure. You might want to open a separate thread about this -- I tend to do most things on the command line, so I don't know much about the details of the Graphical User Interface (GUI).
[*]Did you try this once you had installed the non-free version? If you only tried it with the free version, that would explain it. The free version didn't work on the command line, so it didn't work in the GUI either.
[*] In the Linux world, when people say that a piece of software is "Free" they often mean that the person that wrote the software not only gives everyone the program, they also give everyone all of the code that they wrote to make the program. 

In this case, there's a "free" unrar that we all have the code for and there's the "non-free" unrar which we don't have the code for. Fortunately, even though we don't have the code for it, the author isn't charging us money to use it and pass it around.
[/LIST]

---

### Post by spokoen on 2010-05-10
Ok. thank u again from my hart! :) I will write again in the forum to get answers for the first 2 questions. Bye bye for the moment...i have to write my presentation!

---

