---
title: "X over ssh between Windows and Ubuntu?"
date: 2010-02-07
forum: General Help
---

### Post by mahela007 on 2010-02-07
Hello.. 
With the assistance of some very helpful (and patient ;-) ) members of this forum, I manged to install an ssh server on my Ubuntu PC and use X 'tunneling' to connect to it using another Ubuntu PC. 
However, I'd like to know how to connect a PC running windows to an X window session on linux. I've googled for this topic but all the articles and threads I read ramdomly use terms like puTTY and Xming to name a few. I'd really like to know what the pieces of software are and how they should be used to make a ssh connection between windows and Ubuntu so that I can use GUI programs installed on my Ubuntu PC from my windows PC.
Thanks...

---

### Post by clenched_sphere on 2010-02-09
Hi,    

I don't know much about this, I'm trying to do something similar myself.  

But I do know of puTTy, it's a handy swiss army knife of SSH and SFTP and is extremely helpful when connecting from a winblowz (sorry lol) pc to a proper comp with linux or unix on.  You can get it from the link below, it's free and pretty much self explanatory when you run it. It runs from an .exe file, no install needed.   

[http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") 

If you get anywhere with this, please post up what you did and where you got to, if I get any further myself I'll throw something up here. 

also, as far as I know, all you need for a remote X session over SSH is for the remote machine to have a barebones X client installed, in Ubuntu you can do this by typing:    

sudo apt-get install xauth

 You also need an X server installed on your machine (It might seem that it needs to be the other way around, but you should have the Xserver on your machine and the client on the remote. wierd I know) 

That's about the limit of my knowledge on the subject, I'm stabbing round in the dark otherwise.

 Hope this helps you out    

Thanks 
   Alan

---

### Post by mahela007 on 2010-02-09
I did make some progress.. in fact I got it working once. (couldn't try it again though).
Here's what I did.
I installed the ssh server on Ubuntu
I installed Xming on windows.


I then installed the portable version of putty (I just though the portable version would be handy) on my flash drive and with Xming running, I started putty on my windows PC. 
In the putty window, I entered the IP adress of the my Ubuntu PC and then enabled X over ssh. (use the tree menu on the right of the screen. X is under the part titled 'ssh')
Click 'open' in the putty window.
You should then get a terminal which you can use to login to Ubuntu. Then just type of the name of and GUI app and you should get a window on you windows PC.

---

### Post by clenched_sphere on 2010-02-15
:(
haven't managed to get anywhere with this, but I'm also wrestling with samba configuration atm which is much more of a mindf**k lol.

thanks for posting back, once i finally finish off samba I'm gonna get back to this :D

---

### Post by mahela007 on 2010-02-15
There's a very good samba HOWTO on these forum. Try googling for samba configuration HOWTO at website: ubuntuforums.org
or just use the forums search functions.

---

