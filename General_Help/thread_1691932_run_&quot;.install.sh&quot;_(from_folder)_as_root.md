---
title: "run &quot;./install.sh&quot; (from folder) as root????"
date: 2011-02-20
forum: General Help
---

### Post by wanitto on 2011-02-20
I am trying to install the divx codec, and this is what the readme says: run "./install.sh" as root.

I am an absolute beginner. please help.

---

### Post by Foxheadz on 2011-02-20
run ```
sudo ./install.sh
```
it will then ask you for a password. if your the only user on your computer then it will probably be your password. The sudo command is put in front of any command to run it as root.

---

### Post by wanitto on 2011-02-20
when i do that it says : ```
sudo: ./install.sh: command not found
```

---

### Post by Purplerob on 2011-02-20
try
 ```
sudo sh install.sh
```

---

### Post by Foxheadz on 2011-02-20
not sudo: just sudo ./install.sh

---

### Post by wanitto on 2011-02-20
for sudo sh install it says :  sh: Can't open install.sh

and this doesn't make sense, how do i direct it to the folder?

---

### Post by Foxheadz on 2011-02-20
cd to the directory of install.sh ```
cd path/to/directory
```

---

### Post by wanitto on 2011-02-20
hmm, i'm sorry, i'm still not getting anything.

---

### Post by Foxheadz on 2011-02-20
let's say the file install.sh is in the downloads folder of your home directory then first run ```
cd ~/Downloads
``` then run ```
sudo sh ./install(.sh)
```

---

### Post by jocko on 2011-02-20
> **wanitto said:**
> I am trying to install the divx codec, and this is what the readme says: run "./install.sh" as root.

I am an absolute beginner. please help.
As you are an absolute beginner, I guess that you are trying to do things a lot more complicated than they really are.
To get the divx codec (and a lot of other codecs that are not installed by default), just install the package "libavcodec-extra-52".

Open up synaptic (System-->Administration-->synaptic package manager) and search for it. Or install it from the terminal with this simple command:
```
sudo apt-get install libavcodec-extra-52
```There are a bunch of packages (codecs, adobe flash, support for .rar archives, java plugin for firefox *etc*.) that most people want but that are not installed by default due to their licences, which can be installed by installing the package "ubuntu-restricted-extras".

---

### Post by wanitto on 2011-02-20
i think it worked! thanks

what's happening now is that I wrote "yes" in the terminal and it froze, endlessly writing "y" over and over.

---

### Post by sunveer on 2012-02-17
After that I got options to install.  But when I select by typing 1 in the terminal I got "Compiler is not available to compile modules, aborting..."

---

### Post by felixdecena on 2013-03-23
Also make sure that install.sh script is stored in your disk.  If it is not, you may be getting error "command not found"

---

