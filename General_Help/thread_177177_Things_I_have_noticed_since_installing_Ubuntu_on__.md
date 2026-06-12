---
title: "Things I have noticed since installing Ubuntu on  5/13"
date: 2006-05-15
forum: General Help
---

### Post by Koori23 on 2006-05-15
First off, this baby seems to use ALOT less resources than XP.

Second thing, my Numlock key doesn't come on by default.. It's a minor thing, just drives me nuts sometimes.

Third Thing. After 3 Days, I have YET to revert back to XP. I can do pretty much everything I used to do. (Granted, I did use Firefox and Gimp in Windows).

Fourth thing. I don't know what process name Firestarter is under.. But I can't see the icon in the tray but when I go to GRC.Com, I'm totally stealthed, Firestarter must be working in the background. (I'm not using a hardware firewall)

I've also never created a "Root" account. So, is Ubuntu operating under standard User rights and then SUDO's that User when it's required? It's odd and I'm not sure if this is a good thing or not.

That's it, again, many thanks to the Ubuntu Community for this amazing product.

---

### Post by aysiu on 2006-05-15
[QUOTE=Koori23]
Second thing, my Numlock key doesn't come on by default.. It's a minor thing, just drives me nuts sometimes.[/quote] You're using Gnome? Paste these commands into a terminal: ```
sudo apt-get update
sudo apt-get install numlockx
``` Uh, before you do that, [make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources).

> 
I've also never created a "Root" account. So, is Ubuntu operating under standard User rights and then SUDO's that User when it's required? It's odd and I'm not sure if this is a good thing or not. It's a great thing. [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by ori.livneh on 2006-05-15
Yes, Koori23, Ubuntu is configured in such a way that no one can log in as root (unless you change things explicitly). Instead, a special configuration file (/etc/sudoers) lets the system know that your account is allowed to execute administration commands, if confirm your password. It's not common among other Linux distributions, but Mac OS X works in the same way, and it's looking like a good way to protect users from doing bad things by accident.

---

### Post by Koori23 on 2006-05-15
I swear, I've used Mandrake, Suse (My Linux knowledge is still limited obviously, but I've seen the marketplace). I must honestly say, everyone, I DO MEAN EVERYONE is forever gracious and warm and most helpful in their replies to new users. I am forever grateful. How shall I repay you all for this expert advice?

Seriously, "stupid question" isn't even in your vocabulary. Flaming isn't either. Amazing.

---

### Post by aysiu on 2006-05-15
[QUOTE=Koori23]How shall I repay you all for this expert advice?[/QUOTE] Cheesy as Haley Joel Osment made it... "Pay it forward."

---

### Post by Koori23 on 2006-05-15
Never seen the movie therefore, don't understand the quote. I assume you mean "spread the word"

---

### Post by aysiu on 2006-05-15
[QUOTE=Koori23]Never seen the movie therefore, don't understand the quote. I assume you mean "spread the word"[/QUOTE] From Wikipedia:> Pay it forward or paying it forward refers to repaying the good deeds one has received by doing good things for other unrelated people.

The phrase "pay it forward" as a moral philosophy first appeared in Catherine Ryan Hyde's novel Pay It Forward and in 2000 it was adapted into a Warner Brothers film, Pay It Forward. In the book and movie it is described as an obligation to do three good deeds for others in repayment of a good deed that one receives, and that such good deeds should be things that the person cannot accomplish on their own. The recipient of such acts of kindness is then expected to do three good deeds for others in repayment for the help they have received. In this way, the need to help each other can spread exponentially through society, creating a social movement with the hopes of making the world a better place.

In practice the philosophy of pay it forward has broadened relative to its literary roots, and now it incorporates a more general flavor of social responsibility and desire to help others in recognition of the help one has received for one's self. It is also sometimes described as being "good for a favor", meaning a willingness to help others (even strangers) on the expectation that it will all come back around in the end.

The first written record of this philosophy might be Jesus' teaching of it to His disciples in verses 34 through 46 of Chapter 25 of the Gospel of Matthew, in the New Testament.

The idea of the book has been championed in real life by the Pay It Forward Foundation. The Foundation focuses on bringing the idea of paying it forward to school age children, parents, and educators. The simple idea of doing good works for others to repay the good that has happened to you is one that can easily be conveyed to children and encourages them to be socially aware and take a role in making the world a better place. It should be noted that the main character of the book was a 12-year-old child, thus giving other children someone they can relate to.

Author Robert Heinlein preached and practiced this philosophy; now the Heinlein Society, a humanitarian organization founded in his name, does so.

In October 2005, Syracuse University's Residence Hall Association began a Pay It Forward Campaign on campus. It spread on campus rapidly, and was noted for entering mainstream Syracuse society as a result. Many other schools have now begun campaigns such as this as well.

---

