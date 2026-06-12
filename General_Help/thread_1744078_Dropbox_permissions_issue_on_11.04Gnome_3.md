---
title: "Dropbox permissions issue on 11.04/Gnome 3"
date: 2011-04-30
forum: General Help
---

### Post by smarmytime on 2011-04-30
Hi - This is probably more of a Dropbox issue than an Ubuntu one, but I figured I'd ask here, as well as in the Dropbox forum. I just installed Ubuntu 11.04, and am trying out Gnome 3. All seems well, except Dropbox won't run - it keeps telling me that it's probably a permissions issue, or that it an error could be caused by my home folder being stored on a network share (it's not). I'ts giving me the following output in my tmp dir:

roger@karmalaptop:~$ cat /tmp/dropbox_error9uy0oq.txt
pid:	5437
ppid:	5435
uid:	1000
user_info:	('roger', 'x', 1000, 1000, 'Roger Sherman,,,', '/home/roger', '/bin/bash')
effective_user_info:	('roger', 'x', 1000, 1000, 'Roger Sherman,,,', '/home/roger', '/bin/bash')
euid:	1000
gid:	1000
egid:	1000
group_info:	('roger', 'x', 1000, [])
effective_group_info:	('roger', 'x', 1000, [])
appdata:	u'/home/roger/.dropbox'
mode=040700	uid=1000	gid=1000
parent	mode=040755	uid=1000	gid=1000
dropbox_path:	u'/home/roger/Dropbox'
mode=040700	uid=1000	gid=1000
parent	mode=040755	uid=1000	gid=1000
HOME:	/home/roger
tempdir:	'/tmp'
mode=041777	uid=0	gid=0
parent	mode=040755	uid=0	gid=0
Traceback (most recent call last):
File "__main__dropbox__.py", line 843, in main_startup
File "__main__dropbox__.py", line 499, in run
File "__main__dropbox__.py", line 336, in activate_translation
File "common_util/i18n.py", line 131, in activate_translation
File "common_util/i18n.py", line 172, in system_lang_code
AttributeError: 'NoneType' object has no attribute 'split'
roger@karmalaptop:~$

Dropbox has gotten to be a pretty integral part of my life - I need it to work. However, I'm enjoying the Gnome 3 experience so far, and while I'm not completely sold on it, I would like to keep trying it out. Can anybody offer any advice? FWIW, Dropbox did seem to work under Unity.

---

### Post by edher67 on 2011-05-02
i have the very same problem, here is my logerror, i'll try asking in gnome forums

> edher@edher-Satellite-A135:~$ cat /tmp/dropbox_errorXzbrBg.txt
pid:    28237
ppid:    28236
uid:    1000
user_info:    ('edher', 'x', 1000, 1000, 'edher,,,', '/home/edher', '/bin/bash')
effective_user_info:    ('edher', 'x', 1000, 1000, 'edher,,,', '/home/edher', '/bin/bash')
euid:    1000
gid:    1000
egid:    1000
group_info:    ('edher', 'x', 1000, [])
effective_group_info:    ('edher', 'x', 1000, [])
appdata:    u'/home/edher/.dropbox'
    mode=040700    uid=1000    gid=1000
parent    mode=040700    uid=1000    gid=1000
dropbox_path:    u'/home/edher/Dropbox'
    not found
parent    mode=040700    uid=1000    gid=1000
HOME:    /home/edher
tempdir:    '/tmp'
    mode=041777    uid=0    gid=0
parent    mode=040755    uid=0    gid=0
Traceback (most recent call last):
  File "__main__dropbox__.py", line 843, in main_startup
  File "__main__dropbox__.py", line 499, in run
  File "__main__dropbox__.py", line 336, in activate_translation
  File "common_util/i18n.py", line 131, in activate_translation
  File "common_util/i18n.py", line 172, in system_lang_code
AttributeError: 'NoneType' object has no attribute 'split'


---

### Post by edher67 on 2011-05-02
i've been searching around and I read GS does not use nautilus anymore, and dropbox app is nautilus build-in so... I hope am wrong cause really need dropbox

---

### Post by andrewthomas on 2011-05-02
I was having this problem and I solved it with:

[quote="andrewthomas"]I was having this problem and what I did was to get the latest version 

[http://dl-web.dropbox.com/u/17/dropbox-lnx.x86_64-1.2.0.tar.gz](http://dl-web.dropbox.com/u/17/dropbox-lnx.x86_64-1.2.0.tar.gz)
[http://dl-web.dropbox.com/u/17/dropbox-lnx.x86-1.2.0.tar.gz](http://dl-web.dropbox.com/u/17/dropbox-lnx.x86-1.2.0.tar.gz)

then extract the file, delete ~/.dropbox and ~/.dropbox-dist then move the extracted .dropbox-dist directory to ~/.dropbox-dist and 

```
start dropbox -i
``` in the terminal and it started right up.[/quote]

---

### Post by pseudoremora on 2011-05-03
Just want to say that the solution **andrewthomas** pointed out does in fact work. 

Also, to add some other instructions onto his post, after removing both the .dropbox  and .dropbox-dist folders from your home directory, you can run the command: **tar xvzf <**dropbox-lnx.xxxx-1.2.0.tar.gz> and that will automatically gunzip and extract the files to your home directory, creating the new .dropbox and .dropbox-dist folders. Then from their, you can execute the **dropbox start -i **command like **andrewthomas **mentioned, which should bring up the Login page for dropbox.

Hope that helps. Thanks **andrewthomas!**

---

### Post by andrewthomas on 2011-05-03
Glad to be of help.

---

### Post by edher67 on 2011-05-03
Thanks, that was the solution

---

### Post by hillbillyhotrod on 2011-05-03
I'm still confused, can we go step by step?

---

### Post by andrewthomas on 2011-05-03
> **hillbillyhotrod said:**
> I'm still confused, can we go step by step?
Download the file you need: 

**amd64**

[http://dl-web.dropbox.com/u/17/dropbox-lnx.x86_64-1.2.0.tar.gz](http://dl-web.dropbox.com/u/17/dropbox-lnx.x86_64-1.2.0.tar.gz)

**x86**

[http://dl-web.dropbox.com/u/17/dropbox-lnx.x86-1.2.0.tar.gz](http://dl-web.dropbox.com/u/17/dropbox-lnx.x86-1.2.0.tar.gz)

Open up the location that the file downloaded to (usually ~/Downloads)

Right-click on the file and select copy:

go to your /home directory and right-click and paste.

Now in nautilus, 
select under view > show hidden files 
then delete the .dropbox and .dropbox-dist directories.

Then, right-click on the downloaded dropbox-lnx.???.tar.gz file and select extract here.

open up a terminal and 

```
dropbox start -i
```

or you should be able to open up the .dropbox-dist directory and right-click on the dropbox executable file (the purple diamond) and choose to (run or execute)

and dropbox should then run.

---

### Post by skulls on 2011-05-19
Thanks for the solution. I did it a bit differently:

I deleted the .dropbox-dist folder, uninstalled the nautilus-dropbox package and then proceeded to download and install the DEB package from the dropbox site. 

it works now. Fingers crossed!

---

