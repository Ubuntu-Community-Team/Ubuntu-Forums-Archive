---
title: "apt-get ultimate failure for me"
date: 2011-09-25
forum: General Help
---

### Post by leppel on 2011-09-25
Hello! I just installed ubuntu server 9 on a compaq Proliant 1600 server. The install and boot went okay, but I ran into some issues. I am on command line only, and am trying to update for the ubuntu desktop and to get other software, but everytime, no matter what i try to install, it says "couldnt find package [insert package here]. It is KILLING me, and I cant get it to work! the internet connection is fine, no troubles. Please help! i have un-commented ALL entries in the /etc/apt/sources.list except for the deb-cdrom entries. 

Please help!

I have attached a link of the specs for my proliant. Please, note that I have absolutely NO GUI available...just command line. any help would be greatly appreciated!
[http://h18000.www1.hp.com/products/quickspecs/10035_div/10035_div.HTML](http://h18000.www1.hp.com/products/quickspecs/10035_div/10035_div.HTML)

---

### Post by kimda on 2011-09-25
Can you ping archive.ubuntu.com? Are you behind a proxy? If you connect through a proxy you will have to make extra adjustments for apt-get to work.

---

### Post by leppel on 2011-09-25
Yup! i can ping archive.ubuntu.com, and i dont have any proxies. 

P.S.- I appreciate the quick response, and any suggestions would help!

---

### Post by kimda on 2011-09-25
You said that you run Ubuntu server version 9. Which one are you running? 09.04 or 09.10?

---

### Post by leppel on 2011-09-25
I believe 04. ridiculous question..how do you check? i catted the motd banner, did uname -a, and checked in /proc/version, and cant find it.

---

### Post by kimda on 2011-09-25
```
lsb_release  -a
```

or 

```
cat /etc/lsb-release
```

---

### Post by leppel on 2011-09-25
its jaunty 9.04

---

### Post by kimda on 2011-09-25
I think I know why you cannot download packages. If you run 09.04 its "end of line" since 2010-04-30. After a while they will remove certain releases that are eol from the server. Maybe there is a place where you can download packages but I would reinstall with 10.04 LTS instead. 

See releases:
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29)

I would install 10.04 LTS instead of this version. It will be supported until 2015 on servers. Next year there will be a new LTS server version.

---

### Post by leppel on 2011-09-25
sounds reasonable! Thank you!

---

### Post by leppel on 2011-09-25
My only concern is that I tried installing 10.10 alternative and just 10.10, and when the server boots, it shows the usual processor initializing, array controller initializing screen, and then after Compaq's "hit F10 for system utilities" screen, i'm not even prompted or shown the grub menu is loading, or anything like that. the screen just goes black, and a really small purple square flashes in the bottom-middle of the screen. 

--Any ideas of what to do in case this happens?

---

