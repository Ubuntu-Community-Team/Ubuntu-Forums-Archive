---
title: "problem in registering the entry"
date: 2012-03-18
forum: General Help
---

### Post by zxc_0 on 2012-03-18
hi everybody 

i want to introduce my problem

when registering the entry write password  press enter show small window black if press button exit Write me display 

all Possibilities  y or n if enter y show  me all program

what solve and thank you

---

### Post by TeoBigusGeekus on 2012-03-18
>>>>

---

### Post by zxc_0 on 2012-03-18
what solve not Joke

---

### Post by TeoBigusGeekus on 2012-03-18
Sorry mate, that was just a way for me to tell you that I didn't understand a word of your first post.
Could you please describe as plain and simple as you can what your problem is?

---

### Post by zxc_0 on 2012-03-18
[SIZE=2]i cannot log in[/SIZE]

---

### Post by Helen McCall on 2012-03-18
I think this might be a good time for a moderator to step in and find out if there is any language that zxc_0 can use to explain the problem. Typing with larger font is not going to help here.

---

### Post by zxc_0 on 2012-03-18
What do you want

---

### Post by zxc_0 on 2012-03-19
To raise

---

### Post by matt_symes on 2012-03-19
Hi

I also don't understand your problem.

Can you post a screen shot of your problem or take a picture with a camera and upload it here ?

Kind regards

---

### Post by zxc_0 on 2012-03-19
The problem can not log in the original user
While the user guest can log in

understood yes or no

---

### Post by matt_symes on 2012-03-19
Hi

Boot into a LiveCD/USB and check the permissions of the file

```
.XAuthority
```

You want permissions that look like this

```
matthew@matthew-Aspire-7540:~$ ls -l .Xauthority 
-rw------- 1 matthew matthew 118 Mar 17 22:48 .Xauthority
matthew@matthew-Aspire-7540:~$
```

Make sure you are the owner of that file.

Also, create a new user from the recovery console from the grub menu.

```
adduser user
```

Answer the questions asked and enter a password.

Add the user to these groups.

```
usermod -aG adm,cdrom,sudo,plugdev,lpadmin user
```

Reboot your PC using

```
reboot
```

Try to login as user. Can you login as the new user ?

Kind regards

---

### Post by zxc_0 on 2012-03-26
thank you very very much but How burn Ubuntu to usb

---

### Post by matt_symes on 2012-03-27
Hi

Take a look at unetbootin.

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Kind regards

---

### Post by zxc_0 on 2012-04-05
Now. all user not work what I do

---

### Post by zxc_0 on 2012-04-05
To raise

---

### Post by zxc_0 on 2012-04-06
Forgot something, which is that black screen i can write command like terminal

What type

---

### Post by zxc_0 on 2012-04-06
i wrote  this  command 


fsck -y after Writing appear me


fsck from until - linux 2.19.1

e2fsck 1.41.14.( 22-dec-2010)

/dev/sda1 is mounted

warning !!! the filesystem is mounted . if you continue you ***WILL***

cause *** severe*** filesystem damage.

DO you real want to continue y / n


what write yes or no

---

### Post by zxc_0 on 2012-04-06
To raise

---

### Post by TeoBigusGeekus on 2012-04-06
If you want to check a partition for damage and repair it, the partition has to be unmounted.
Better do this from a live cd/usb.

---

### Post by zxc_0 on 2012-04-07
> **TeoBigusGeekus said:**
> If you want to check a partition for damage and repair it, the partition has to be unmounted.
Better do this from a live cd/usb.


burn on usb but I do not know what to do

---

### Post by zxc_0 on 2012-04-07
To raise

---

### Post by zxc_0 on 2012-04-08
To raise

---

### Post by zxc_0 on 2012-04-08
To raise

---

### Post by zxc_0 on 2012-04-09
write command fsck - y

appear me this Options


