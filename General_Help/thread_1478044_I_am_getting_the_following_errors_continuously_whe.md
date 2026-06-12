---
title: "I am getting the following errors continuously whenever I update/save a config file."
date: 2010-05-09
forum: General Help
---

### Post by angheloko on 2010-05-09
I am getting the following errors continuously whenever I update/save a config file in /etc/

```
error: line 29136: bad flag vector alias
error: line 29137: bad flag alias index: 0
```The config file got updated though. I am just worried that this may be something bad.

I update the files using the command sudo gedit <config_file>. 

I haven't encountered this before in Karmic. Has anyone encountered the same error messages?

Thanks!

Additional Info:

This might be a problem with gedit. I tried doing the following and the error messages also came up:

1. In terminal, gedit foo.txt
2. In gedit, type anything and save
3. Terminal will show the following:

```

...
...
error: line 19234: bad flag vector alias
error: line 19243: bad flag alias index: 0
...
...

```

**May 10, 2010**

Running artha from the terminal also causes the error.

I've managed to get the top-most line of the error:

error: line 15: bad flag alias index: 0
error: line 15: bad flag vector alias

The hardest thing about this is I have no idea what's causing it. I thought it was gedit but running artha (from the terminal) also causes the error.

Sigh. This is a clean install of Lucid, which again makes it even harder to know what causes it.

I have tried checking the logs from the Log File Viewer but nothing there says anything helpful (from what I can understand).

---

### Post by philinux on 2010-05-09
Post moved to new thread. The sticky is not for support.

---

### Post by angheloko on 2010-05-10
Now I'm sure I'm not the only one experiencing this. Got my co-worker to try it out and got the same errors.

Here's how to replicate:

1. In a terminal, type gedit foo.txt
2. In gedit, type anything and save
3. The error message should show up in the terminal

We're both using Lucid Lynx; Kernel - 2.6.32-22-generic; gedit - Version 2.30.2.

From what I could search (which is very limited since googling shows my posts), I think hunspell may be the one causing the issue.

Thanks!

---

### Post by dimpletz on 2010-05-10
Remix has no problem, only the desktop edition of Ubuntu Lucid.

---

### Post by rw3bb on 2010-05-10
See attachment if somebody wants to analyze this.

---

### Post by jpmeijers on 2010-05-14
I definitely got this error in every Ubuntu 10.04 I saw so far. The delay caused by the terminal output is also very frustrating. See Launchpad Bug #578917.

---

### Post by angheloko on 2010-05-14
> **jpmeijers said:**
> I definitely got this error in every Ubuntu 10.04 I saw so far. The delay caused by the terminal output is also very frustrating. See Launchpad Bug #578917.

Hi jp, the strange thing is that it's not only gedit that causes the bug (as seen from the bug # you've provided. I also tried running artha (a thesaurus) from the terminal and it also produced the errors). I don't think there is any fix yet.

My only worry is that if there are any other programs that may produce the error and ending up filling some logfiles, unknown to the user. :confused:

---

### Post by fsando on 2010-05-18
Hi
I believe it has to do with a bug in one of the myspell dictionaries (in some way), I ran this command (I was fiddling with a theme a the time):
Note: strace traces the command and spews out tons of info on what goes on during executions -o "filename" collects all the info into a file.

```
strace -o "strace-gedit-bad-flag.txt" gedit index.theme
```


This is the interesting part:
```

...
open("/usr/share/myspell/dicts/en_ZA.dic", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=595723, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb781f000
read(21, "53476\n!boerbul\n!likable\n!poes\nA\n"..., 4096) = 4096
mmap2(NULL, 221184, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb55c9000
write(2, "error: line 15: bad flag alias i"..., 40) = 40
write(2, "error: line 15: bad flag vector "..., 38) = 38
write(2, "error: line 16: bad flag alias i"..., 40) = 40
write(2, "error: line 16: bad flag vector "..., 38) = 38
write(2, "error: line 18: bad flag alias i"..., 40) = 40
write(2, "error: line 18: bad flag vector "..., 38) = 38
write(2, "error: line 19: bad flag alias i"..., 40) = 40
...
(several million lines)

```
It appears to be myspell en_ZA that causes the problem, I removed anything myspell related to en_ZA. This solved it.

