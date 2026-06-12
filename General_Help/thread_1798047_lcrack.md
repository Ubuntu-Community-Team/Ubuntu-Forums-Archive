---
title: "lcrack"
date: 2011-07-05
forum: General Help
---

### Post by reidar5 on 2011-07-05
Hello

 I'm trying to get Lcrack to work.
What do I have to write,to for example activate mode "b"?

The programme is run in terminal,and looks like this:

lcrack: method must be specified (-m), exiting..
usage: lcrack [-q | -v] -m <method> [<opts>] <file> ..
 -o  <file>     : output password file
 -d  <file>     : use word list from <file>
 -t  <file>     : use pre-computed word list from <file>
 -s  <charset>  : use specified charset for incremental
 -s# <name>     : use charset from charset.txt file
 -l  <lenset>   : use specified length-set for incremental
 -g  <regex>    : enumerate regex for incremental
 -g# <name>     : use regex from regex.txt file
 -x<mode>[+|-]  : activate/deactivate specified mode
   mode = l     : login mode
   mode = f     : fast word list mode
   mode = s     : smart word list mode
   mode = b     : incremental (brute-force) mode
 -stdin         : stdin (external) mode
 -rand          : randomized brute-force mode
 -h             : display usage information and exit
 <method>       : hash algorithm, one of:
                { 'dom' 'md4' 'md5' 'nt4' 'null' 'sha1' }

---

### Post by Dangertux on 2011-07-05
Assuming that this is for legal purposes ie: Auditting your own passwords. (anything else is against coc) 

The readme file which can be found here [http://usuarios.multimania.es/reinob/lcrack/README](http://usuarios.multimania.es/reinob/lcrack/README)

Or in the source directory for lcrack would be your first destination. 

However for this type of work I would recommend  both hashcat and rainbow crack are faster and can utilize a gpu (which makes processing much faster

---

### Post by slevinfcross on 2012-01-11
Thank you! 

I was also looking for a tutorial for **lcrack** which is available in Ubuntu software center (it least in 10.10). It is fun and frightening at the same time, that the program can break a 8 chars md5 password in a few minutes.  

According to the documentation above, the most simple (brute force) syntax is: **~$ lcrack -m md5 -xb+ passwd.txt** 

Just in case someone is looking for a sample syntax. ;)

---

