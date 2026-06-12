---
title: "Please tell me how to filter certain sites"
date: 2009-12-13
forum: General Help
---

### Post by Nailox on 2009-12-13
I installed Dansguardian but then I can't start it - its not in the apps menu, alt+F2 doesn't work - i hit run and nothing happens. So how can I block some sites ?

---

### Post by StuartN on 2009-12-13
> **Nailox said:**
> I installed Dansguardian but then I can't start it - its not in the apps menu, alt+F2 doesn't work - i hit run and nothing happens. So how can I block some sites ?

There is a guide to DansGuardian on Ubuntu at [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008), but it seems to be configured by editing scripts. You might want to add an additional GUI frontend [http://ubuntuforums.org/showthread.php?t=237355](http://ubuntuforums.org/showthread.php?t=237355)

For simpler needs (e.g. just eliminating unwanting annoyances, rather than prohibiting access) you can add lines like **127.0.0.1	ad.doubleclick.net** to your /etc/hosts file, which would redirect this site to return nothing. There are some browser add-ins like adblocker that do the same with predefined lists.

---

### Post by Nailox on 2009-12-13
/etc/hosts turns out to be a read only file or Im wrong? this seems the easier option for me - i don't want to go tru all the hastle with the dansguardian .. Im out of patience lately

---

### Post by sliketymo on 2009-12-13
You have to edit it as root: sudo gedit etc/hosts, then save it ,close,or exit terminal.As a side note,I myself have also used the old MVP host files(after editing).Works to some extent.

---

### Post by Nailox on 2009-12-13
so where exactly i add the line? i tried under the line with mypcname but nothing.. so its gotta look like 127.0.0.1 [http://uglysite.com](http://uglysite.com) ?

> 127.0.0.1    localhost
127.0.1.1    my pc name


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

p.s. uglysite.com was a random example i didnt mean anythyng

---

### Post by StuartN on 2009-12-13
> **Nailox said:**
> so where exactly i add the line? i tried under the line with mypcname but nothing..

Lookups are cached, so you carry on seeing the site until the cache is refreshed. For sure the cache is refreshed the next time you reboot, and uglysite.com will be history then, but I have never been in enough of a hurry to find out how to force an immediate refresh.

---

### Post by Nailox on 2009-12-13
so the right way to do it is to add the line 127.0.0.1 [http://www.uglysite.com](http://www.uglysite.com) below the other lookups ? but 127.0.0.1 is the localhost so shouldnt the numbers for uglysite.com be different ? Im afraid it's not working even after the reboot..

---

### Post by t0p on 2009-12-13
I've never edited /etc/hosts.  But there is a manual page that tells you how to edit the file.

```
man hosts
```

---

### Post by StuartN on 2009-12-13
> **Nailox said:**
> so the right way to do it is to add the line 127.0.0.1 [http://www.uglysite.com](http://www.uglysite.com) below the other lookups ? but 127.0.0.1 is the localhost so shouldnt the numbers for uglysite.com be different ? Im afraid it's not working even after the reboot..

Sorry I did not notice, but you have included _http://_ and you should not. Each line is 127.0.0.1 followed by the site name, without a protocol and without any trailing folder/page:

```
127.0.0.1  www.uglysite.com
```

---

### Post by Nailox on 2009-12-14
yay it worked ! imho thats the proper way to teach newbies like me - show it like a code and let the newB copy it :)

---

### Post by StuartN on 2009-12-14
> **Nailox said:**
> yay it worked ! imho thats the proper way to teach newbies like me - show it like a code and let the newB copy it :)

Out of complete idleness on my part, do you know how to put the new /etc/hosts into force without rebooting?

Usually I just look at the source of sites that are annoying me, stuff some domains into the /etc/hosts and they are (hopefully) gone next time I boot up. It would be nice to edit/test/edit occasionally.

---

### Post by Nailox on 2009-12-14
what is edit/test/edit lol ? and why do u need to look the source of the page ? cant u just add a line like [www.bla.com](www.bla.com) ?

---

### Post by Boondoklife on 2009-12-14
Just for kicks, here is a list that I use on my router in conjunction with dnsmasq for filter out most of the crap online.

[http://pgl.yoyo.org/adservers/](http://pgl.yoyo.org/adservers/)

You can download a list in hostfile format too so you can just copy and paste. This is not a omnipotent list but gets almost everything. What it doesn't get you can add as stated above.

---

### Post by StuartN on 2009-12-14
> **Nailox said:**
> what is edit/test/edit lol ? and why do u need to look the source of the page ? cant u just add a line like [www.bla.com](www.bla.com) ?

That is fine if you know the source beforehand, but opening the source code (view->source in Firefox) and searching for any http:// that isn't the page you are viewing will find things that aren't immediately obvious.

For instance, [www.rte.ie/news](www.rte.ie/news) is an Irish news site. Obvious images appear at static.2mdn.net and m1.emea.2mdn.net, but there are also 6 calls to content from ad.ie.doubleclick.net and 2 calls to content from b.scorecardresearch.com.

---

### Post by Nailox on 2009-12-14
i see.. thanks boondoklife and stuartn

---

