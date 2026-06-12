---
title: "Upgrade or clean install.. which is better"
date: 2011-04-25
forum: General Help
---

### Post by andjarnic on 2011-04-25
i all,

I have 10.10 Desktop right now.. and was considering the 11.04 beta 2 upgrade. However, when 11.04 comes out.. first.. will I be able to update to 11.04 final from 11.04 beta (if so is that automatic.. or do I need to do clean install)? Second, will the 11.04 beta 2 upgrade.. as well as the 11.04 final release.. remove/replace old 10.10 stuff.. or is an upgrade going to leave a lot of stuff around and thus a clean install is the best way to go?

I have a lot of stuff.. bookmarks, tools, data, etc on my linux box.. and while I do have a 2nd drive that I can move stuff to, if the upgrade path is as clean (or almost as clean) as a clean install, I am fine with that. I recall from Windows upgrades, there is generally a lot of remnants left behind that can slow things down or just sit around taking up space for no good reason. So I want to avoid anything like that if possible.

Thanks

---

### Post by pctx on 2011-04-25
Most people say that clean install is the best way to go.  I know for me, I'm due for a repartitioning, new Windows install and such of which once 11.04 is released I'll be doing clean installs of both Windows 7 and 11.04.  

In order to do the updates to feature releases, I believe the command is:
gksudo "update-manager -c"

run sudo aptitude update and you should see the new files from canonical. 

If you're wanting to use a development release (IE 11.04 Beta) and want to upgrade your 10.10 to a Beta,
run the above with a "-d".  Once 11.04LTS proper comes out, just run the above with a "-c" and that 
will bump you up versions.

Obviously, make sure you have data backed up before messing around with that stuff.... speaking from experience.

Happy Ubuntuing! :)

---

### Post by KegHead on 2011-04-25
Hi!

I've always updated/upgraded..until the new release..then I do a fresh install.

Just me..I do a lot of adding and deleting packages...I think(uneducated guess) that some stuff is left behind.

KegHead

---

### Post by apochry on 2011-04-25
> **pctx said:**
> ...  Once 11.04LTS proper comes out, ...

Just a note... 11.04 is not LTS. The next LTS should be the 12.04 release.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by pctx on 2011-04-25
> **apochry said:**
> Just a note... 11.04 is not LTS. The next LTS should be the 12.04 release.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)
What the heck?  I thought it was the 10.04 de facto replacement?  That stinks.

---

### Post by wilee-nilee on 2011-04-25
I always fresh install, but I have like 4 OS's on the hd right now, and all the pertinent info I can't lose including full images of all the OS's individually are on a external hd.

Fresh installs are faster generally, but this depends on your level of customization, and the ability to remember what you did.

You can also save the install list for reinstall, post 2 references.
[http://ubuntuforums.org/showthread.php?t=1733570](http://ubuntuforums.org/showthread.php?t=1733570)

---

### Post by bodhi.zazen on 2011-04-25
As others have mentioned, most people do fresh installs, which is rather trivial if you have a separate /home or better a /data partition.

Personally I upgrade and have only had a few minor problems.

I have one laptop 8.04 -> 8.10 -> ... -> 10.10

Will try upgrading that to 11.04 in a month or so

---

### Post by nothing.halo on 2011-04-25
I have always installed the upgrades for the new release. I have not had many, if any issues from doing this. I was going to wait for the next LTS to come out. I have been very happy with 10.10.

---

### Post by leehach on 2011-04-25
The one thing I can say about clean install is that when I upgraded from 8.04 &#8594; 10.04, trying to preserve my /home partition did not really work. Much of the system panel remained in 8.04. I ended up mounting my 8.04 home as /old_home, and selectively copying some application settings to the new /home partition.

--Lee

---

### Post by andjarnic on 2011-04-25
Great replies all. So sounds like for the most part, upgrading is ok on Ubuntu. I usually prefer a clean install too. I don't mind reconfiguring things either, although I have a few things configured now that I'll have to figure out again. 

My other concern with moving to 11.04 in a few days when it comes out is how well the stuff I use works.. Java, VMWare, cisco vpn client, etc. As long as most things are solid, I am all for moving up.

I too thought each .04 release was an LTS. I've been with Ubuntu since the 8.x days and have been contemplating moving to CentOS just because a lot of the cloud services use CentOS, but from what I've read online Ubuntu is still a much better desktop/development OS, but CentOS is probably the better server OS.

Thanks all.

---

