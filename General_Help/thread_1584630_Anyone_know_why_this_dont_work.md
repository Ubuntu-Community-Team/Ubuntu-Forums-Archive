---
title: "Anyone know why this dont work?"
date: 2010-09-29
forum: General Help
---

### Post by zuerston on 2010-09-29
Anyone know why this don't work? I thought I had allready installed this but very little info in apt-get output!



xaaxa@xaaxa-desktop:~$ sudo apt-get install Ubuntu restricted extras
[sudo] password for xaaxa: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package Ubuntu
xaaxa@xaaxa-desktop:~$ 




(yes I did)

---

### Post by exclesodia on 2010-09-29
sudo apt-get install ubuntu-restricted-extras

---

### Post by zuerston on 2010-09-29
> **exclesodia said:**
> sudo apt-get install ubuntu-restricted-extras

I tried it that way too man, neither works????


OHHH lemmie check that out ,I see said the blind man!  (Clear as mud!)


Yeha I got it now,its already installed,I knew that! 

"xaaxa@xaaxa-desktop:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xaaxa@xaaxa-desktop:~$ 
"

---

