---
title: "sudo apt-get install nasm"
date: 2010-06-18
forum: General Help
---

### Post by Silviner on 2010-06-18
Hi Folks,

trying to install nasm in Ubuntu10.04 Desktop

when I use the command nasm, I get the following

The program 'nasm' is currently not installed.  You can install it by typing:
sudo apt-get install nasm

So naturally, I enter it as follows:

~$ sudo apt-get install nasm
And then I get the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nasm

obviously, this is not working, any ideas?
thanks

---

### Post by Silviner on 2010-06-18
Hello again folks,

managed to get around it with Synaptic package installer, after I done a search for updates to repositories.
however, still curious why the sudo command would not work, perhaps it is because only the basic repository of paskages is installed with ubuntu? Just guessing here, I'm new to ubuntu, and linux. 
Anyway was able to proceed with nasm, now its installed. 

regds,
Silviner.

---

### Post by yetiman64 on 2010-06-18
I'm not sure which repo nasm is in, however in System > Administration > Software Sources ensure you have the universe, restricted and multiverse repos ticked, and in the other software tab tick the canonical entries (this enables all basic repositories supplied with Ubuntu).

I did the "sudo apt-get" command you mentioned earlier with this set up and nasm installed without a problem (then uninstalled it with "sudo apt-get purge"). I suspect your problem is in your "Software Source" set up.

---

