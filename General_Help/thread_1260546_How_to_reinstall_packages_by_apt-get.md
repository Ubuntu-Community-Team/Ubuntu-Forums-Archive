---
title: "How to reinstall packages by apt-get?"
date: 2009-09-07
forum: General Help
---

### Post by ankspo71 on 2009-09-07
Hi Everyone,

Because of risking uninstalling dependencies... I would like to know how does a person 'reinstall' a package using apt-get in a terminal without having to uninstall the package first?

For example, if I wanted to reinstall brasero, how could I do that without losing the gnome desktop? I made similar mistake before but I was using synaptic package manager to uninstall something and didn't know what the dependencies were at the time. Now I know what they are (and how important they are), but I am just curious to learn more about apt-get in the terminal. 

I see that 
```
sudo apt-get install brasero
```
will not install it if it is already installed.

Thanks for the learning experiences.
James

---

### Post by Sidewinder1 on 2009-09-07
Synaptic is simply a front end (GUI) for apt-get. IMHO, it's much easier and safer to remove and reinstall using Synaptic. I've done it many times (successfully) without the necessary, correct syntax needed by apt-get. Just my $.02.
HTH,
Side

---

### Post by drs305 on 2009-09-07
```
sudo apt-get install --reinstall brasero
```

You can learn about commands by typing "man <command>" in a terminal.  
Example:  man apt-get


*Please mark the thread solved via the Thread Tools link near the upper right of the original post when you no longer need assistance.*

---

### Post by ankspo71 on 2009-09-07
Thanks Sidewinder1 and drs305,

Yes I use synaptic too... in the full Ubuntu desktop (which I am using now), but I have played around with a mini ubuntu cd as well... where I chose not to install too many packages.

Thanks for the man page tip. I didn't know commands had man pages. That helps alot.

Thanks for the help,
James

---

