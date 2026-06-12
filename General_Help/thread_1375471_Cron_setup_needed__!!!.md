---
title: "Cron setup needed  !!!"
date: 2010-01-07
forum: General Help
---

### Post by baday2003 on 2010-01-07
Hello  

Im using Ubuntu  server 
and i installed Dolphin 7 
and i got this  Cron  job


MAILTO=admin@masterb.ca
* * * * * cd /var/www/virtual/web.com/htdocs/dolphin/periodic; /usr/bin/php -q cron.php


how can I  setup it 


this  is what i  did  it  worked somehow and  stopped....


I  ran Terminal 
and wrote 
# pico /etc/crontab
and i added this 

MAILTO=admin@masterb.ca
 * * * * * cd /var/www/virtual/web.com/htdocs/dolphin/periodic; /usr/bin/php -q cron.php

but nothing happened 


I  didnt  get any emails  from the  cron 

anyways  i hope  someone here got idea how to do this ...

thanks
Mr.-B

---

### Post by Grim76 on 2010-01-07
I am no crontab expert but last I checked you need to use the command crontab -e to edit your crontab.

The man pages for crontab also covers some of the conventions used.

---

### Post by baday2003 on 2010-01-07
I  tried  to use  that  but its  too gay and i dont kno how to use it 
so i use pico / nano ( /etc/crontab) 
and i think they are the same ..?

yeah 
it  got this too

/etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --$
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --$
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --$
#



is  it the  right  place ?  ( Im new to this ! :) )

---

### Post by baday2003 on 2010-01-07
SOLVED!!! :popcorn:

> **hyper_ch said:**
> (1) run
```

sudo crontab -u root -l

```(2) if step 1 does not return anything then do
```

cd /root
sudo nano cron.txt

```(3) add the according jobs you want to run as root

(4) save and exit the cron.txt file

(5) add the cron.txt to root cron
```

sudo crontab cron.txt

```(6) verify if it was added:
```

sudo crontab -u root -l

```
I got it  right 
I did what  he said and it  worked  fine :)

---

### Post by baday2003 on 2010-01-12
hello
its me  again



i get this e-mail


cd: 1: can't cd to /var/www/virtual/e-suliman.com/htdocs/periodic
Could not open input file: cron.php

??
i installed postfix 
is  it  from postfix


I need big help 


!!!

---

### Post by baday2003 on 2010-01-16
anyone
?


i cant  run my  site  
till i fix all the problems with the cron !!!


please some help

---

### Post by llamabr on 2010-01-16
My guess is that you've alienated everyone who uses 

crontab -e

by insisting that using it is "gay".

You did so with sudo, for some reason.  Maybe just go back and take grim76's advice

---

### Post by baday2003 on 2010-01-16
i changed it 
nothing happened  still getting the error

and i get it  ever min 
in my email
>?

and i deleted the job but still getting it ? 
:(

---

### Post by r_s on 2010-01-16
Well if you use crontab -e , you also need to check the file permissions (I guess they need to be 755, please check) ...and also in your crontab rather than using "cd" ,you can give the absolute file path , also if you include any files in your file cron.php their paths should be absolute rather than relative as their is a difference while you are executing it from terminal than using it in cron.

---

### Post by abcuser on 2010-01-16
If you don't like vim editor you can change your default editor with command:
```
sudo update-alternatives --config editor
```
and then select the editor from menu.

You HAVE TO!!! use "crontab -e" to edit crontab. It probably will not work any other way.

I suggest you execute "crontab -e" and write command
```
* * * * * echo "Cron is working fine" > ~/cron.out
```

Then wait a minute or two and look for cron.out file in your home directory. If you can see the text you have some other problem beside cron.

Check the file paths, file permissions etc.

---

