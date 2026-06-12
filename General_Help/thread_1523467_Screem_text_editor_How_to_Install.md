---
title: "Screem text editor: How to Install?"
date: 2010-07-03
forum: General Help
---

### Post by madmax.santana on 2010-07-03
I have just downloaded the [Screem]("http://www.screem.org/") text editor source from their website...

I tried to aptitude it first, but it wasn't available in the repos. So I thought maybe building from the script would be the solution. The problem is, this package doesn't build with the usual configure, make and make install commands.

Well ./configure works. It checks the system and dependencies. But after that... How would I install it? Does anyone have any idea???

There is an executable install-sh in the folder but when I run it, it says no file specified. Please help. Thank you.

---

### Post by gmargo on 2010-07-03
> **madmax.santana said:**
> The problem is, this package doesn't build with the usual configure, make and make install commands.

Yes it does.  Perhaps your 'configure' step is failing?  I had no probably configuring it, but it will not compile with at least some minor edits (on 10.04 Lucid).

---

### Post by madmax.santana on 2010-07-04
Configuration was OK... Problem is with make!

---

### Post by madmax.santana on 2010-07-05
Can I bump this once?

---

### Post by madmax.santana on 2010-07-06
Nobody there???

---

### Post by stoneage on 2010-07-06
[https://launchpad.net/ubuntu/lucid/+package/screem](https://launchpad.net/ubuntu/lucid/+package/screem)

---

### Post by madmax.santana on 2010-07-06
Thanks a lot stoneage!
But it seems that launchpad contains deprecated or deleted releases of screem. I am gonna stick to bluefish... :)

---

### Post by mbspringer1 on 2011-07-19
In file included from egg-recent-view.c:28:
egg-recent-view.h:33: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'egg_recent_view_get_type'
egg-recent-view.c:32: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'egg_recent_view_get_type'
egg-recent-view.c: In function 'egg_recent_view_get_model':
egg-recent-view.c:58: warning: implicit declaration of function 'egg_recent_view_get_type'
make[3]: *** [egg-recent-view.lo] Error 1
make[3]: Leaving directory `/home/screem-0.16.1/libegg/recent-files'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/screem-0.16.1/libegg'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/screem-0.16.1'
make: *** [all] Error 2
@-desktop:~/screem-0.16.1$ 

do i need a newer compiler/ linker?
or is this a bad pointer?  (to file /directory) bad path?

---

