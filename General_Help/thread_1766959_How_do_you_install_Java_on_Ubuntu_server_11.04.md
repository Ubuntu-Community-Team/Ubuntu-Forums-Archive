---
title: "How do you install Java on Ubuntu server 11.04?"
date: 2011-05-25
forum: General Help
---

### Post by Jragon on 2011-05-25
Hi!

I was wondering how I would go about installing Java on Ubuntu Server. I need it for my Minecraft server.

Thanks

Jragon

---

### Post by Jragon on 2011-05-25
Anyone

---

### Post by jerryjustly on 2011-05-25
I've only played on the Ubunter server a little, but since you haven't got any replies, I'll try to answer.  From what I've seen it's just like the terminal in Ubuntu.  So you can probably install java with the following commands:

sudo apt-get update
sudo apt-get install openjdk-6-jdk

--------------------
[http://www.dotdeb.com](http://www.dotdeb.com) is a great place to find deb packages

---

### Post by Jragon on 2011-05-25
Would the OpenJDK work with Minecraft?

---

### Post by yangli on 2011-05-25
My friends told me to use

sudo apt-get install ubuntu-restricted-extras

It seems Java was installed then.

---

### Post by Azdour on 2011-05-25
Hi,

I see that some people have had issues with Minecraft and OpenJDK: [http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server](http://www.minecraftwiki.net/wiki/Tutorials/Setting_up_a_server). I've not tried this but you should be able to install by:

```
sudo add-apt-repository ppa:sun-java-community-team/sun-java6

sudo apt-get update

sudo apt-get install sun-java6-jdk


```

Just a word of caution, installing ubuntu-restricted-extras also installs other things you may not want or need on a server.

---

### Post by nathan42100 on 2011-09-15
I realize that this is an old thread, but the above answer did not prove fruitful for me as it asked to install python extras because apt-add didn't exist.

Here is what did work for me:

```

computer$ cd /etc/apt
computer$ sudo vi sources.list
hit "i" to enter insert mode
uncomment out deb and deb-src for partners and main (bottom of file)

esc -> :wq -> enter (saves and quits vi)

computer$ sudo apt-get update
computer$ sudo apt-get install sun-java6-jdk
```

---

