---
title: "I need help, i dont understand anything anymore!!!"
date: 2010-03-29
forum: General Help
---

### Post by TRUJohn on 2010-03-29
OK i buy this book from sitepoint, called build your own database driven website with php and mysql 4th edition, i have there step by step instruction on how to install everything in ubuntu yet  its not working i googled, and  i tried for the past week to fix the problem and all the guides i saw on the INTERNET ether i had no idea what they are talking about or they didin't work.

I feel like whatever i try to do nothing is working why is it so difficult to install something in Linux?  For the past week i been installing back and forward from Ubuntu, Debian, Fedora, Mandirva, Suse etc i am tiered why is it that nothing works ?  One thing works in one distribution and another thing dosen't.   Now i am very new at Linux, so i am asking the community to help me do the flowing.

1) install VMware in Ubuntu
2) Install LAMP (Mysql, apache and php) and configure it
3)  give me a couple of pointers on how to use the system properly

ohh please guys dont point me to an Internet guide because i want someone who can give me an messenger ID so we can do it through there.  Please HELP i am desperate and i dont want to go to Windows.  I made a decision and i want to stick with it.

Thanks for your time and sorry about the Bitching :)

---

### Post by nitstorm on 2010-03-29
Not sure about the others.. about you don't need VMware on ubuntu, you can use VirtualBox :)

---

### Post by Calash on 2010-03-29
For VMWare, are you installing it just to install LAMP or is it for a different application?

VMWare is an software that lets you create virtual computers and it seems a bit odd when paired with LAMP, so I just want to make sure we understand what you are looking to do.

If all you are looking for is to have a local web server/MySql/PHP setup you can get this done without VMWare.

---

### Post by techbrainless on 2010-03-29
Hi [TRUJohn]("http://ubuntuforums.org/member.php?u=940250") ,
I too new to linux and I am facing some problems sometimes .

summarize your problem which you are facing so that the others can help you. if you are stuck in a point just mention it .

thanking you

---

### Post by TRUJohn on 2010-03-29
First of all i would like to say thank you for the quick reply.

I want to use VMware to install windows so i can put adobe cs4 master edition. I need Photoshop, Ilustrator, Flash, etc.

And i want to learn how to program in PHP thats why i want to install LAMP.

---

### Post by TRUJohn on 2010-03-29
_for _[techbrainless]("http://ubuntuforums.org/member.php?u=970776")I

n the book it told me to install the binary pack for mysql first off, i got to the point where in the book it says to do this scripts/mysql_install_db --user=mysql, and i get this error

FATAL ERROR: Could not find mysqld

The following directories were searched:

    /usr/libexec
    /usr/sbin
    /usr/bin

If you compiled from source, you need to run 'make install' to
copy the software into the correct location ready for operation.

If you are using a binary release, you must either be at the top
level of the extracted archive, or pass the --basedir option
pointing to that location.

---

### Post by n0dix on 2010-03-29
> **TRUJohn said:**
> _for _[techbrainless]("http://ubuntuforums.org/member.php?u=970776")I

n the book it told me to install the binary pack for mysql first off, i got to the point where in the book it says to do this scripts/mysql_install_db --user=mysql, and i get this error

FATAL ERROR: Could not find mysqld

The following directories were searched:

    /usr/libexec
    /usr/sbin
    /usr/bin

If you compiled from source, you need to run 'make install' to
copy the software into the correct location ready for operation.

If you are using a binary release, you must either be at the top
level of the extracted archive, or pass the --basedir option
pointing to that location.

BUt there is a package in the repo to install lamp. I don't remember the name but is more easy to install than the source code.
Or you can follow this guide: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

---

### Post by TRUJohn on 2010-03-30
I don't know i cannot get it to work properly.

:( someone please help me

---

### Post by n0dix on 2010-03-30
Follow [this]("http://tuxtweaks.com/2009/10/install-lamp-on-ubuntu-9-10-karmic-koala/") guide.

---

### Post by Iowan on 2010-03-30
There are a few "perfect server" articles on [http://howtoforge.com]("http://howtoforge.com"). Sometimes, they seem to go a bit overboard, but generally, they can produce a working server. Good reading - even if only for ideas. the [server guide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") is another good starting point.

---

### Post by JUSTINBEAIRD on 2010-03-30
when I do php programing on windows i usually just use usb webserver [http://www.pendriveapps.com/usb-webserver/](http://www.pendriveapps.com/usb-webserver/)

but recently switched to xxamp-light on usb because i could not get pdo to work 
[http://www.apachefriends.org/en/xampp-windows.html](http://www.apachefriends.org/en/xampp-windows.html)

please note you should not use these as a live sever
I no this isn't what you asked but I just thought this was useful for the beginner

---

### Post by JUSTINBEAIRD on 2010-03-30
sorry for my last post i didnt fully read your post

---

