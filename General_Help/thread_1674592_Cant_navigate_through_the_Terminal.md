---
title: "Cant navigate through the Terminal"
date: 2011-01-24
forum: General Help
---

### Post by baqar on 2011-01-24
assasinz@assasinz-desktop:~$ cd downloads
bash: cd: downloads: No such file or directory
assasinz@assasinz-desktop:~$ cd music
bash: cd: music: No such file or directory
assasinz@assasinz-desktop:~$ 

Whats the matter i cant navigate through the terminal please help :(

[IMG]http://i54.tinypic.com/1129a3s.png[/IMG]

---

### Post by baqar on 2011-01-24
Hope reply may come early ...

---

### Post by djeikyb on 2011-01-24
Please be aware that linux is case-sensitive. Note there is no folder in your home directory called "downloads", but there is a folder called "Downloads".

Also, you got the syntax down at the end, but just to emphasize, type the command first, then a space, then the parameters. Ie:
```
cd ~/Downloads
```

Now, by Zeus's beard I'll never agree with Ubuntu's decision to capitalise the initial letter of its default directories. It sounds dumb, and it's really a small thing, but it does slow me down on the command line. Worse is that the bloody directories are required. Delete them, they pop right back. One could (and I have) create all small case symlinks, but it's inelegant.

---

### Post by or3x on 2011-01-24
You have to have a space between cd and the dir. For Example:
```

cd /
cd /home
cd ~/Downloads

```

---

### Post by Vaphell on 2011-01-24
djeikyb, there is an option to disable case sensitivity in terminal so you don't have to capitalize default directories

[http://serverfault.com/questions/217418/case-insensitive-bash-auto-complete](http://serverfault.com/questions/217418/case-insensitive-bash-auto-complete)

---

### Post by djeikyb on 2011-01-24
Sweet! I still harumph at having Documents instead of documents, but that's a nifty workaround. I like that it you can affect only tab-completion rather than renouncing case-sensitivity altogether.

---

### Post by baqar on 2011-01-24
Thanks u guys...
I am all new here. First time using Ubuntu :D
Thanks anyway. I appreciate it.;)

---

### Post by djeikyb on 2011-01-24
Don't forget to use the Thread Tools button at the top to mark your thread as solved : )

---

### Post by baqar on 2011-01-24
Ok. DOne thanks all :)

---

