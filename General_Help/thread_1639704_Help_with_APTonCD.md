---
title: "Help with APTonCD"
date: 2010-12-07
forum: General Help
---

### Post by praveen12 on 2010-12-07
Hello guys,
                I am new to ubuntu. Recently I have downloaded Ubuntu 10.04 ( both 32 and 64 bit) server edition and installed it successfully. To get GUI I have done the following "**apt-get install ubuntu-desktop**" now it was fine. The commanded has downloaded around 400 mb of packages. 
               Now I have installed the ubuntu 10.04 on another server, now I want to get the gui over here so I have used  APTonCD and copied all the packages onto the cd from the first server. 
               On the second server I have issued the following command after placing the cd in the cdrom
               **apt-cdrom add** ( the cdrom was detected and was added to repo successfully) but the problem is now I have issued the following command on the second server as 

 [B]apt-get update
 apt-get install ubuntu-desktop [/B]( when I give this command the packages are again downloaded from the internet rather than the cd)

This was one issue I was facing. So to avoid this I have browsed through the cd and performed the following command

**dpkg -i *.deb** ( This was installing the packages with some errors and failing some dependencies)

Now after issuing the above command I am doing the following

**apt-get upgrade** ( this procedure is bringing down the download to 100 mb)

Guyzzz please help me out as I am planning to use ubuntu on my 15 servers!!!!!

Please forgive me if I have broken any forum rules as this is my first post here!!!

---

### Post by zvacet on 2010-12-07
Aptoncd should do that job fine,but if you have problems with it you can put all content of /var/cache/apt/archives in one folder and then in other machine put folder on hard drive and go inside of it and type

```
sudo dpkg -i *deb
```

After that you can run

```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

Of course that 

```
sudo apt-get upgrade
```

downloaded more packages because you did upgrade of existing packages.Do that on your first machine before you try to copy content of /var/cache/apt/archives to another folder.

---

### Post by praveen12 on 2010-12-08
Thanks a lot bro!!!! Hope that works

---

