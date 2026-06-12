---
title: "applying a patch"
date: 2006-06-29
forum: General Help
---

### Post by lex1 on 2006-06-29
I am about to install inn2 (NNTP server know as internet net news) there is a patch.

which looks like this:

--- /usr/lib/news/innshellvars.pl	2006-03-15 11:37:21.000000000 +0100
+++ ./innshellvars.pl	2006-06-15 10:04:28.000000000 +0200
@@ -9,7 +9,11 @@
 
 package inn ;
 
-eval `/usr/lib/news/bin/innconfval -p`;
+my $icv = `/usr/lib/news/bin/innconfval -p`;
+my %icv;
+$icv{$icv}++;
+($icv) = keys %icv;
+eval $icv;
 
 $newshome = $pathnews;
 $newslib = "/usr/lib/news";


I have not installed inn2 yet how do I apply the patch, ?and how do i know if its not already been allpied to latest release of inn2? Latest package is 15-03-2006.


lex1

---

### Post by Rui Pais on 2006-06-29
hi, try
```
cd /path/of/app/to/patch/
```
```
patch -p1 </path/to/the/patch
```

---

### Post by lex1 on 2006-06-29
Can you give an example of what you have said, ok i am a bit braindead, it would help.

thanks

lex1

---

### Post by Rui Pais on 2006-06-29
Hi, i don't know inn2, i'll assume that you want to apply that to source code package already downloaded and then compile.

Go to the folder you have the source package and uncompressed if you haven't made it yet. 
Let's say that you end with source code in ~/inn2 and have the patch in your home folder and its named inn2.patch.

cd ~/inn2
patch -p1<~/inn2.patch

then usual:
./configure 
make
sudo make install

why not install simply with apt? 
is that patch supposed to solve some bug?

---

### Post by lex1 on 2006-06-29
Thanks for explaination.

yes it will done with

apatitude install inn2

and yes it is a bug the patch is the fix.


lex1

---

### Post by Rui Pais on 2006-06-29
Uhmm... applying the patch to something installed with apt or aptitude is a little more ticky.

But the patch looks very simple. 
Try install first and then apply the patch on the /usr/lib/news/ folder.

---

### Post by lex1 on 2006-06-29
see pm please . uum you do not have a pm tag or email cannot also?

cannot find file to apply patch?

