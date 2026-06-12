---
title: "how to use mumudvb please help."
date: 2012-03-13
forum: General Help
---

### Post by hayalperestbk on 2012-03-13
Hi everybody.Im really pretty much new to ubuntu but I have to use ubuntu for my graduation project and I have been trying to install and configure mumudvb.I always have errors.I cant understand any.pls some one tell me how to use mumudvb from the begining.btw I use ubuntu 11.10. 

some example of erro&#305;s 

mrmr-iptv@mrmriptv-MS-7142:~/mumudvb$ ./configure
configure: error: cannot find install-sh, install.sh, or shtool in "." "./.." "./../.."
mrmr-iptv@mrmriptv-MS-7142:~/mumudvb$ autoreconf -i -f
Can't exec "libtoolize": No such file or directory at /usr/bin/autoreconf line 196.
Use of uninitialized value in pattern match (m//) at /usr/bin/autoreconf line 196.
configure.ac:27: warning: macro `AM_ICONV' not found in library
configure.ac:27: error: possibly undefined macro: AM_ICONV
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1

---

### Post by Cheesemill on 2012-03-13
Instead of compiling from source you could try using the Debian packages available here:
[http://packages.debian.org/sid/mumudvb](http://packages.debian.org/sid/mumudvb)

---

### Post by hayalperestbk on 2012-03-13
thank you for your reply.but problem which version I will download of this debian? and how can I use it? because I donwloaded amd64 version but I couldnt use it =( this debian depends on my system ? sorry for my ignorant.

btw my system is this memory =512mb 
                                   cpu= amd sempron 3000+

---

### Post by Cheesemill on 2012-03-13
Edit - See post below

---

### Post by Cheesemill on 2012-03-13
Forget my previous posts, it looks like it's already in the Ubuntu repos.
Just do:
```
sudo apt-get install mumudvb
```
to install.

---

### Post by hayalperestbk on 2012-03-13
thank you soo much Cheesemill I guess I could do it =) but I faced other problem now =(. when I wanna launch mumudvb with exmple configuration file it says this error. 

mrmr-iptv@mrmriptv-MS-7142:~$ mumudvb -d -c example.conf
MuMuDVB Version 1.6
Latest version available from [http://mumudvb.braice.net/](http://mumudvb.braice.net/)

example.conf: No such file or directory

where shall I keep this config file in mumudvb folder?

---

### Post by hayalperestbk on 2012-03-13
I tried this type now.but again errors =(. I guess errors are my destiny =)


  mrmr-iptv@mrmriptv-MS-7142:~/mumudvb$ mumudvb -d -vvv -s -c example.conf
MuMuDVB Version 1.6
Latest version available from [http://mumudvb.braice.net/](http://mumudvb.braice.net/)

You decided to send the RTP header.
Sap announces will be sent
You have enabled the Pat Rewriting
WARNING : Can't create /var/run/mumudvb/chaines_diffusees_carte0: No such file or directory
WARNING : Can't create /var/run/mumudvb/chaines_non_diffusees_carte0: No such file or directory
Streaming. Freq 12015000
FRONTEND DEVICE: /dev/dvb/adapter0/frontend0 : No such file or directory
FE_GET_INFO: Bad file descriptor 
Tunning issue, card 0

closing cleanly. Error 7

Please guys.anyone help me??

---

### Post by hayalperestbk on 2012-03-13
Heyy guys.anyone helps me plsss?

---

### Post by Cheesemill on 2012-03-13
Have you read the instructions?

[http://mumudvb.braice.net/mumudvb/doc/mumudvb-1.6/QUICKSTART.html](http://mumudvb.braice.net/mumudvb/doc/mumudvb-1.6/QUICKSTART.html)
[http://mumudvb.braice.net/mumudvb/doc/mumudvb-1.6/README.html](http://mumudvb.braice.net/mumudvb/doc/mumudvb-1.6/README.html)

---

### Post by hayalperestbk on 2012-03-13
thank you for your help to me cheesemill.I read them and I couldnt launch mumudvb. I did everything like it is written.but I cant understand why it doesnt wanna work. btw where shall I save configuration file ? maybe that's the problem and I dont know where I should save the config file

---

