---
title: "Samba installed but won't run"
date: 2011-07-19
forum: General Help
---

### Post by evilbrent on 2011-07-19
I have a few computers that share files from this main Ubuntu desktop - I've been having samba problems so I've run 

> sudo aptitude purge samba

then re-installed it from the Software Centre. But it's not starting:

```

brent@Bertha:~$ sudo service samba start
samba: unrecognized service

```

Any ideas?

---

### Post by An Sanct on 2011-07-19
[Basic samba setup]("http://www.jonathanmoeller.com/screed/?p=1590") and [another more complicated sample]("http://shaileshagarwal1.wordpress.com/tag/samba/")

---

### Post by uvex8969 on 2011-07-19
Hi,

are you sure your installation success?

You may try this site: [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

Recently i install it, then i thought the samba is not working because i cannot access Windows file sharing from Ubuntu.

Until I completely configure everything then i can discover Windows Domain.

---

### Post by Morbius1 on 2011-07-19
> **evilbrent said:**
> ```

brent@Bertha:~$ sudo service samba start
samba: unrecognized service

```Any ideas?
Unless you are running Debian itself there is no "samba" service. Try this:
```
sudo service smbd start
```[COLOR=Blue]**EDIT:**[/COLOR] Ubuntu separated the "samba" service into it's original constituent parts: smbd and nmbd so to do the the equivalent "samba" start in Ubuntu you should also start nmbd:
```
 sudo service nmbd start
```

---

### Post by evilbrent on 2011-07-25
WIN!!!!!

Thanks guys!

Currently now playing Star Wars, Clone Wars, Episode 23, on my laptop, over the network from my desltop where I downloaded it!!

Excellent! I can now send my kids to bed to watch videos on Friday or Saturday night - yes yes, I know what sort of parent that makes me, but it keeps them in the damn room ;-)

I'm now expecting to be able to watch movies on my telly in exactly the same way!

hooray!!! life is complete and I can tell my wife that we don't need windows 7 after all!

---

