---
title: "Problem in ubuntu 9.04 with pidgin"
date: 2009-06-29
forum: General Help
---

### Post by abhi_69 on 2009-06-29
Hello,
i install ubuntu 9.04 few days ago. everything is ok except pidgin. its pidgin version 2.5.5 that comes with ubuntu 9.04. but, i want to use latest version, so, i enable lunchpad repo as described in pidgin official website for ubuntu users & install version 2.5.7. but, the problem is- i can't connect to my yahoo account using it. i use a proxy for connection which not support tunneling of several ports. so, i use 'no proxy' option in Advanced settings.
but, it still can't connect to yahoo account. it only show- connecting....dialouge, but, can't connect at all!
i had used the same settings for pidgin in ubuntu 8.10 & it worked well then. but, in 9.04, this settings is not working.
i look for a solution in pidgin website & try many methods they described there regarding yahoo account problem (by changing pager server address) but no one works for me.
whats the problem with pidgin in ubuntu 9.04? can anybody inform me.
for info- i also try the pidgin 2.5.5 that comes with ubuntu 9.04 & same problem happening.
now, i hav to use web based yahoo messenger (web.im) or [www.meebo.com](www.meebo.com) for chat which is annoying for me, becoz i have to open my browser window always.
is there any other chat client for me to use with yahoo ? i have no KDE, so i can't use kopete.
plz. anybody give me a solution. i love pidgin for chat. but, i can't use it for this problem.....i have no windows (actually, i don't like windows & always prefer linux) in my PC, so, i can't use yahoo messanger software.
any help for me?
thanz in advance.
Regards.

---

### Post by zero777zero on 2009-06-29
2.5.7 is working fine for me with yahoo. are you sure you installed it properly?

---

### Post by sirhalos on 2009-06-29
This has been explained before.

Go to the edit Yahoo account thing then you'll see a list of server things by the proxy section. The first ones says something like snc.yahoo.com or something close like that. Change it to start with cn. that should fix it.

---

### Post by abhi_69 on 2009-06-30
> **zero777zero said:**
> 2.5.7 is working fine for me with yahoo. are you sure you installed it properly? yes, i installed it properly. but, not working with yahoo

---

### Post by pbpersson on 2009-06-30
I had that problem on two Jaunty Jackalope machines, I fixed it using the instructions on [this web page]("http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues/")

Although, there was one little wrinkle.  I had to open the etc/apt/sources.list.d/pidgin-ppa.list file with gedit and change the line to the following:

```
deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu jaunty  main
```

because the word "jaunty" was missing

---

### Post by abhi_69 on 2009-06-30
thanz a lot!!!
it solve my pidgin problem. now, i can connect to yahoo with pidgin 2.5.7 well & enjoy chat.
Regards.

---

