---
title: "Using Tar to Extract Thunderbird (or any program) - how? - please help!"
date: 2010-07-11
forum: General Help
---

### Post by zozza on 2010-07-11
Hello,

Perhaps someone can explain how to use tar with Thunderbird properly.  I know I can use apt-get install but I want to learn how to use tar.

I went here and downloaded the .tar.bz2 file  -http://www.mozillamessaging.com/en-US/thunderbird/

The I found Thunderbird on my system using whereis - it was in /usr/lib/thunderbird.

So I used sudo tar jxvf /usr/lib/thunderbird - it would not let me do this.

So I copied the file to /usr/lib and installed it over the /thunderbird directory - but when I typed thunderbird it said it was not installed.

Obviously I have used tar wrongly.  In XP one clicks the .exe file and all the files go into the correct directories - for example, system32.

How do I use tar so that when I download a program all the files go into the correct directories and, if necessary, overwrite the older version?

Thanks.

---

### Post by bobnutfield on 2010-07-11
Type:

> man tar

in a terminal and it will give you all you need.  However, in the interim, the correct usage of decompression of a compressed archive is covered all over the net.  In it's basic explanation:

> tar jxvf XXXXXXXX.tar.bz2

Change into the directory with the same name as the program you are installing:

> cd XXXXXX.x.2

> ./configure

> make

> make install

This is very basic and there are a lot of options available to manipulate the install.  But normally you will download, move the archive to an appropriate directory, and extract and install there.

You should be aware that installing Thunderbird in this manner may make it difficult to uninstall if you want to.  It will not have the Ubuntu branding, either.  I would recommend practising with a less used program.

---

### Post by robsoles on 2010-07-11
I think you will be better off looking at results of the following google search.

[http://www.google.com/search?q=howto+compile+source+code+package+in+ubuntu](http://www.google.com/search?q=howto+compile+source+code+package+in+ubuntu)

---

