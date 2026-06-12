---
title: "Surfing the net got weird..."
date: 2010-01-23
forum: General Help
---

### Post by AmirM on 2010-01-23
Hi,
I dont know if here is the right place to ask this or not but I hope you can answer me or guide me.
I have an Ubuntu and a windows XP installed on my computer.two days ago when I was on Ubuntu an was browsing the web suddenly I saw that I cant open some sites(i.e this forum),I taught it may be because of google chrome,but I had same problem with Firefox.taught it can be internet problem but it wasnt.
the detailed problem is:the browser doesnt open most of the pages,it stays on "waiting for www.example.com".its ok with google,blogger,some site/weblogs but for the rest I get that status.
to add:
1)its OK with the Windows.all pages are OK.
2)After trying to changing configuration and when that didnt solve the problem,I deleted the Ubuntu patition,and reinstalled Ubuntu,but the problem is remaining.
3)before uninstalling ubuntu I tried opening the pages with TOR and that worked,pages opened.but for reasons(its low speed and also after reinstalling ubuntu I cant download that!!)
4)I cant count ISP mainenance,he didnt even know what ubuntu is...
5)when I ping to the sites that dont open(using terminal,writing "ping example.com") it shows thats its ok,XXXms latency,no packet loss and so on.


I think the problem is from ISP,am I right?

---

### Post by c0mput3r_n3rD on 2010-01-23
> **AmirM said:**
> Hi,
I dont know if here is the right place to ask this or not but I hope you can answer me or guide me.
I have an Ubuntu and a windows XP installed on my computer.two days ago when I was on Ubuntu an was browsing the web suddenly I saw that I cant open some sites(i.e this forum),I taught it may be because of google chrome,but I had same problem with Firefox.taught it can be internet problem but it wasnt.
the detailed problem is:the browser doesnt open most of the pages,it stays on "waiting for www.example.com".its ok with google,blogger,some site/weblogs but for the rest I get that status.
to add:
1)its OK with the Windows.all pages are OK.
2)After trying to changing configuration and when that didnt solve the problem,I deleted the Ubuntu patition,and reinstalled Ubuntu,but the problem is remaining.
3)before uninstalling ubuntu I tried opening the pages with TOR and that worked,pages opened.but for reasons(its low speed and also after reinstalling ubuntu I cant download that!!)
4)I cant count ISP mainenance,he didnt even know what ubuntu is...


I think the problem is from ISP,am I right?

Some times I get problems like that with ubuntu and windows, and I just unplug my modem and router, wait a few seconds and reconnect them and it works.  See if that helps any.

---

### Post by AmirM on 2010-01-23
> **c0mput3r_n3rD said:**
> Some times I get problems like that with ubuntu and windows, and I just unplug my modem and router, wait a few seconds and reconnect them and it works.  See if that helps any.
it was the first thing I did.
I even reseted the modem(with reset hole) and...nothing.

---

### Post by fjf314 on 2010-01-23
When you are in Ubuntu, what happens when you run a traceroute to a site that you can't reach from your web browser? You may need to install traceroute first.

```
sudo apt-get install traceroute
```

After that, run a traceroute on these forums since you can't reach them.

```
traceroute ubuntuforums.org
```

Does it eventually get hung up somewhere? Or does it fail to resolve the site with DNS and give you a "Name or service not known error" right away?

---

### Post by AmirM on 2010-01-24
> **fjf314 said:**
> When you are in Ubuntu, what happens when you run a traceroute to a site that you can't reach from your web browser? You may need to install traceroute first.

```
sudo apt-get install traceroute
```After that, run a traceroute on these forums since you can't reach them.

```
traceroute ubuntuforums.org
```Does it eventually get hung up somewhere? Or does it fail to resolve the site with DNS and give you a "Name or service not known error" right away?

Here's the result:
```

amir@Desktop:~$ sudo apt-get install traceroute
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package traceroute is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package traceroute has no installation candidate
amir@Desktop:~$ 

```

to mention that due to internet problem that I said,I cant update the ubuntu or install anything.

---

### Post by mikewhatever on 2010-02-04
Just for reference, and for whoever might read this later, the command to use is 'tracepath' and not 'tracerout'. It's pre-installed.

---

