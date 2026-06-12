---
title: "permissions denied???"
date: 2010-08-07
forum: General Help
---

### Post by NightWalker187 on 2010-08-07
I recently loaded ubuntu 10.04 as part of a dual boot on a windows 7 machine. And i tried to load the compiz desktop stuff and noticed that not all the options that i was used to were there. i looked it up on-line and found instructions on how to get them. 

the website is:[http://forum.compiz.org/viewtopic.php?&f=114&t=12012](http://forum.compiz.org/viewtopic.php?&f=114&t=12012)

I created the compiz-addons file and place it in the home directory after that was placed i was supposed to 
run a command in the terminal. ~/compiz-addons install all is the command. but when i run it i get:


bjoslin@bjoslin-laptop:~$ ~/compiz-addons install all
bash: /home/bjoslin/compiz-addons: Permission denied
bjoslin@bjoslin-laptop:~$ 


Any ideas on why this is? And can any one help?

---

### Post by corncob on 2010-08-07
start off with 'sudo'

---

### Post by GlazedDonut on 2010-08-07
The file probably doesnt have execute permissions. do:
```
chmod 755 ~/compiz-addons
```

---

### Post by NightWalker187 on 2010-08-07
OK that got passed the password thing but now it says:


sudo: /home/bjoslin/compiz-addons: command not found
bjoslin@bjoslin-laptop:~$ sudo ~/compiz-addons install all
sudo: /home/bjoslin/compiz-addons: command not found
bjoslin@bjoslin-laptop:~$ 


Is there a better way to get the addons? i followed the instructions right from that website that i included.

---

### Post by dv3500ea on 2010-08-07
Try installing [compiz-fusion-plugins-main]("apt:compiz-fusion-plugins-main") and [compiz-fusion-plugins-extra]("apt:compiz-fusion-plugins-extra").

or
```

chmod +x ~/compiz-addons
sudo ~/compiz-addons

```

---

### Post by NightWalker187 on 2010-08-07
That did the trick.

Thanks for your help.

:) :p :) :p

---

