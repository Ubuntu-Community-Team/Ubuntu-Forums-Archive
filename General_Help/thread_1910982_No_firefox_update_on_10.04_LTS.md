---
title: "No firefox update on 10.04 LTS"
date: 2012-01-18
forum: General Help
---

### Post by texpat on 2012-01-18
Hi all,

ubuntu 10.04.3 LTS runs on two of my machines. On one of them firefox was upgraded to v9 recently, but on the other I'm stuck with v3.6.24, even though other updates seem to be going through.

The second computer (the one that doesn't update firefox) runs the 64-bit version of ubuntu, while the other runs 32-bit ubuntu.

I've done apt-get-uptade and apt-get-upgrade, which didn't help.

Rather than manually installing FF, I'd like to do this from the repositories, so if anyone has any ideas that may help...?

Thanks for reading.

---

### Post by plucky on 2012-01-18
> **texpat said:**
> Hi all,

ubuntu 10.04.3 LTS runs on two of my machines. On one of them firefox was upgraded to v9 recently, but on the other I'm stuck with v3.6.24, even though other updates seem to be going through.

The second computer (the one that doesn't update firefox) runs the 64-bit version of ubuntu, while the other runs 32-bit ubuntu.

I've done apt-get-uptade and apt-get-upgrade, which didn't help.

Rather than manually installing FF, I'd like to do this from the repositories, so if anyone has any ideas that may help...?

Thanks for reading.


Have you install the Mozillateam PPA on your 32-bit system?

Both my 64-bit and 32 bit Lucid systems are running 3.6.24 version of Firefox.

Just a thought.

Good luck

---

### Post by raja.genupula on 2012-01-18
+1 to Plucky 

@op 
do this by opening your terminal 
```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update 
sudo apt-get install firefox
```

it will gives firefox 9 .
all the best.

---

### Post by eminnyEntaisE on 2012-01-18
Thank you for the auspicious writeup. It in fact was a amusement account it. Look advanced to more added agreeable from you! By the way, how could we communicate? [garage door repair Katy Texas](http://www.corolla-forum.com/9th-generation-2003-2008/893-car-wont-start-but-turns-over-had-been-low-gas-added-gas-no-change.html#post1524)

---

### Post by texpat on 2012-01-18
Thanks guys, that did it!

---

