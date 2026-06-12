---
title: "How to change root password?"
date: 2010-03-08
forum: General Help
---

### Post by GreenRaccoon on 2010-03-08
I'm really new to Linux so this will probably sound like a pretty naive question to most users, but how do you change the root password?

To install Java, I have to type # su into Terminal, which then asks for the password.  What's weird is that when I start typing a password, no characters show up.  I don't know if this is supposed to happen or not.

I've found a bunch of different sites on the Internet that explain how to change the root password, but none of them seem to work for my specific work station.

I've got Ubuntu 9.10 64 bit.  In the GRUB boot menu, I can choose to boot normal or in recovery mode (I'm led to believe older versions don't have this option).

I've tried typing # sudo passwrd into Terminal, but I already have a root password set up apparently, so I can't change it there.

Can someone help?

---

### Post by bcbc on 2010-03-08
Just use your regular user password (the one you chose when you installed ubuntu). Ubuntu has been setup like this. It's normal that you don't see the password when you're typing. 

Just prefix your terminal commands with "sudo" and your gui programs with "gksudo" to elevate your privileges, type in your password and you're good to go.

Instead of "$ su" to get a root shell you must use "$ sudo su" (since you can't login as root on ubuntu without making changes)

---

### Post by colobix on 2010-03-08
Ok I have no idea why you would like to install java using your root account or install anything manually for that matter.
But ok it's your pc.
Here you go:

To enable your root. go to the terminal and type in
```
sudo passwd root
```
Don't forget to lock your root after you're done..
```
sudo passwd -l root
```

But seriously, why don't you just use synaptic to download java?

---

### Post by lemuriaX on 2010-03-08
Root is disabled by default in Ubuntu but your main account should have sudo privileges, and you can update your password at System --> Administration --> Users and Groups.

It is normal when typing the password in a terminal for no asterisks or anything to appear.

---

### Post by GreenRaccoon on 2010-03-09
Oh wow that was easy.  I thought that the root password and the sudo password were the same thing.  Thanks guys!

---

