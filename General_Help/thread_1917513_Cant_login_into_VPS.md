---
title: "Cant login into VPS"
date: 2012-01-30
forum: General Help
---

### Post by davedavy on 2012-01-30
My host won't help me so this is my only option.

When i login into my VPS i see this:

[IMG]http://i41.tinypic.com/xpphs9.jpg[/IMG]

I can't enter any command's. But i can login into WinSCP  , does anybody know how i fix this?

---

### Post by jim_deadlock on 2012-01-30
I don't know the answer but the first thing you should always do in these situations is google your error message, in this case it produces loads of info:

[http://www.google.co.uk/search?aq=f&gcx=c&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=server+refused+to+allocate+pty#sclient=psy-ab&hl=en&client=ubuntu&channel=cs&source=hp&q=server+refused+to+allocate+pty&pbx=1&oq=server+refused+to+allocate+pty&aq=f&aqi=g-e2g1g-c1&aql=&gs_sm=e&gs_upl=192033l192033l1l195074l1l1l0l0l0l0l48l48l1l1l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a8cc55938fdce19c&biw=1210&bih=787]("http://www.google.co.uk/search?aq=f&gcx=c&sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=server+refused+to+allocate+pty#sclient=psy-ab&hl=en&client=ubuntu&channel=cs&source=hp&q=server+refused+to+allocate+pty&pbx=1&oq=server+refused+to+allocate+pty&aq=f&aqi=g-e2g1g-c1&aql=&gs_sm=e&gs_upl=192033l192033l1l195074l1l1l0l0l0l0l48l48l1l1l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a8cc55938fdce19c&biw=1210&bih=787")

This one looks promising:

[http://tektonic.net/forum/showthread.php?t=1296]("http://tektonic.net/forum/showthread.php?t=1296")

---

### Post by sj1410 on 2012-01-30
you can ask your service provider to run this command to solve this problem

/sbin/MAKEDEV pty
/sbin/MAKEDEV tty

---

