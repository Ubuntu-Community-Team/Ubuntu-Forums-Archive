---
title: "Need to find the location"
date: 2010-09-11
forum: General Help
---

### Post by daddlylo on 2010-09-11
using 10.04 and having problems , just installed it in about 3 hours ago .


need to find the path to ( I am beginner so from the start no geek/ Greek ;) language please)

need to find location of 

GRUB_CMDLINE_LINUX_DEFAULT= ,

 I have to tweak it otherwise I can't do ( lets say my mouse and keyboard freeze if I doesn't tweak it:D) 
 
Daddylo ( new to the forum and Linux)

---

### Post by sikander3786 on 2010-09-11
/etc/default/grub

Is this what you are looking for?

Edit: But don't play with it. You may leave your system non-bootable. :-)

Open it using (in case you don't know)

```

sudo gedit /etc/default/grub

```

---

### Post by dadylo on 2010-09-11
> **sikander3786 said:**
> /etc/default/grub

Is this what you are looking for? 



Edit: But don't play with it. You may leave your system non-bootable. :-)



Open it using (in case you don't know)

```

sudo gedit /etc/default/grub

```


btw where should I put the code , I tried the code xterm ( logged in , I think it is like safe mode in vista something dunno or soemthing similar to regedit like in vista , I dunno just may be  ) put it there and nothing special like opening of folder didn't  nothing happened ...... in normal I can't find a place to put the code :(

---------------------------------

yep that's the folder or configuration thingy I need to open ....

no need to worry , have vista installed and working fine ,

 just need to see this tweak and figure if my computer can handle this or may be trying to buy pc with i7 cpu , 2 GB dedicated graphic card and  fast hard drive just to install linux 10.04 :D

---

### Post by daddlylo on 2010-09-11
off topic , I entered the wrong username and so I thoguht  forgot my password so had to make a new account .... just commneted to say I am the same person me and dadylo 


to go deeper , 
 anyway if there is easy solution ( I know now this bug is fixed but I do not wnt to download beta versiobn to get rid of the probelm ) 

this thread expalin the problem


[http://ubuntuforums.org/showthread.php?t=1497247](http://ubuntuforums.org/showthread.php?t=1497247)  ( the problem)

I do not have the link now somebody said try this ands it will get fixed 

edit/etc/default/grub, go to the line that begins like: ( ***_this is where the problem where do I find this Edit thingy..._***)



GRUB_CMDLINE_LINUX_DEFAULT=

Achange it to:


GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"  after that run this command:

sudo update-grub 

Reboot and that's it ( I print this part only didn't save the link :( ) 


daddlylo

---

