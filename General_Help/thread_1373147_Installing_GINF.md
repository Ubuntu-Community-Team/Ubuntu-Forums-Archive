---
title: "Installing GINF"
date: 2010-01-05
forum: General Help
---

### Post by L4U on 2010-01-05
I stumbled across this looks-to-be-abandoned WYSIWYG html editor called [GINF](http://ginf.sourceforge.net/) ("Ginf Is Not FrontPage"), but can't get it to install.  Not sure if the app is just too outdated, or I'm installing it wrong.  Can someone [download it](http://ginf.sourceforge.net/download/) and give it a try?

```
Compiling/Running GINF

Extract the files from the tar-ball (be default to: ginf/)
tar -zxf ginf-1.01-src.tar.gz [ENTER]
cd ginf/ [ENTER]

Now become root by typing:
su [ENTER]
Enter the root password, and execute the script:
./install-sh 1 [ENTER]

To run ginf, just type:
ginf [ENTER] 
```

---

### Post by bodhi.zazen on 2010-01-05
> **L4U said:**
> I stumbled across this looks-to-be-abandoned WYSIWYG html editor called [GINF]("http://ginf.sourceforge.net/") ("Ginf Is Not FrontPage"), but can't get it to install.  Not sure if the app is just too outdated, or I'm installing it wrong.  Can someone [download it]("http://ginf.sourceforge.net/download/") and give it a try?

```
Compiling/Running GINF

Extract the files from the tar-ball (be default to: ginf/)
tar -zxf ginf-1.01-src.tar.gz [ENTER]
cd ginf/ [ENTER]

Now become root by typing:
su [ENTER]
Enter the root password, and execute the script:
./install-sh 1 [ENTER]

To run ginf, just type:
ginf [ENTER] 
```

What problems are you having ?

That script seems to want to su to root, and that step will fail because the root account is locked.

become root with sudo -i and try running the install script again.

Did you install the dependencies ?

---

### Post by L4U on 2010-01-05
I'm getting "No such file or directory."  I swear I changed the dir to the correct one, but I'm a newbie, so maybe not!

When downloading an app file like GINF, is there a preferred folder to move it in?

---

### Post by bodhi.zazen on 2010-01-05
> **L4U said:**
> I'm getting "No such file or directory."  I swear I changed the dir to the correct one, but I'm a newbie, so maybe not!

When downloading an app file like GINF, is there a preferred folder to move it in?

No, but personally when I install from source I like to keep in in a directory I make ~/src

You then make ~/src/app-1
~/src/app-2
etc ...

---

### Post by L4U on 2010-01-05
Can you try to install GINF and see if it works for you?

---

### Post by Twitch6000 on 2010-01-05
right click on the install file and make sure you have checked the execitable option.

---

### Post by L4U on 2010-01-05
> **Twitch6000 said:**
> right click on the install file and make sure you have checked the execitable option.
I assume you mean the *install-sh* file.  I did, the execute was on, but just opened up the script in gedit.

---

### Post by L4U on 2010-01-05
> **L4U said:**
> Can [someone] try to install GINF and see if it works for you?
bump

---

### Post by L4U on 2010-01-06
Bueller?

---

### Post by bodhi.zazen on 2010-01-06
I downloaded the binary (not the source) to ~/Downloads

extracted the archive with tar xcvf ginf-1.01-i386.tar.gz

cd ginf

run the install script

sudo ./install.sh 1

There is an error message about a missing directory, remove ginf

sudo ./install.sh 2

make the directory

mkdir -p /usr/local/doc/ginf

re-run the installer

```
sudo ./install.sh 1
```

Installed fine, but it does does not run.

Installed gtkhtml3.8 (foir gtkhtml) , no joy.

It is an old program and that is as far as I am willing to go with it.

To be honest I suggest you look as bluefish . It is not WYSIWYG, although it is nice.

---

### Post by L4U on 2010-01-06
> **bodhi.zazen said:**
> It is an old program and that is as far as I am willing to go with it.
That's what I figured. :(  I appreciate your willingness to help.  Thanks!

---

