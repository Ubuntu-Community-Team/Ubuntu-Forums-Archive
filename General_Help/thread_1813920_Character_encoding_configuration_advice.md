---
title: "Character encoding configuration advice"
date: 2011-07-28
forum: General Help
---

### Post by Andrew Utnubu on 2011-07-28
Here is a strange problem I have encountered.

I have two ISO files generated from cds. Each one of them has a file called "support.txt", but "support" written in Russian language.

When I'm trying to "mount -o loop" it, I can't copy this file from one of the images because it's name becoming "????????????.txt".

The strange thing is that when I'm doing "ls /media/$mounted_cd_folder$" for each mounted image, this support file name appears correctly in cd1.iso mounted folder and appears incorrectly in cd2.iso mounted folder. But when I'm trying to open these files with ArchiveManager in GUI, the support file name appears correctly in cd2.iso and incorrectly in cd1.iso. O_o

The contents of both files appears incorrectly if Windows cp1251 character encoding not chosen in OpenOffice.


Also, it seems like I need to configure my systems properly, because on another Ubuntu system things going vice-versa.

Could somebody please help me with proper encoding\locales configuration?

---

### Post by Andrew Utnubu on 2011-08-02
No ideas at all? =(

---

### Post by tredegar on 2011-08-02
I *hate* this locale, character-encoding and language stuff, but here is my 2¢ (or is it &#8364;0.02 ?) because nobody else seems to be interested ....

Linux pretty much uses UTF-8 now, and this solves a lot of horrible encoding problems.

But your messy filenames have not been encoded with UTF-8 it seems. The **convmv** utility will help you with this, it's in the ubuntu repositories. Its **man** page is pretty impenetrable, but at least you have something to start your searches with.

Good luck!

Edit: I forgot [this link]("http://www.cl.cam.ac.uk/~mgk25/unicode.html") for UTF-8

---

### Post by Andrew Utnubu on 2011-08-02
Thank you very much, tredegar!

I used to surf the web for this problem and red about the convmv utility. I thought that maybe I could change some settings in OS itself, so I won't have to recreate all these ISO files again, because actually there's more than a few of them and I will have to check them all or create some kind of script to automate the process.

Anyway, if I won't find any better solution I will have to convert all these bad files.

P.s.: Thanks for the link, I'll check it.

---

### Post by tredegar on 2011-08-02
OK. 

There's nothing in linux you can change to fix your problem, it's the filenames that are at fault.

If you search on **convmv** you'll find scripts and suggestions for mass-conversions. Like [this one]("http://www.linux.com/archive/feed/58689") which also shows how to test your command _before_ you try it for real.

---

### Post by Andrew Utnubu on 2011-08-02
Thank you very much, tredegar. I'll keep digging.

---

### Post by Andrew Utnubu on 2011-08-17
The problem partially solved. After I did this:

```
vi /var/lib/locales/supported.d/local
//add "ru_RU.CP1251 CP1251"
//save & exit
dpkg-reconfigure locales
reboot

```

both images mounted with correct file names. File names appears correct in terminal window and in my little test java application when I'm listing folder.

But the thing I left behind this post, that I have a java application inside GlassFish web server, that does the same things I'm doing in my test application, but it fails.

I think it's time to search for some GlassFish character encoding problems.

Thank you guys!

---

### Post by tredegar on 2011-08-17
Thanks for the follow-up.

You have a workaround in that you have added support for windows CP1251 but the fact remains that your problem filenames are not encoded as UTF-8, as they should be.

It will be easier to fix the root cause than to make workarounds for all your different systems.

The command you need is 
```
convmv -f cp1251 -t utf8 -r /path/to/files/*
```
That will just _show you_ what it is going to do. Check the output to make sure it is what you want. (If this data is **really important**, you should do this filename conversion on a copy of your data.)

The following command will _do it_
```
convmv -f cp1251 -t utf8 -r --notest /path/to/files/*
```

Good luck.

---

### Post by Andrew Utnubu on 2011-08-19
I suppose that this output gives another thought that the problem is somewhere in GlassFish.. )

```

root@1:~# convmv -f cp1251 -t utf8 -r /usr/dist/360_1/
Your Perl version has fleas #37757 #49830
Starting a dry run without changes...
Skipping, already UTF-8: /usr/dist/360_1/&#1058;&#1077;&#1093;&#1087;&#1086;&#1076;&#1076;&#1077;&#1088;&#1078;&#1082;&#1072;.txt
No changes to your files done. Use --notest to finally rename the files.

```

---

