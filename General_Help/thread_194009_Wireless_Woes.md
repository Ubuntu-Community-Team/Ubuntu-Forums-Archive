---
title: "Wireless Woes"
date: 2006-06-10
forum: General Help
---

### Post by Vyizis on 2006-06-10
I have just installed dapper on my laptop (dell inspiron 1200) and so far i am impressed all of the ACPI and shortcut keys work straight away. The only problem is my wireless card (BT Voyager 1060 uses bcmw15 driver) wont work.

I have done the following so far:-
```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i ~/Desktop/bcmwl5.inf
sudo ndiswrapper -m
```

The card is detected by the system lspci picks it up but it just wont start.

This is getting me no where, anybody have any ideas?

---

### Post by evilghost on 2006-06-10
Does lsmod show ndiswrapper as being loaded?

Also, did you add bcm43xx to /etc/modprobe.d/blacklist?

Hope this helped.

---

### Post by Vyizis on 2006-06-10
Yes lsmod shows it to be loaded.

> Also, did you add bcm43xx to /etc/modprobe.d/blacklist?

im not using that driver file would i need to add bcmwl5 there instead?

---

### Post by Vyizis on 2006-06-11
I could  really do with some help with this guy's. I have read through all of the other posts about this card and there is nothing there to help. It starting to drive me crazy.

---

### Post by deathbyswiftwind on 2006-06-11
try entering this command into a terminal and reboot see what happens

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by Vyizis on 2006-06-11
It came back with

```
blacklist bcm43xx
```

---

### Post by deathbyswiftwind on 2006-06-11
Lol sorry I didnt explain myself try restarting and see if your networking will work. Your card takes the same driver as my card. This is the only cure Ive found to running ndiswrapper is you have to kill (blacklist) the linux native driver. So please restart and see if that did the trick

---

### Post by Vyizis on 2006-06-11
That did the trick thankyou. I didnt even reailse there was a linux native driver for this card.

Anyhow Thanks Again

---

### Post by deathbyswiftwind on 2006-06-11
Good Im glad it worked for you. The linux native driver doesnt work I dont think without using fwcutter due to licensing. One thing you may want to consider is saying that command as a text document that way if you ever format you have it on hand. Thats what I do since I like to experiment :)

---

### Post by Vyizis on 2006-06-12
I have written a bash script to do it for me as i do tend to mess around, i have reinstalled my laptop 5 times in the last two days! Thanks for your help.

---

### Post by deathbyswiftwind on 2006-06-15
Hey you mind posting this script I wanted to write one myself but wasnt sure how to :)

---

### Post by Motorbikeman on 2007-03-04
Hi there,

Apologies for digging up an old thread but it would appear that you've fixed a problem I will be facing.

I'm considering installing Ubuntu and one of the things I will need to do is to configure my BT Voyager 1060 wireless card. As I am totally new to both Ubuntu and also Linux in general I would be hugely appreciative if someone could either post a complete step by step guide to doing this, point me in the direction of one if I've missed it while searching or pm/email me with the how to.

Many thanks in advance

---

