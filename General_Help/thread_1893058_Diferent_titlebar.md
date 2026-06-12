---
title: "Diferent titlebar"
date: 2011-12-09
forum: General Help
---

### Post by javidemon95 on 2011-12-09
The titlebar has changed when I installed mate. I don t like it. I want it will be the default.
Here is a screenshot [http://www.imagenonline.com/img_a223914.png](http://www.imagenonline.com/img_a223914.png)
And it changed the context menu. Now it has icons, and i dont wont them
Sorry for my bad english

---

### Post by BC59 on 2011-12-09
Let's see now.
To use Mate I assume you are using LinuxMint.
There is a tool to make changes to the titlebar.
It's called Advanced Settings. If you don't have it you can install it from the software center.
Open it and to the left panel the last option is Windows. From there you can make some changes.

---

### Post by BC59 on 2011-12-09
And here are some tricks you can do in LinuxMint

[http://www.techsupportalert.com/content/tips-and-tricks-linux-mint-after-installation.htm](http://www.techsupportalert.com/content/tips-and-tricks-linux-mint-after-installation.htm)

---

### Post by javidemon95 on 2011-12-09
I have installed mate on ubuntu

---

### Post by BC59 on 2011-12-09
Yes I know, but your Ubuntu now is converted to LinuxMint. You don't have Ubuntu repositories but Mint.

---

### Post by javidemon95 on 2011-12-09
> **BC59 said:**
> Yes I know, but your Ubuntu now is converted to LinuxMint. You don't have Ubuntu repositories but Mint.
What can I do?

---

### Post by Frogs Hair on 2011-12-09
If Mate includes a configuration editor you may be able the remove the menu from there as was possible from Gnome 2 .

I know Mate is based on Gnome 2.xx but haven't used or seen it yet and don't know if Advanced Settings as it is in Gnome 3 will work with Mate  . I could be that BC59 is referring to a different application .

---

### Post by qamelian on 2011-12-09
> **BC59 said:**
> Yes I know, but your Ubuntu now is converted to LinuxMint. You don't have Ubuntu repositories but Mint.
 Not so. You don't need to be running Mint to use Mate, just because Mint allows you to use Mate. You can use Mate on Ubuntu and still use Ubuntu repos. There's a thread on here on the forum discussing how to install Mate on Ubuntu.

---

### Post by BC59 on 2011-12-09
You can make changes with the tool I said. 

To get back to Ubuntu it's impossible with tricks. The only way is to reinstall Ubuntu.

---

### Post by BC59 on 2011-12-09
> **qamelian said:**
> Not so. You don't need to be running Mint to use Mate, just because Mint allows you to use Mate. You can use Mate on Ubuntu and still use Ubuntu repos. There's a thread on here on the forum discussing how to install Mate on Ubuntu.

Yes that's me one of the victims they followed the instructions. It's not exactly LinuxMint but it's not Ubuntu either. And if you try to logon again to Ubuntu you have some nasty surprises.

---

### Post by qamelian on 2011-12-09
> **BC59 said:**
> Yes that's me one of the victims they followed the instructions. It's not exactly LinuxMint but it's not Ubuntu either. And if you try to logon again to Ubuntu you have some nasty surprises.
 I've played with it and haven't had any surprises that I considered nasty. Logically, it will call problems with the stock Ubuntu, becasue of the differences between Gnome 2 & 3. I just did it to try it out on a test box anyway. I much prefer Gnome-shell to Gnome 2 any day of the week. :)

---

### Post by BC59 on 2011-12-09
> **qamelian said:**
> I've played with it and haven't had any surprises that I considered nasty. Logically, it will call problems with the stock Ubuntu, becasue of the differences between Gnome 2 & 3. I just did it to try it out on a test box anyway. I much prefer Gnome-shell to Gnome 2 any day of the week. :)

Then have a look to your /etc/lsb-release and /etc/update-motd.d. It's not Ubuntu it's Mint. And I don't know what else is changed.

In a while you will be unable to use your Ubuntu Software center and Synaptic.

---

### Post by javidemon95 on 2011-12-09
I changed  /etc/lsb-release and I write: 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=Oneric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
and then edit /etc/*issue
Ubuntu 11.10 n l

with this you are back to ubuntu
but i will reinstall ubuntu

---

### Post by BC59 on 2011-12-09
> **javidemon95 said:**
> I changed  /etc/lsb-release and I write: 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=Oneric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
and then edit /etc/*issue
Ubuntu 11.10 n l

with this you are back to ubuntu
but i will reinstall ubuntu

It's not that easy. The changes are rejected and they get you back to Mint.
If you reinstall Ubuntu don't forget to create a separate ~/home partition.

---

### Post by qamelian on 2011-12-09
> **BC59 said:**
> Then have a look to your /etc/lsb-release and /etc/update-motd.d. It's not Ubuntu it's Mint. And I don't know what else is changed.
 
In a while you will be unable to use your Ubuntu Software center and Synaptic.
 I have. It still says Ubuntu. I don't care about Software Centre because I don't like it and don't use it. I haven't had any problem using Synaptic, but I only use it rarely for a few specific purposes. Besides, like I said, I just tried it out on a spare test box. I can't imagine any scenario where I would want to go back to Gnome 2, personally. I find Gnome 3 with Gnome-shell to be much more comfortable and productive for my needs.

---

### Post by BC59 on 2011-12-09
> **qamelian said:**
>  I can't imagine any scenario where I would want to go back to Gnome 2, personally. I find Gnome 3 with Gnome-shell to be much more comfortable and productive for my needs.

I totally agree. Gnome 2 looks primitive now.

---