---

### Post by angheloko on 2010-05-19
> **fsando said:**
> Hi
I believe it has to do with a bug in one of the myspell dictionaries (in some way), I ran this command (I was fiddling with a theme a the time):
Note: strace traces the command and spews out tons of info on what goes on during executions -o "filename" collects all the info into a file.

```
strace -o "strace-gedit-bad-flag.txt" gedit index.theme
```
This is the interesting part:
```

...
open("/usr/share/myspell/dicts/en_ZA.dic", O_RDONLY) = 21
fstat64(21, {st_mode=S_IFREG|0644, st_size=595723, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb781f000
read(21, "53476\n!boerbul\n!likable\n!poes\nA\n"..., 4096) = 4096
mmap2(NULL, 221184, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb55c9000
write(2, "error: line 15: bad flag alias i"..., 40) = 40
write(2, "error: line 15: bad flag vector "..., 38) = 38
write(2, "error: line 16: bad flag alias i"..., 40) = 40
write(2, "error: line 16: bad flag vector "..., 38) = 38
write(2, "error: line 18: bad flag alias i"..., 40) = 40
write(2, "error: line 18: bad flag vector "..., 38) = 38
write(2, "error: line 19: bad flag alias i"..., 40) = 40
...
(several million lines)

```It appears to be myspell en_ZA that causes the problem, I removed anything myspell related to en_ZA. This solved it.


Hi fsando,

It seems that the locales or myspell are indeed causing the problem. I removed all other locales except for EN using localepurge. And it also solved this issue.

Thanks!

---

### Post by anantshri on 2010-05-28
final error i get is this 

(gedit:12595): Gtk-WARNING **: Attempting to store changes into `/home/anant/.recently-used.xbel', but failed: Failed to rename file '/home/anant/.recently-used.xbel.WDSVCV' to '/home/anant/.recently-used.xbel': g_rename() failed: Is a directory

hope this could help some one find the root of problem.

i tried localepurge but this didn't helped.


EDIT : seems like myspell indeed was the culprit.removed it and now error seems to be gone.

---

### Post by gamesbook on 2010-06-07
> **angheloko said:**
> Hi fsando,

It seems that the locales or myspell are indeed causing the problem. I removed all other locales except for EN using localepurge. And it also solved this issue.

Thanks!

Is there a fix or patch for this that does **not **involve removing the local versions of myspell (speaking as en_ZA Ubuntu user)?

---

### Post by dvanrensburg on 2010-06-08
It seems to be the en_ZA language support of the spell checker plugin that does not work properly. 

It works if you change the language from 'English South Africa'  to 'English United Kingdom' but that only lasts for the life of the  terminal session. 

I do not know how to change the language settings for gnome as a whole. I tried System->Administration->Language Support but I cannot  select a language to apply. It stays unselected no matter which language  I click on. 
 
However, I managed to 'fix' it permanently by removing the spell checker plugin for gedit.

In 'edit->preferences->plugins ' find the spell checker plugin and disable it.

---

### Post by gamesbook on 2010-06-08
> **dvanrensburg said:**
> It seems to be the en_ZA language support of the spell checker plugin that does not work properly. 

It works if you change the language from 'English South Africa'  to 'English United Kingdom' but that only lasts for the life of the  terminal session. 

I do not know how to change the language settings for gnome as a whole. I tried System->Administration->Language Support but I cannot  select a language to apply. It stays unselected no matter which language  I click on. 
 
However, I managed to 'fix' it permanently by removing the spell checker plugin for gedit.

In 'edit->preferences->plugins ' find the spell checker plugin and disable it.

Thanks - but it would be good to get a real fix - I assume that would require a patch of sorts for the plugin.  MS should see to this - or he has he abandoned his roots entirely?!  ;)

---

### Post by linekill on 2010-06-08
@dvanrensburg: Thanks for this workaround. I was having trouble with getting my 3G Modem to work, while following this steps provided [here]("http://blog.lynxworks.eu/20090830/huawei-e1550-on-ubuntu"), I encountered this issue with gedit. Google brought me to this page, and it's working now. 

Thanks again,

---

### Post by 4hp007 on 2010-06-26
Removed my spell completely from synaptic package manager and now everything works well. :KS:KS:KS:KS:KS

---

