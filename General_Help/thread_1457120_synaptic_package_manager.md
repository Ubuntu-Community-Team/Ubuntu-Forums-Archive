---
title: "synaptic package manager"
date: 2010-04-18
forum: General Help
---

### Post by luckyking8 on 2010-04-18
when ever i open my [COLOR=Red]synaptic package manager[/COLOR] [COLOR=Black]it shows an error




E: Type 'Executing:' is not known on line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.



help me plz
[/COLOR]

---

### Post by didkoslawow on 2010-04-18
Can you try to remove [COLOR=Black]**/etc/apt/sources.list.d/pidgin-ppa.list** ?
[/COLOR]

---

### Post by coffeecat on 2010-04-18
> **didkoslawow said:**
> Can you try to remove [COLOR=Black]**/etc/apt/sources.list.d/pidgin-ppa.list** ?
[/COLOR]

Perhaps the OP wants to keep the pidgin-ppa repository.

@luckyking8, there's a bad line in [COLOR=Black]/etc/apt/sources.list.d/pidgin-ppa.list. Please post the contents of that file and we can take it from there.

Also, how did you add the pidgin-ppa repository? Can you post a link?
[/COLOR]

---

### Post by ajgreeny on 2010-04-18
Or show us the output of ```
cat /etc/apt/sources.list.d/pidgin-ppa.list
```as it sounds as if there is an error in the file.

---

### Post by luckyking8 on 2010-04-20
E: Type 'Executing:' is not known on line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


how can i remove this

---

### Post by luckyking8 on 2010-04-20
E: Type 'Executing:' is not known on line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.






Plese help me ..... how can i close this:((

---

### Post by x1a4 on 2010-04-20
In Synaptic open the repository dialog (Settings > Repositories) and remove (or correct) the Pidgin entries.  You can also just delete the list file.  You may also want to post the contents of the file here and I'm sure someone will be able to offer a correction so you don't have to delete it (assuming you want to keep the Pidgin repo).

---

### Post by shaka_zulu on 2010-04-20
go to Synaptic and try to delete that repository or go to /etc/apt/source.list and delete line which makes problems.

---

### Post by luckyking8 on 2010-04-20
see the problem ho can i open setting and etc






Help me !!!!!

---

### Post by lisati on 2010-04-20
Threads merged

---

### Post by jaco223 on 2010-04-20
> **luckyking8 said:**
> see the problem ho can i open setting and etc






Help me !!!!!

Open a terminal and type

cd /
cd /etc/apt/sources.list.d
sudo rm (name of the ppa.list)

See if that helps.

Jaco

---

### Post by lisati on 2010-04-20
> **coffeecat said:**
> Perhaps the OP wants to keep the pidgin-ppa repository.

@luckyking8, there's a bad line in [COLOR=Black]/etc/apt/sources.list.d/pidgin-ppa.list. Please post the contents of that file and we can take it from there.

Also, how did you add the pidgin-ppa repository? Can you post a link?
[/COLOR]

@luckyking8: Please provide the information requested, otherwise how can we help you?

---

### Post by luckyking8 on 2010-04-20
Can some one help me or not.................................... :((:((:((

---

### Post by lisati on 2010-04-20
> **luckyking8 said:**
> Can some one help me or not.................................... :((:((:((

Not if you don't provide the information that you have been asked for.

---

### Post by x1a4 on 2010-04-20
More information is needed before specific help can be given.  Please start by clicking 'Close' on the error dialog when you start Synaptic, then click 'Settings' in the Synaptic menu, then 'Repositories' to open the repository dialog window and you will most likely be able to easily fix it yourself.  

Otherwise please post the contents of the file /etc/apt/sources.list.d/pidgin-ppa.list or a screenshot of the repositories dialog.  

Alternatively, delete the file /etc/apt/sources.list.d/pidgin-ppa.list.  You will lose your Pidgin repository though.

---

### Post by luckyking8 on 2010-04-20
lucky@lucky-desktop:/$ cd /etc/apt/sources.list.d
[email]lucky@lucky-desktop:/etc/apt/sources.list[/email].d$ sudi rm pidgin-ppa.list
No command 'sudi' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudi: command not found
[email]lucky@lucky-desktop:/etc/apt/sources.list[/email].d$ 






here it is tell me what i do now

---

### Post by jaco223 on 2010-04-20
Try to give the info lisati requested.

You may not have followed these instructions correctly

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

@lisati, ,this is where his/her problem may be.

Jaco

---

### Post by jaco223 on 2010-04-20
> **luckyking8 said:**
> lucky@lucky-desktop:/$ cd /etc/apt/sources.list.d
[EMAIL="lucky@lucky-desktop:/etc/apt/sources.list"]lucky@lucky-desktop:/etc/apt/sources.list[/EMAIL].d$ sudi rm pidgin-ppa.list
No command 'sudi' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudi: command not found
[EMAIL="lucky@lucky-desktop:/etc/apt/sources.list"]lucky@lucky-desktop:/etc/apt/sources.list[/EMAIL].d$ 






here it is tell me what i do now

You have a typo

try ```
 sudo rm pidgin-ppa.list
```

---

### Post by lisati on 2010-04-20
> **jaco223 said:**
> Try to give the info lisati requested.

You may not have followed these instructions correctly

[http://pidgin.im/download/ubuntu/](http://pidgin.im/download/ubuntu/)

@lisati, ,this is where his/her problem may be.

Jaco

:) I spotted the other thread(s)

---

### Post by luckyking8 on 2010-04-20
sudo apt-key adv --recv-keys --keyserver  keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
 echo deb  [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) \     `lsb_release --short --codename` main | \
    sudo tee /etc/apt/sources.list.d/pidgin-ppa.list








i put there commands on Terminal... after that this problem occurs......

---

### Post by luckyking8 on 2010-04-20
i m thinking to leave this oprating system,.......
no one nows abut the solution,,,,,,,,,,,
its better to stay away


bye

---

### Post by lisati on 2010-04-20
> **luckyking8 said:**
> i m thinking to leave this oprating system,.......
no one nows abut the solution,,,,,,,,,,,
its better to stay away


bye

/me tears hair out, because **people were trying to help.** See you later. Thread closed.

---