p- automatic repair (no questions


n- make no change to the filesysem

y- assume "yes to all questions 

-c- check for bad  block and add them to the bad lock list 

f- force checking even if filesysem is marked clean 


-v be verbose 

-b- supeblock    use alterrative superblock 

-  B -force blocksize when looking for superlock 

 -j -external_ journal     set loction of external journal 

i- bad _ block _ file      add to bad locks list 


l- bad _block _ file    setv bad locks list



what Options choose

---

### Post by zxc_0 on 2012-04-12
someone answer me

---

### Post by jwbrase on 2012-04-12
What is your native language?

Español? Français? Deutsch? &#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;? &#26085;&#26412;&#35486;? &#20013;&#25991;?

---

### Post by tea for one on 2012-04-12
> **jwbrase said:**
> What is your native language?

Español? Français? Deutsch? &#1056;&#1091;&#1089;&#1089;&#1082;&#1080;&#1081;? &#26085;&#26412;&#35486;? &#20013;&#25991;?

Yes, I agree.

There is definitely a language difficulty here.

We need to know the native language of the original poster so that somebody can step forward and communicate in their mother tongue.

---

### Post by zxc_0 on 2012-04-12
why question

---

### Post by jwbrase on 2012-04-12
> **zxc_0 said:**
> why question

Because we want to find somebody who can speak your language to help you.

---

### Post by tea for one on 2012-04-12
> **zxc_0 said:**
> why question

Yes, indeed, there is a wealth of help available here in a multitude of languages.

Even when English is the native language of both parties, there are often misunderstandings and unresolved problems. Computer technology has its own register and you often read that new users ask for replies in plain English or non-technical language.

---

### Post by zxc_0 on 2012-04-12
my native language is arabic

 i don't expect it support you have

---

### Post by zxc_0 on 2012-04-12
somebody response

---

### Post by tea for one on 2012-04-12
Possibly one of these may help:-

Arabic

Algeria

    IRC: #ubuntu-dz on irc.freenode.net
    Forum: [http://algeria.ubuntuforums.org](http://algeria.ubuntuforums.org)
    Wiki: [https://wiki.ubuntu.com/AlgerianTeam](https://wiki.ubuntu.com/AlgerianTeam)
    Mailing List: [https://lists.launchpad.net/ubuntu-dz](https://lists.launchpad.net/ubuntu-dz)


Egypt

    IRC: #ubuntu-eg on irc.freenode.net
    Website: [http://www.ubuntu-eg.org/](http://www.ubuntu-eg.org/)
    Forum: [http://egypt.ubuntuforums.org/](http://egypt.ubuntuforums.org/)
    Mailing List: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-eg](https://lists.ubuntu.com/mailman/listinfo/ubuntu-eg)


Jordan

    IRC: #ubuntu-jo on irc.freenode.net
    Website: [http://www.ubuntu-jo.org/](http://www.ubuntu-jo.org/)
    Forum: [http://ubuntuforums.org/forumdisplay.php?f=320](http://ubuntuforums.org/forumdisplay.php?f=320)
    Mailing List: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-jo](https://lists.ubuntu.com/mailman/listinfo/ubuntu-jo)


Morocco

    IRC: #ubuntu-ma on irc.freenode.net
    Website: [http://www.ubuntu-ma.org/](http://www.ubuntu-ma.org/)
    Forum: [http://morocco.ubuntuforums.org](http://morocco.ubuntuforums.org)
    Mailing List: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-ma](https://lists.ubuntu.com/mailman/listinfo/ubuntu-ma)


Saudi Arabia

    IRC: #ubuntu-sa on irc.freenode.net
    Forum: [http://ubuntuforums.org/forumdisplay.php?f=264](http://ubuntuforums.org/forumdisplay.php?f=264)
    Mailing List: [http://groups.google.com/group/ubuntu-sa](http://groups.google.com/group/ubuntu-sa)
    Wiki: [http://wiki.ubuntu.com/SaudiTeam](http://wiki.ubuntu.com/SaudiTeam)


Tunisia

    IRC: #ubuntu-tn on irc.freenode.net
    Website: [http://www.ubuntu-tn.org/](http://www.ubuntu-tn.org/)
    Forum: [http://tunisie.ubuntuforums.org](http://tunisie.ubuntuforums.org)
    Mailing List: [https://lists.ubuntu.com/mailman/listinfo/ubuntu-tn](https://lists.ubuntu.com/mailman/listinfo/ubuntu-tn)


Yemen

    IRC: #ubuntu-ye on irc.freenode.net
    Forum: [http://ubuntuforums.org/forumdisplay.php?f=387](http://ubuntuforums.org/forumdisplay.php?f=387)
    Mailing List: [http://lists.launchpad.net/ubuntu-ye](http://lists.launchpad.net/ubuntu-ye)
    Wiki: [https://wiki.ubuntu.com/YemenTeam](https://wiki.ubuntu.com/YemenTeam)

---

### Post by zxc_0 on 2012-04-13
Appeared  me recovery menu

There are several order


first choice resume              resume normal boot 

second      fsck                             check all file system( will exit read-only mode )

third       remount                     remount  / read / write and mount  all other file system

Fourth      root                            drop to root shell prompt



what Choose

---

### Post by zxc_0 on 2012-04-14
To raise

---

### Post by zxc_0 on 2012-04-15
I wrote command sudo su startx 

appear me unknown id : startx

 
what can  i do

---

### Post by zombifier25 on 2012-04-15
> **zxc_0 said:**
> I wrote command sudo su startx 

appear me unknown id : startx

 
what can  i do
It's sudo startx.
However, most people on your forum has lost track of your problem anyway. You should try a forum of your native language. It would be easier.
Or start a new thread altogether.

---

### Post by zxc_0 on 2012-04-15
thNK YOU

---

