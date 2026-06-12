---
title: "Opera 11 unbelievably slow"
date: 2010-12-25
forum: General Help
---

### Post by syrag on 2010-12-25
I installed Opera 11 a couple of days ago and it is incredibly slow. After entering a url it just sits there with "Document 0%" in the location bar for thirty seconds to a minute, then renders relatively fast. I've gone back to both version 9.xx and 10.63 and they are both faster.

Anyone else? Any ideas?

---

### Post by Frogs Hair on 2010-12-25
That is strange , I used 11 alpha , beta , and am now using the final release without any problem. I installed via the .deb package from the Opera site.

---

### Post by syrag on 2010-12-25
> **Frogs Hair said:**
> That is strange , I used 11 alpha , beta , and am now using the final release without any problem. I installed via the .deb package from the Opera site.

That's how I installed it, too. I'm now going through and removing widgets and add-ons one by one and trying it.

---

### Post by gandaran on 2010-12-25
> **syrag said:**
> I installed Opera 11 a couple of days ago and it is incredibly slow. After entering a url it just sits there with "Document 0%" in the location bar for thirty seconds to a minute, then renders relatively fast. I've gone back to both version 9.xx and 10.63 and they are both faster.

Anyone else? Any ideas?
opera 11 or any other opera version is fast only if you have a fast internet connection, google chrome/chromium works ten time faster with slow internet connections (under 1MG) at least this is my experience using both browsers, I don't buy the idea that opera is the fastest browser there is, it depends a lot on your internet.

---

### Post by veggen on 2010-12-25
Try a clean install. Remove Opera and all of it's configs and reinstall. Backup what you might still need, like contacts, feeds, bookmarks etc.
For the record, I updated from 10.x and it works normally...

---

### Post by syrag on 2010-12-26
Thanks for the replies.

"opera 11 or any other opera version is fast only if you have a fast internet connection"

I have a 6 megabit DSL connection. Opera 10 works normally.

"Try a clean install. Remove Opera and all of it's configs and reinstall."

Tried that, up to and including 'rm -rf .opera'. No help. Could this be a network config thing? I'm on Lucid, but don't know if ipv6 is enabled. How do I find out?


I originally moved away from firefox because flash (mainly on youtube) flickers so badly and I can't find a fix. This doesn't happen with opera.

---

### Post by otik on 2010-12-30
Same problem here. Ubuntu 10.10 64bit + Opera 64bit + slowneeeeeesss... My only guess is that can be IPv6 related problem.

---

### Post by syrag on 2011-01-01
> **otik said:**
> Same problem here. Ubuntu 10.10 64bit + Opera 64bit + slowneeeeeesss... My only guess is that can be IPv6 related problem.

I disabled ipv6 using the instructions found [here]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") (I had to edit sysctl.conf directly, as the command line didn't work) and reinstalled Opera 11. This seems to have fixed the problem.

---

### Post by scouser73 on 2011-01-01
Glad you've fixed the issue now, I've been using Opera 11 as my main browser for a few weeks now and it's extremely fast.

---

### Post by eragot on 2011-01-04
I have had to avoid any upgrades since 10.11 to avoid Opera just sitting there for a minute before loading a page. It is strange as it happens on both my computers one has 10.04 and the other is a clean install of 10.10 (as of a week ago). If I don't keep the Opera version down to the low 10.'s it isn't worth trying to use it.

How do I fix this?

Thanks

---

### Post by syrag on 2011-01-04
> **eragot said:**
> I have had to avoid any upgrades since 10.11 to avoid Opera just sitting there for a minute before loading a page. It is strange as it happens on both my computers one has 10.04 and the other is a clean install of 10.10 (as of a week ago). If I don't keep the Opera version down to the low 10.'s it isn't worth trying to use it.

How do I fix this?

Thanks

As Stated above this seems to an ipv6 problem. Run the following command in a terminal to determine if ipv6 is enabled or not:

```
cat /proc/sys/net/ipv6/conf/all/disable_ipv6
```

If this returns a 1, then ipv6 is already disabled, and your problem lies elsewhere. If it returns a 0 try the following:
Edit /etc/sysctl.conf and add the following lines:

```
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Reboot, and run the first command again to make sure it returns '1'.

Then install opera 11 and try it. This worked for me.

---

### Post by hg21 on 2011-01-24
There may be a problem with the opera version in tne ubuntu repositories

Opera was recently automatically updated on my PC via the repositories.  It was slow and imageless.  I have just reinstalled by 
sudo dpkg -i opera_11.00.1176_amd64.deb 
and it now works fine

---

