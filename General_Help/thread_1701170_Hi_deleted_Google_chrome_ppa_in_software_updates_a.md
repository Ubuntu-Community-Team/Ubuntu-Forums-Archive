---
title: "Hi deleted Google chrome ppa in software updates and  Canonical partner ppa vanished"
date: 2011-03-06
forum: General Help
---

### Post by Mat11 on 2011-03-06
Hi i recently deleted Google chrome ppa in the (software manager/ other software) checking it twice beforehand nothing else was ticked.Once i pressed delete i lost Canonical partners (think it was main) the one i have left is Canonical partners source.

The reason for doing this was because after i updated Google chrome and one other i noticed that my security extensions in both had partially failed and i could not see a padlock security symbol in my web mail start pages.

Can anyone help.

A bit stuck.

Mat

---

### Post by howefield on 2011-03-06
Try adding the lines here substituting your verion instead of hardy...

[https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Partner%20Repositories](https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Partner%20Repositories)

---

### Post by Mat11 on 2011-03-06
> **howefield said:**
> Try adding the lines here substituting your verion instead of hardy...

[https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Partner%20Repositories]("https://help.ubuntu.com/community/Repositories/CommandLine#Adding%20Partner%20Repositories")

Thanks for the reply but i'm using maverick 10.10 and noticed your highlighted line takes you to hardy not 10.10

---

### Post by howefield on 2011-03-06
The line in my Maverick install sources.list is

```
deb http://archive.canonical.com/ubuntu maverick partner
```

---

### Post by Mat11 on 2011-03-06
> **howefield said:**
> The line in my Maverick install sources.list is

```
deb http://archive.canonical.com/ubuntu maverick partner
```

Could you let me know what is under (other software) in update manager regarding partner source -- what is the other partner .... ?, would really help thank.

---

### Post by runeh76 on 2011-03-06
Do u mean this: ```
deb-src http://archive.canonical.com/ubuntu maverick partner
```

---

### Post by Mat11 on 2011-03-06
Have to go can only answer later will take a closer look at the source list thank you.

---

### Post by Mat11 on 2011-03-06
> **runeh76 said:**
> Do u mean this: ```
deb-src http://archive.canonical.com/ubuntu maverick partner
```

Hi i've deleted one of the Canonical Partners in system, admin,update manager,other software/software sources.Still have the one mentioning  Canonical partners source 
code underneath its says software packaged by Canonical for their partners.

Need to find out how to recover the other one in software updates as the updates have now completely failed. I know i didn't make error because i double checked there was only one tick in google chromes box no where else !!!
Forget i mentioned ppa thats confusing things i remember that from my old Karmic system.

Can you let me know what you see in other software sources in Maverick 10.10 ?

Would really help Thanks.

Mat

---

### Post by runeh76 on 2011-03-07
I dont know exactly what u need, so i paste my sources.list. U can copy and paste it to ur **sources.list**
```
gksu gedit /etc/apt/sources.list

```




#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse

###### Ubuntu Update Repos
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse
deb [http://fi.archive.ubuntu.com/ubuntu/](http://fi.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos


#### GetDeb - [http://www.getdeb.net](http://www.getdeb.net)
## Run this command: wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) maverick-getdeb apps

---

