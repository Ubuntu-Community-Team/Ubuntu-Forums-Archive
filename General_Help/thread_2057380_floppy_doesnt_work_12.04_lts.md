---
title: "floppy doesnt work 12.04 lts"
date: 2012-09-13
forum: General Help
---

### Post by chevyiron420 on 2012-09-13
I have installed 12.04 on a new system I'm building, and the floppy won't work. The light doesn't come on when a disc is inserted, and if I go to "computer" and right click floppy and mount, it says no media in drive. If I use a formatter, it says the drive is not defined. I was given a fix for this with 10.04, but cant figure out how to use it here with 12.04. Please help me out.

---

### Post by redmk2 on 2012-09-13
> **chevyiron420 said:**
> I have installed 12.04 on a new system I'm building, and the floppy won't work. The light doesn't come on when a disc is inserted, and if I go to "computer" and right click floppy and mount, it says no media in drive. If I use a formatter, it says the drive is not defined. I was given a fix for this with 10.04, but cant figure out how to use it here with 12.04. Please help me out.

What changed between [**_[COLOR="Blue"]this post[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12186773&postcount=21") and now?

---

### Post by chevyiron420 on 2012-09-15
I would like to try to downgrade my udisks be this method but need some help.- 1. Allow yourself to use the floppy by going to 
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

- 2. Download 1.0.1-1build1  from here:
[https://launchpad.net/ubuntu/+source/udisks](https://launchpad.net/ubuntu/+source/udisks)
Select the 1.0.1-1build1 and download your processor version; example
for 32bit:

- 3. In Maveric: open a terminal cd (go) to the download (folder) &:
$ sudo dpkg -i udisks_1.0.1-1build1_i386.deb

- 4. reboot
The first problem is I cant find user privileges in 12.04. Is it there? Am I missing something?
The second problem is, when I go to download udisks there are three downloads there and I dont know which one to get, and I dont see anything about 32 bit or i386.
Next is exactly what do I type in terminal to to cd download, i cant get that to work.
Will someone walk me through this please.):P

---

### Post by oldfred on 2012-09-15
Have you just tried mounting from command line?

[http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
[http://ubuntuforums.org/showthread.php?p=11244050#post11244050](http://ubuntuforums.org/showthread.php?p=11244050#post11244050) post #2 coffeecat
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*

---

### Post by redmk2 on 2012-09-15
> **chevyiron420 said:**
> I would like to try to downgrade my udisks be this method but need some help.- 1. Allow yourself to use the floppy by going to 
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

- 2. Download 1.0.1-1build1  from here:
[https://launchpad.net/ubuntu/+source/udisks](https://launchpad.net/ubuntu/+source/udisks)
Select the 1.0.1-1build1 and download your processor version; example
for 32bit:

- 3. In Maveric: open a terminal cd (go) to the download (folder) &:
$ sudo dpkg -i udisks_1.0.1-1build1_i386.deb

- 4. reboot
The first problem is I cant find user privileges in 12.04. Is it there? Am I missing something?
The second problem is, when I go to download udisks there are three downloads there and I dont know which one to get, and I dont see anything about 32 bit or i386.
Next is exactly what do I type in terminal to to cd download, i cant get that to work.
Will someone walk me through this please.):P

I'm still using 10.04 so YMMV.  The option is to add the user to the *floppy group*.  You can manually add the user.  Check to see if the group exists ```
getent group|grep floppy
```

The link you have provided is for the source code.  You want to install the compiled binaries package.  Click on the link for the Ubuntu version you are using (i.e.Precise Pangolin) and then look for Binary Packages (to the right side of the page).

It's Downloads not download so from the terminal it would be ```
cd Downloads
```

---

### Post by chevyiron420 on 2012-09-15
Changing to the older udisks seemed to do the trick. Oddly though, some of my floppy's with airplane plans it will open with doc viewer and some it wont???

---

