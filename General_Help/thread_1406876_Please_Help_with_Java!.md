---
title: "Please Help with Java!"
date: 2010-02-14
forum: General Help
---

### Post by 131bobby313 on 2010-02-14
Can somebody please give me some clear instructions on how to install java, and not direct me to some other page because I just need some clear instructions. I don't know anything about ubuntu really, but I really need to get java installed.

Im running ubuntu 8.04, Im using the browser mozilla firefox. I want java so I will be able to play some game on the internet. 

So if you could please give complete instructions, and don't I have to like update the apts? or something, if so let me know the command for that, thanks so much in advance guys I really need to figure this out.

---

### Post by j.bell730 on 2010-02-14
Go to **Applications** > **Accessories** > **Terminal**, and type in (or copy and paste, whatever you want):
```
sudo apt-get install ubuntu-restricted-extras
```

Hope this helps.

---

### Post by ron999 on 2010-02-14
> **j.bell730 said:**
> Go to **Applications** > **Accessories** > **Terminal**, and type in (or copy and paste, whatever you want):
```
sudo apt-get install ubuntu-restricted-extras
```

Hope this helps.

That didn't work for me.
I had to use the instructions from this website (section 4) here:-[http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by nnamdi on 2010-02-14
go to synaptics and install java and all its component then if u want to use an ide you get netbeans for linux on ubuntu a .deb or .sh file depending good luck in your findings lemme know how you went easy....

---

### Post by lovinglinux on 2010-02-14
> **131bobby313 said:**
> Can somebody please give me some clear instructions on how to install java, and not direct me to some other page because I just need some clear instructions. I don't know anything about ubuntu really, but I really need to get java installed.

Im running ubuntu 8.04, Im using the browser mozilla firefox. I want java so I will be able to play some game on the internet. 

So if you could please give complete instructions, and don't I have to like update the apts? or something, if so let me know the command for that, thanks so much in advance guys I really need to figure this out.

What game do you want to play? Games are usually flash based. Sometimes you will receive a message that you need flash plugin or javascript to see the content/play the game. Javascript is not the same as java. Anyway, those alerts are usually related to flash plugin conflicts.

To solve those issues follow [this](http://lovinglinux.megabyet.net/?page_id=220#Removing-Conflicting-Plugins-2).

If you really need Java, then [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by xdemo on 2010-02-14
Heres a really nice guide for a manual install:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Its pretty simple and ensures you are using the latest version even if the repositories are not up to date with the latest sun-java package.

---

### Post by lovinglinux on 2010-02-14
> **xdemo said:**
> Heres a really nice guide for a manual install:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Its pretty simple and ensures you are using the latest version even if the repositories are not up to date with the latest sun-java package.

I imagine what the OP will think when he/she reads all these posts with the same link to the easylinuxtipsprojec tutorial :)

---

