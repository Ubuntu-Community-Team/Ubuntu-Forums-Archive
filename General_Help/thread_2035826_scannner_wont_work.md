---
title: "scannner wont work"
date: 2012-07-31
forum: General Help
---

### Post by tobythedog on 2012-07-31
hi just connected a trust easy webscan 19200 to my laptop ,the lubuntu scan program detects it ok as its in the description of which scanner to use, when i try scanning however it wont work saying unable to connect to scanner, anyone any ideas as to what i need to do to get it to work please.

---

### Post by tobythedog on 2012-07-31
tried the xane scanner but get error  says failed to open device artec-eplus 48u:libusb:002:002`: invalid argument.
affraid i dont have a clue what this all means , anyone any idea how i can get the scanner working please.

---

### Post by Scott Goodgame on 2012-07-31
Might want to look here... looks promising...
[https://help.ubuntu.com/community/ArtecEplus48uConf](https://help.ubuntu.com/community/ArtecEplus48uConf)

---

### Post by tobythedog on 2012-08-01
the link is interesting but i dont  think its much help as lubuntu doesnt use natilus,
does anyone know what i need to do in lubuntu to use the info in the  link given , as it is for nautilus and lubuntu doesnt use it i dont know what to do

---

### Post by audiomick on 2012-08-01
Nautilus is the file manager on a standard Ubuntu. On Lubuntu, I believe it is PCManFM

[https://en.wikipedia.org/wiki/PCMan_File_Manager]("https://en.wikipedia.org/wiki/PCMan_File_Manager")

The advise in the link to do
```
gksudo nautlius
```

means "start your file manager with root privileges. The reason for this is that the author then goes on to suggest to

> navigate to....etc/sane.d. 

Download/paste Artec48.usb in here. 

So you apparently need to add something to a file in the /etc folder. This folder belongs to root, so you can't edit anything in there as a normal user.

I think that
```
gksudo pcmanfm
```
will get you an instance on lubuntu of the file manager with root privileges, but I am not certain. I don't have an install of lubuntu to check. You will have to try it for yourself.

Point is, it is all about adding something to the folder etc/sane.d. , and you need root privileges to do this.

---

### Post by sgoodman on 2012-08-01
you can try with gimp and the quitesane scanner plugin for gimp

---

### Post by Sef on 2012-08-01
Check out the [SANE]("http://www.sane-project.org/sane-mfgs.html#Z-TRUST") project. It says it works good.

---

### Post by Scott Goodgame on 2012-08-02
You can do the same thing, but with PCMANFM or from the command line, you nust need to edit and save files in the right locations

---

### Post by tobythedog on 2012-08-11
i dont know enough yet to know what i need to do , i need step by step instructions on what i need to do please.

---

