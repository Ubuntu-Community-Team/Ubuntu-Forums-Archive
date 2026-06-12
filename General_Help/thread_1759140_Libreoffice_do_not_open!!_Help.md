---
title: "Libreoffice do not open!! Help"
date: 2011-05-15
forum: General Help
---

### Post by masterserver on 2011-05-15
Hi guys, i am new to linux and  have a problem with libreoffice. I have Ubuntu 11.04 and i am trying to open libre office files but they do not open. For example i am trying to open an .xls file and when i double click it libre office start loadind nad then nothing!!! It does not open. The only way to open a file is to go to Applications->Office->LibreOffice   start a new document and then open the file from File->open...

Any idea?

Thanks

---

### Post by 73ckn797 on 2011-05-15
From Places/Documents have you right clicked over the file and told it what program to open with?

---

### Post by masterserver on 2011-05-15
Yes i've done that. when i double click the file the liblreoffice calc loads for 1 or 2 secs and then stops.

i will try to uninstall libre office and reinstall them.

---

### Post by slooksterpsv on 2011-05-15
Do you have Sun Java installed or openjdk? If you're not sure do this:

Dash -> gnome-terminal (search for it) - in the terminal type in:
gksudo update-java-alternatives -l

What's the results?

---

### Post by masterserver on 2011-05-16
I did what you said but he terminal shows nothing. when i pressed enter the system asked for my password, i entered my password, i pressed enter and nothing. It just started a new line for command.

---

### Post by slooksterpsv on 2011-05-16
Let's install Java then:

Go to Ubuntu Software Center -> Edit -> Software Sources -> Other Software -> and check Canonical Partners
Click on OK, and it should say it needs to refresh the package list (or do it automatically). Now search for sun-java6-plugin - download it and install it. Then try to open LibreOffice.

Terminal wise for installing it if you've enabled the Canonical Partners repositories:
sudo apt-get install sun-java6-plugin

---

### Post by masterserver on 2011-05-17
I tried everything you told me but nothing. 
I have i7 processor and i have installed ubuntu 11.04 32bit.
Should i install ubuntu 64bit????

---

### Post by slooksterpsv on 2011-05-17
> **masterserver said:**
> I tried everything you told me but nothing. 
I have i7 processor and i have installed ubuntu 11.04 32bit.
Should i install ubuntu 64bit????

How about open terminal, type in lowriter, and see what happens, the terminal should output errors, if there are any, to help us pinpoint what's going on.

---

### Post by debd on 2011-05-17
could you post the outputs of
```
 apt-cache unmet | grep libreoffice.org
```

---

### Post by debd on 2011-05-17
could you post the outputs of
```
 apt-cache unmet | grep libreoffice.org
```

---

### Post by masterserver on 2011-05-20
the outputs of "apt-cache | grep libreoffice.org"   is nothing!!!

Output:

nick@nick-desktop:~$ apt-cache | grep libreoffice.org
nick@nick-desktop:~$ 

I don't know what is going on.

---

### Post by masterserver on 2011-05-20
Slooksterpsv i typed lowriter in terminal and appeared the LbreOffice loading image and then disappeared. no errors in terminal.

---

### Post by linuxinstalledfromhdd on 2011-05-20
That doesn't add up.

Backup everything, reinstall Ubuntu 11.04 from a fresh disc. Download and make one. 

Than use a straight forward to-do list to install everything you want. Take your time with it too. One step at a time.

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by masterserver on 2011-05-20
I will do it. This time i will install 64bit edition.

---

### Post by debd on 2011-05-20
> **masterserver said:**
> the outputs of "apt-cache | grep libreoffice.org"   is nothing!!!

Output:

nick@nick-desktop:~$ apt-cache | grep libreoffice.org
nick@nick-desktop:~$ 

I don't know what is going on.

I told 
```
apt-cache unmet | grep libreoffice.org
```

just copy and paste.

---

### Post by masterserver on 2011-05-20
Sorry about that debd. I reinstalled Ubuntu 11.04 64bit and now libre offce works fine.

Thanks a lot to everyone for your help

---

