---
title: "Installing ircd-hybrid"
date: 2006-01-30
forum: General Help
---

### Post by Squirrel44 on 2006-01-30
Hi,

I've just installed the base install of ubuntu on an old laptop of mine that I'm going to use as a basic server - FTP, IRC (just for my friends and myself) and a shell really.  I've not got x windows or anything installed.

I've just got the source of ircd-hybrid off their webpage and I'm trying to compile it now.

First time I tried I forogt I didn't have gcc installed so I installed gcc via "apt-get install gcc".

Now when I run the configure script I get the error:
"checking for C compiler default output file name... configure: error: installation or configuration problem: C compiler cannot create executables"

I'm not exactly new to Linux, but I'm no expert, so could anyone point out what's wrong?  I can post the config.log file if it is needed.

Thanks.

---

### Post by Adrian on 2006-01-30
Try installing the "build-essential" package.

---

### Post by Squirrel44 on 2006-01-30
Thanks for that Adrian but I've just done a bit more searching and found out what my problem was.

The lic-* abd glibc-* libraries weren't installed so I installed them and it's compiled ok now.

Thanks.

---

### Post by animatrix on 2006-12-09
double up removed

---

### Post by animatrix on 2006-12-09
ok im definately a newbie on this one 

i have  xubuntu terminal based server 

i need to add repositories and i cant remember how and i also need to download instal and configure the ircd as well and then i will need to dl and install anope too 
i knwo how to do anope i hope lol

but what i cant remember is how do i enable multiverse and universe
and all other levels 
so i can access all files even un supported ones 

is there a newbie how to i can read i cant see the manual and dont knwo where to start lookin i have trouble absorbing lots of details so a simple how to would suffice if someone can be so kind

---

