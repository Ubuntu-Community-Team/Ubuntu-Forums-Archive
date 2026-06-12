---
title: "error when trying to get transparent terminals"
date: 2006-06-09
forum: General Help
---

### Post by robio376 on 2006-06-09
Hi,
I've followed the Ubuntu guide for installing trannset but I get this message:

transset-df-4$ make
cc -Wall `pkg-config --cflags xcomposite xfixes xdamage xrender` -c transSet.c
/bin/sh: cc: command not found
make: *** [transSet.o] Error 127

I tried as sudo and I do have alien 
Thanks!

....figured it out Solved

---

### Post by jocko on 2006-06-09
[QUOTE=robio376]
/bin/sh: cc: command not found
[/QUOTE]

I'm not sure, but it looks like you don't have gcc installed?
If not, install it by ```
sudo apt-get install gcc
```

---

### Post by mcduck on 2006-06-09
better get the 'build-essential' package instead, so you don't have to install every tool needed for compiling one-by-one..

'sudo apt-get install build-essential'

---

### Post by robio376 on 2006-06-09
[QUOTE=mcduck]better get the 'build-essential' package instead, so you don't have to install every tool needed for compiling one-by-one..

'sudo apt-get install build-essential'[/QUOTE]

Yeah, Thanks I figured that out as soon as I submitted my post. Just wasn't thinking. But still can't get transparent terminals working on 6.06 LST. All the guides and references point to breezy. Nothing but artifacts and and grey boxes on Dapper!:? 

Thanks anyways!

---

### Post by QUASAR_FREAK on 2006-06-09
You still can use this terminal that support true transparency

[http://www.ubuntuforums.org/showthread.php?t=141307&highlight=urxvt](http://www.ubuntuforums.org/showthread.php?t=141307&highlight=urxvt)

Always worked ok for me.

---

### Post by mcduck on 2006-06-09
If you have supported graphics card, you could also try XGL and Compiz, and get transparent *everything* :D

---

### Post by taurus on 2006-06-09
Aterm is working fine and it's in repo!

---

### Post by 23meg on 2006-06-09
[QUOTE=robio376]Yeah, Thanks I figured that out as soon as I submitted my post. Just wasn't thinking. But still can't get transparent terminals working on 6.06 LST. All the guides and references point to breezy. Nothing but artifacts and and grey boxes on Dapper!:? 

Thanks anyways![/QUOTE]
Which guide did you follow, and how exactly do things fail? Any error messages?

---

### Post by robio376 on 2006-06-10
[QUOTE=23meg]Which guide did you follow, and how exactly do things fail? Any error messages?[/QUOTE]
Thanks for the help... There's no errors that I can find. I'm thinking that I have a problem with a failing video card. I dual boot this system with Fedora 5 and now it's showing artifacts also. I've been wanting to replace my Ati X300 card with a Nvidia card anyways. So now's a good time. Anybody know of a really good nvidia card for LTS? My system is as follows 3.2P4HT 1GB Ram and PCIx16 slot. 
Any ideas would be greatly appreciated!!
Thanks again!

---

