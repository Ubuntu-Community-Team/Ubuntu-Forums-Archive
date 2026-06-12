---
title: "how to upgrade from 9.04 to 10.04 ?"
date: 2011-07-13
forum: General Help
---

### Post by lion21 on 2011-07-13
I am unable to install
"update-manager-core"

since support for my distribution has already expired 


I tried editing sources.list 
 file  like this


> # Required
deb [http://old-releases.ubuntu.com/ubuntu/lynx](http://old-releases.ubuntu.com/ubuntu/lynx) main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/lynx-updates](http://old-releases.ubuntu.com/ubuntu/lynx-updates) main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/lynx-security](http://old-releases.ubuntu.com/ubuntu/lynx-security) main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/lynx-backports](http://old-releases.ubuntu.com/ubuntu/lynx-backports) main restricted universe multiverse


but when tried installing

> sudo apt-get install update-manager-core 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update-manager-core

---

### Post by pqwoerituytrueiwoq on 2011-07-13
you have to update to 9.10 first
not worth the download time imo just do a clean install of 10.04
separate /home partition would be useful now

---

### Post by Enigmapond on 2011-07-13
> **pqwoerituytrueiwoq said:**
> you have to update to 9.10 first


This is incorrect. 9.04 and 10.04 are both LTS's and it IS possible to upgrade from one LTS to another...however I agree, you will save your  sanity by just doing a fresh install from the LiveCD.

Good Luck!

---

### Post by OldBoy44 on 2011-07-13
> **Enigmapond said:**
> This is incorrect. 9.04 and 10.04 are both LTS's 

8.04 and 10.04 were last LTS releases.  :)

---

### Post by Enigmapond on 2011-07-13
> **aussiebean said:**
> 8.04 and 10.04 were last LTS releases.  :)

OOPS...I hang my head in shame. I just checked the wiki and 9.04 was a standard. lion21, just do a fresh install and none of this will matter...:)

---

