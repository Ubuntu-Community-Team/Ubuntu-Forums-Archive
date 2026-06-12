---
title: "Official Ubuntu Dapper Drake 6.06 Repositories?"
date: 2006-06-01
forum: General Help
---

### Post by Galban on 2006-06-01
Today is June 1st 2006 06:20am here in Montreal. Dapper Drake is finally released and my last ¨apt-get update¨ before today (10 min ago), was yesterday at 16:00 local time. So, Am ´ I right or wrong. There is no difference betwin Dapper RC and the 6.06 released, cause my ¨apt-get update that I did 12 min ago doesn´t shows any update since yesterday.  Can somebody having the officiall Dapper Drake 6.06 release repositories, please, share it with us? :-D 

Those are what I have right now on /etc/apt/source.lis :


[HTML]## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf breezy free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf breezy free non-free



[/HTML]

---

### Post by matthew on 2006-06-01
Your repo list is fine. There haven't been any new updates in about 24 hours or more...what you have now is the official release. Congratulations!

---

### Post by Galban on 2006-06-01
[QUOTE=matthew]Your repo list is fine. There haven't been any new updates in about 24 hours or more...what you have now is the official release. Congratulations![/QUOTE]

Thanks for make it clear for us!! :-D

---

### Post by Kabal on 2006-06-01
Can't wait to test the final!! :D

---

### Post by Hezekiah on 2006-06-01
Just to clarify - Dapper has used the same repository from the start of its development, so there hasn't been a development-vs-release repository distinction.  So there were definitely changes between the RC and final release, but since you've been updating regularly (from what it sounds like), you have already upgraded your system to Dapper-final.

---

### Post by suziequzie on 2006-06-02
Thanks.  I used automatix, and somehow it reverted my sources list to breezy when it was done... 

All I was looking for, an official sources list, is now found.  I should keep a copy of it in my home "texts" folder, for future reference.

---