following this howto [http://news.aioe.org/article.php3?id_article=18](http://news.aioe.org/article.php3?id_article=18)

bug here
[https://launchpad.net/distros/ubuntu/+source/inn2/+bug/49947](https://launchpad.net/distros/ubuntu/+source/inn2/+bug/49947)

---

### Post by Rui Pais on 2006-06-29
Well, thats the problem with patchs to installed software. Ubuntu deb may have changed paths or even changed files. 
There is no garantee that it works unless the place you got the patch specifics that it's to be applied to a version/distro deb package.
(Edit: i read now your edit. it seems to be applyed to ubuntu debs, so should give no problem as long as you have the file)

But try to check if your inn2 install that file:
```
dpkg -S innshellvars.pl
```  
will tell you if and where that file was installed

---

### Post by lex1 on 2006-06-29
here we go



:~$ dpkg -S inshellvars.pl
dpkg: *inshellvars.pl* not found.

lex
ps have not applied patch as cannot seem to finf file i am supposed to apply it to?

---

### Post by Rui Pais on 2006-06-29
[QUOTE=lex1]here we go

:~$ dpkg -S inshellvars.pl
dpkg: *inshellvars.pl* not found.

lex
ps have not applied patch as cannot seem to finf file i am supposed to apply it to?[/QUOTE]

the patch apply to that file...

weird, i download  inn2_2.4.2-3_i386.deb and  inn2_2.4.2-3_amd64.deb and both have that file on the path refered on patch...

try to remove inn2 and reintall it again... something seems to failed...

---

### Post by lex1 on 2006-06-29
ok heres the remove and install
and below is the message i received from my postfix server re news

ps where is your pm tab? for personal messages?
lex1


root@xstation:~# aptitude remove inn2
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are unused and will be REMOVED:
  inn2-inews libperl5.8 
The following packages have been kept back:
  gdm gnupg language-pack-en libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libpango1.0-0 libpango1.0-common linux-386 linux-image-386 linux-restricted-modules-386 
  linux-restricted-modules-common pcmcia-cs spamassassin wpasupplicant 
The following packages will be REMOVED:
  inn2 
0 packages upgraded, 0 newly installed, 3 to remove and 15 not upgraded.
Need to get 0B of archives. After unpacking 8864kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 40048 files and directories currently installed.)
Removing inn2 ...
Stopping news server: done.
Removing inn2-inews ...
Removing libperl5.8 ...
root@xstation:~# aptitude install inn2
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  inn2-inews libperl5.8 
The following packages have been kept back:
  gdm gnupg language-pack-en libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libpango1.0-0 libpango1.0-common linux-386 linux-image-386 linux-restricted-modules-386 
  linux-restricted-modules-common pcmcia-cs spamassassin wpasupplicant 
The following NEW packages will be installed:
  inn2 inn2-inews libperl5.8 
0 packages upgraded, 3 newly installed, 0 to remove and 15 not upgraded.
Need to get 0B/3678kB of archives. After unpacking 8864kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Preconfiguring packages ...
Selecting previously deselected package inn2-inews.
(Reading database ... 39807 files and directories currently installed.)
Unpacking inn2-inews (from .../inn2-inews_2.4.2-3ubuntu1_i386.deb) ...
Selecting previously deselected package libperl5.8.
Unpacking libperl5.8 (from .../libperl5.8_5.8.7-10ubuntu1_i386.deb) ...
Setting up inn2-inews (2.4.2-3ubuntu1) ...
Selecting previously deselected package inn2.
(Reading database ... 39833 files and directories currently installed.)
Unpacking inn2 (from .../inn2_2.4.2-3ubuntu1_i386.deb) ...
Setting up libperl5.8 (5.8.7-10ubuntu1) ...

Setting up inn2 (2.4.2-3ubuntu1) ...
Starting news server: done.



I also got this message

-rw-r--r-- 1 news news 82 2006-06-29 10:51 /var/log/news/news.crit
-----
Server running
Allowing remote connections
Parameters c 10 i 50 (0) l 1000000 o 1011 t 300 H 2 T 60 X 0 normal specified
Not reserved
Readers follow enabled
Perl filtering enabled
-----
Jun 29 10:51:23 xstation innd: SERVER cant listen RCreader Address already in use

---

### Post by Rui Pais on 2006-06-29
Now you should have the needed file. It belongs to that package (you can check it in the deb file by open it with file-roller or alike).
```

cd /usr/lib/news/
patch -p1 </path/to/patch
```

I will leave now for a few hours. 
If you have problems don't strange my silence :)

Good luck

---

### Post by lex1 on 2006-06-29
Thanks for your help on this heres the output

total 104
drwxr-xr-x  3 root root  4096 Jun 29 11:37 .
drwxr-xr-x 48 root root 12288 Jun 29 11:37 ..
drwxr-xr-x  5 root root  4096 Jun 29 11:37 bin
-rw-r--r--  1 root root 69162 Dec 22  2004 innreport_inn.pm
-rw-r--r--  1 root root  2526 Mar 15 10:38 innshellvars
-rw-r--r--  1 root root  3008 Mar 15 10:38 innshellvars.pl
-rw-r--r--  1 root root  3462 Mar 15 10:38 innshellvars.tcl
root@xstation:/usr/lib/news# patch -pl /home/admin/patch
patch: **** strip count l is not a number
root@xstation:/usr/lib/news#

---

### Post by Rui Pais on 2006-06-29
So reinstall did the trick. I wonder why that file miss on your first inn2 install...

about patch, thats an easy one, it's patch -p1 (one) not -pl ;)
(i now note that 1 with font inside CODE tags look like "l" letters)

---

### Post by lex1 on 2006-06-29
ok when i run the command as suggested the cursor remains at the beging of the 

line 
ie
r:/usr/lib/news# patch -p1 /home/admin/patch
curser

not flashing just staying still
what is the commend to stop the news server from running 
then i apply the patch?

lex1

---

### Post by Rui Pais on 2006-06-29
hey, thats the patch command hates you :lol:
just joking ;)
[QUOTE=lex1]/usr/lib/news# patch -p1 /home/admin/patch[/QUOTE]
it should be 
> /usr/lib/news# patch -p1 **<** /home/admin/patch

it just replaces line 12 of that file with:
> my $icv = `/usr/lib/news/bin/innconfval -p`;
my %icv;
$icv{$icv}++;
($icv) = keys %icv;
eval $icv;

---

### Post by lex1 on 2006-06-29
many manythanks , 

root@xstation:/usr/lib/news# patch -p1 < /home/admin/patch
patching file innshellvars.pl
root@xstation:/usr/lib/news# 

 how to restart news server with new patch?

lex1

---

### Post by Rui Pais on 2006-06-29
[QUOTE=lex1]many manythanks , 

root@xstation:/usr/lib/news# patch -p1 < /home/admin/patch
patching file innshellvars.pl
root@xstation:/usr/lib/news# [/QUOTE]

Good!

>  how to restart news server with new patch?

i have no idea, since i don't have such a thing installed, but according to logic should be something like:
```
sudo /etc/init.d/inn2 restart
```

---

### Post by lex1 on 2006-06-30
Thanks for all your posts yesterday.

As I mentioned i was following a howto [http://news.aioe.org/article.php3?id_article=18](http://news.aioe.org/article.php3?id_article=18)


I was wondering if there was any reason why i could not do this through my own ISP 
as they provide news service?

Lex1

---

### Post by Rui Pais on 2006-06-30
[QUOTE=lex1]Thanks for all your posts yesterday.[/QUOTE]

No problem, glad i could help :)

> 
I was wondering if there was any reason why i could not do this through my own ISP 
as they provide news service?

Lex1

Sorry i can't help with that one...

May i suggest that you start a new thread on this one. 
Few people will find it here, since it's not mentioned on the title of post or had anything to do with the topic. 

Good luck

---

