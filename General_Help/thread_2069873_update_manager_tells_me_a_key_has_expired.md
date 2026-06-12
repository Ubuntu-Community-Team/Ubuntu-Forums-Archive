---
title: "update manager tells me a key has expired"
date: 2012-10-11
forum: General Help
---

### Post by rapattack1 on 2012-10-11
The update manager today told me a key has expired so not sure what to do and what this key is for...appreciate any advice as i am not that experienced yet :0)

---

### Post by drmrgd on 2012-10-11
Have a look at this thread here:  

[http://ubuntuforums.org/showthread.php?t=2056571](http://ubuntuforums.org/showthread.php?t=2056571)

Seems others have run into this, and it's a fairly straightforward fix.  Hope that helps!

---

### Post by rapattack1 on 2012-11-02
Oh thanks sorry it has taken me so long to reply but dealing with injuries from two accidents. Um the  problem or error whatever has not shown itself again so will visit again if it does

---

### Post by rapattack1 on 2012-11-02
OH ok i did an update today and got another one of these things/errors
The other error hasn't happened again but i did what it said on that other thread and it seemed to go well thanks :0)

---

### Post by rapattack1 on 2012-11-04
I got this today

---

### Post by rapattack1 on 2012-11-08
Hi can anyone help? I really don't have the energy or time to upgrade to the latest version of Artistx which i should do so would like to stay with this version as long as i can :0)

---

### Post by rapattack1 on 2012-11-30
Anyone?????

---

### Post by raja.genupula on 2012-11-30
when the linked things won't work we have a common solution to this issue . 

```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

---

### Post by rapattack1 on 2012-11-30
Thanks so much> I got this:
~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for carla: 
carla@carla-desktop:~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by rapattack1 on 2012-12-01
Hi ok are you saying this should have fixed it? It didn't

---

### Post by raja.genupula on 2012-12-02
> **rapattack1 said:**
> Thanks so much> I got this:
~$ sudo rm -rf /var/lib/apt/lists/*
[sudo] password for carla: 
carla@carla-desktop:~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.

```
sudo mkdir /var/lib/apt/lists/partial 
```

sorry man , i am busy . do this and then try again .

---

### Post by rapattack1 on 2012-12-12
Oh yes me too with injuries and physio......
I got this at the end of everything :
E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by rapattack1 on 2013-01-04
Did an upgrade as i gave up and well for other reasons i needed to do it anyway. So this matter is solved now

---

