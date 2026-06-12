---
title: "trouble with installing on the terminal"
date: 2011-01-31
forum: General Help
---

### Post by becca2010 on 2011-01-31
im running ubuntu 10.10 with a 64 bit,i have a canon pixma mx340 mutifuntion print scan and fax,i found the drivers i need to make it work after researching forums,i had the printer working after finding the instructions on another help forum by going through the terminal, here is the web site that the downloads are on [http://support-my.canon-asia.com/P/search?model=PIXMA+MX347&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-my.canon-asia.com/P/search?model=PIXMA+MX347&menu=download&filter=0&tagname=g_os&g_os=Linux) ,please help :confused:

---

### Post by matt_symes on 2011-01-31
Hi

You might have problems with those drivers. I'm not sure though.

> System requirements
Ubuntu 9.10(32bit)

Do you have a link to the thread you found ?

Kind regards

---

### Post by khamil8686 on 2011-01-31
to install 32bit programs on 64bit architecture you want to make sure you have the ia32-libs package installed, ive had no problems running 64bit vs running a 32bit system as long as ive had that package installed :) its the libraries for 32bit programs to run on 64bit
to install just download the "MX340 series IJ Printer Driver Ver. 3.30 for Linux (debian ..." tarball file and extract it to a directory and run the install.sh script it provides
```
/path/to/extracted/files/install.sh
```

may have to use sudo before the above code but im not sure

also if you have trouble with running the above install.sh script they did include .deb packages within the tarball you could run in the /path/to/extracted/files/packages/ directory called cnijfilter-common-3.30-1_i386.deb and cnijfilter-mx340series-3.30-1_i386.deb which you can just double click to install

---

### Post by becca2010 on 2011-01-31
> **matt_symes said:**
> Hi

You might have problems with those drivers. I'm not sure though.



Do you have a link to the thread you found ?

Kind regards
[http://ubuntuforums.org/showthread.php?t=1543191&highlight=canon+pixma+mx340](http://ubuntuforums.org/showthread.php?t=1543191&highlight=canon+pixma+mx340) ,this worked for the printer but not scanner but there is a link for scan gear mp i just don't know how to do it like the printer link

---

### Post by becca2010 on 2011-01-31
> **khamil8686 said:**
> to install 32bit programs on 64bit architecture you want to make sure you have the ia32-libs package installed, ive had no problems running 64bit vs running a 32bit system as long as ive had that package installed :) its the libraries for 32bit programs to run on 64bit
to install just download the "MX340 series IJ Printer Driver Ver. 3.30 for Linux (debian ..." tarball file and extract it to a directory and run the install.sh script it provides
```
/path/to/extracted/files/install.sh
```may have to use sudo before the above code but im not sure

also if you have trouble with running the above install.sh script they did include .deb packages within the tarball you could run in the /path/to/extracted/files/packages/ directory called cnijfilter-common-3.30-1_i386.deb and cnijfilter-mx340series-3.30-1_i386.deb which you can just double click to install
yes i tryed all of that already it tells me error,the terminal is the only way so far as to get it to work,please refer to the link to the help forum i provided for the other person

---

### Post by becca2010 on 2011-01-31
alrite i've gotten the link in to the sudo (terminal) but its not letting me put my passwrd,and yes i tryed cap lock

---

### Post by matt_symes on 2011-01-31
Hi

If you enter your password in the terminal you will not see it echoed to the screen. This is normal and for security. Just type it in (it's case sensitive) and hit enter.

Kind regards

---

### Post by becca2010 on 2011-01-31
yeah did that and it told me incorrect and asked for it again

---

### Post by matt_symes on 2011-01-31
Hi

Press ALT and F2 together and enter

```
gksudo gnome-terminal
```

Enter your password as you would when installing software or performing other admin tasks through X. 

This will put you in a root shell so be very careful here indeed.

You should then be able to install the software without using sudo.

```
/path/to/install.sh
```

(or something similar).

Close the terminal as soon as possible. Does it accept your password now ?

Kind regards

---

### Post by becca2010 on 2011-01-31
ok now how do i install using that window,when i click on the install icon after extracting file it ask if i want to run in terminal(wont let me enter password) display(dont know how to use) cancel ,and run (that dose nothing)

---

### Post by khamil8686 on 2011-02-01
how do you install using which window? the window that comes up after pressing alt+f2 and typing the following and pressing enter  is called a terminal window, is this window what you are referring to?
```
gksudo gnome-terminal
```
to install this you would want to enter the command
```
/home/*your user name here*/Desktop/*extracted file folder name*/install.sh
```
this will run the included install.sh script you downloaded to the desktop as root so you have access to install files and whatever else the install script may call for, just follow whatever prompts it may give you and once its done try using your device

---

