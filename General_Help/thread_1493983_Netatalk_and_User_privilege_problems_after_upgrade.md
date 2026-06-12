---
title: "Netatalk and User privilege problems after upgrade"
date: 2010-05-26
forum: General Help
---

### Post by blueyelabs on 2010-05-26
Hi All,

I just did quite a big apt-get upgrade and some weird things have started happening on my Sheeva Plug running debian squeeze (yes, I know these are Ubuntu Fora but hey =]).

Anyway, firstly, netatalk takes a _long_ time to log in and doesn't display any files when it has logged in (when I SSH in I can find the files with no problem).

The other strange problem is that I have a user called transmission to run the transmission daemon. The folder I was using to store torrents has everything chowned and -modded correctly but the transmission user simply can't read/write to that dir anymore. Weird no? Also, when I look at ps aux | grep transmission I see it running as user 1004 (which is the transmission user) but other processes display the user name. Also strange.

Maybe I should remove the transmission user and re-add it? How do I preserve the home dir? Any ideas with netatalk would be great, I get the following in the log:
```

getfd: connect localhost: Connection refused
tsock_getfd: no suitable network config from localhost:4700

```

Anyone?

---

### Post by nairboon on 2010-07-17
I got the same error after upgrading netatalk

this worked for me:
edit /etc/default/netatalk and change to
```
CNID_METAD_RUN=yes
```
and then restart netatalk
```
sudo /etc/init.d/netatalk restart
```

I also removed ~/.AppleDB but I don't know if thats necessary

---

### Post by blueyelabs on 2010-07-18
Thanks for that... I got it to work but I can't remember how now... after a couple of revert-upgrade-revert-upgrade cycles it started working... It was a serious pain though. If it happens again I'll use your method.

---

