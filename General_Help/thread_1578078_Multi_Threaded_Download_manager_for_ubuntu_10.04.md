---
title: "Multi Threaded Download manager for ubuntu 10.04"
date: 2010-09-19
forum: General Help
---

### Post by Vivekananda_kukkapalli on 2010-09-19
I use Ubuntu 10.04.
I want to have a download manager which can integrate into Firefox(Just like IDM). What would be the option? 

PS: I m a new user, pl come from the beginning.

---

### Post by arifeen on 2011-01-21
I was looking for the same. But no one seemed to reply your question :(

---

### Post by Amente on 2011-01-21
axel is a small download manager which you can install from the repositories by running the command
```

sudo apt-get install axel

```

after the installation is finished all you have to do is run this code
```

axel -n (Number of connections) (your download link)

```
for example
```

axel -n 256 http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10382479

```
will download this page.
axel cannot download a youtube video for you and is not integrated with firefox,but since you can choose the number of connections you can download faster.idm uses 16 connections maximum. axel can 256.

---

### Post by mastablasta on 2011-01-21
there are plenty firefox estensions that will do the downloading... For example add on "downloadthemall"
 
[https://addons.mozilla.org/en-US/firefox/tag/download%20manager]("https://addons.mozilla.org/en-US/firefox/tag/download%20manager")

---

