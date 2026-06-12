---
title: "Help installing (tar.gz)"
date: 2010-03-02
forum: General Help
---

### Post by petedes5 on 2010-03-02
I'm really new to ubuntu and I want to install songbird. 

When I downloaded it, it came labeled as "Songbird_1.4.3-1438_linux-x86_64.tar.gz"

The file does not have a install guide on it and I am absolutely clueless in how to go about installing it. I googled and have tried some of the codes in terminal but always end up with an error

---

### Post by switch10 on 2010-03-02
you can find the .deb (download it, and it installs easily) here: [http://skyzim.com/songbird-1-2-0-installer/](http://skyzim.com/songbird-1-2-0-installer/) Its a slightly older version. Or to install that tar.gz file you have to untar it (like unziping) like this.

```
tar -zxvf Songbird_1.4.3-1438_linux-x86_64.tar.gz
```

then 

```
cd Songbird_1.4.3-1438_linux-x86_64.tar.gz
```

to change your working directory to Songbird_1.4.3-1438_linux-x86_64.tar.gz

you can usually find a readme in here somewhere that will explain how to install, but generally you just have to do:

```
./configure
make
make install
```

good luck

---

### Post by Nordite on 2010-03-02
What version of Ubuntu are you using.  If you are using 9.10 you can click on the little down arrow on the right of the file download and select "show in folder", then find your package right click and select "Archive Manager".  That should help you install it.
Nordite

---

### Post by petedes5 on 2010-03-02
Jaunty; 9.04

---

### Post by switch10 on 2010-03-02
> **petedes5 said:**
> I'm really new to ubuntu and I want to install songbird. 

When I downloaded it, it came labeled as "Songbird_1.4.3-1438_linux-x86_64.tar.gz"

The file does not have a install guide on it and I am absolutely clueless in how to go about installing it. I googled and have tried some of the codes in terminal but always end up with an error

put the .tar.gz in your home folder if it is not already there, or you have to change the directory to where the file .tar.gz file is. i.e. if it is on your desktop do this;
```
cd ~/Desktop 
```

the only other error you could get would be that you don't have permission to mess with the file.  If this happens, put a ```
sudo
``` before your commands.

---

### Post by petedes5 on 2010-03-02
so i enter the first code and:

peter@peter-laptop:~$ tar -zxvf Songbird_1.4.3-1438_linux-x86_64.tar.gz
tar: Songbird_1.4.3-1438_linux-x86_64.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
peter@peter-laptop:~$

---

### Post by switch10 on 2010-03-02
thats because the file does not exist in your home directory.  It is probably on your desktop or something.  Move it to your home directory and then run the command.

---

### Post by switch10 on 2010-03-02
If you look at my original post, I gave you a URL where you can just download songbird and it installs automatically, similar to an EXE file in Windows.

---

### Post by petedes5 on 2010-03-02
I moved it into my home directory ?? at least i think, I went to computer>file system>home>peter

am I missing something?

---

### Post by petedes5 on 2010-03-02
so i re-extracted it and got pass the first code=success 

but then i try the second code and

peter@peter-laptop:~$ cd Songbird_1.4.3-1438_linux-x86_64.tar.gz
bash: cd: Songbird_1.4.3-1438_linux-x86_64.tar.gz: Not a directory
peter@peter-laptop:~$

---

### Post by wojox on 2010-03-02
Try:

```
cd Songbird
``` 

And hit the tab button.

---

### Post by switch10 on 2010-03-02
type in:
```
 cd Songbi
```
hit the TAB button while typing, and it will fill the rest in for you.  You probably have to drop the .tar.gz

---

### Post by petedes5 on 2010-03-02
all it did was put a forward slash.

I apologize for being so dumb with this

---

### Post by ErichK on 2010-03-02
Actually, I made the installer for the newest version of Songbird, available here: [http://skyzim.com/songbird-1-4-3-installer/](http://skyzim.com/songbird-1-4-3-installer/)

---

### Post by switch10 on 2010-03-02
download this!! ^^^^^^^^^  it is much easier...

---

### Post by petedes5 on 2010-03-02
> **ErichK said:**
> Actually, I made the installer for the newest version of Songbird, available here: [http://skyzim.com/songbird-1-4-3-installer/](http://skyzim.com/songbird-1-4-3-installer/)


super easy! thanks, it's people like you that keep people like me on ubuntu

---

