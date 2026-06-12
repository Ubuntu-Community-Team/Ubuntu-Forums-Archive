---
title: "install phun?"
date: 2009-12-13
forum: General Help
---

### Post by bwhitney1256 on 2009-12-13
new to ubuntu so go easy on me. I downloaded a program called phun. used this program on XP a couple years ago but how the heck to i get it to install on this OS?

---

### Post by tcchris on 2009-12-13
Looks like you download the tar file 
 extract it to a folder 
 and run "sh phun" from that directory in terminal
or make a link to phun on the desktop

---

### Post by bwhitney1256 on 2009-12-13
i know im a newb, but how do i open a terminal in that directory. tried running from terminal window and i get this.
blair@blair-desktop:~$ sh phun
sh: Can't open phun

---

### Post by t0p on 2009-12-13
> **bwhitney1256 said:**
> new to ubuntu so go easy on me. I downloaded a program called phun. used this program on XP a couple years ago but how the heck to i get it to install on this OS?

Is there any particular reason why you think it will work in Ubuntu?  If it's a Windows program, it will work in Windows.  You need a Linux version if you want it to work in Linux.

---

### Post by bwhitney1256 on 2009-12-13
did a search for a linux version and found one, just still new to linux

---

### Post by t0p on 2009-12-13
Okay, go to the directory where you downloaded the file and paste a file listing here.

If you downloaded the file to your Desktop, the following command will print out the file listing we need:

```
ls Desktop
```

---

### Post by bwhitney1256 on 2009-12-13
/home/blair/Downloads

---

### Post by t0p on 2009-12-13
> **bwhitney1256 said:**
> /home/blair/Downloads

Okay, tell me what you have in that directory.  You can get a list of its contents by typing the following into a terminal:

```
ls ~/Downloads
```

If you don't know: you open a terminal by going to **Applications > Accessories > Terminal**

---

### Post by bwhitney1256 on 2009-12-13
blair@blair-desktop:~$ ls ~/Downloads
Phun_beta_5_28_linux32.tgz



[COLOR=Blue]tks for trying to help me with this:D[/COLOR]

---

### Post by t0p on 2009-12-13
Use the file manager ('Places') to navigate to your Downloads directory.  Now right-click on Phun_beta_5_28_linux32.tgz and select 'Extract here...'.

A folder called Phun_beta_5_28_linux32 or something similar should have been created.  Go in there and tell us what files are in there.

---

### Post by bwhitney1256 on 2009-12-13
/home/blair/Downloads/Phun/data
/home/blair/Downloads/Phun/lib
/home/blair/Downloads/Phun/materials
/home/blair/Downloads/Phun/scenes
/home/blair/Downloads/Phun/screenshots
/home/blair/Downloads/Phun/textures
/home/blair/Downloads/Phun/autoexec.cfg
/home/blair/Downloads/Phun/config.cfg
/home/blair/Downloads/Phun/Credits.txt
/home/blair/Downloads/Phun/LICENSE.txt
/home/blair/Downloads/Phun/phun
/home/blair/Downloads/Phun/phun.bin
/home/blair/Downloads/Phun/README.txt
/home/blair/Downloads/Phun/startbrowser.sh
/home/blair/Downloads/Phun/thyme.cfg

---

### Post by t0p on 2009-12-13
I suggest reading that Readme file.  If you don't understand it, post its contents here.

---

### Post by scouser73 on 2009-12-13
There is a software program called Phun that is in GetDeb, the file can be found [[COLOR="Red"]**Here**[/COLOR]]("http://old.getdeb.net/search.php?keywords=phun")

To install the file, click where it says **Download: Phun**
A dialogue box will open up, select **Open With GDebi Package Installer**
Click **OK**

The software will now start to be installed.

---

