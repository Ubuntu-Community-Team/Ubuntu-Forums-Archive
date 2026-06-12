---
title: "Requires installation of untrusted packages"
date: 2009-11-11
forum: General Help
---

### Post by Atomic_kemo on 2009-11-11
Hi all!
I've been running karmic for a while now & it's really good, but suddenly Ubuntu Software Center gives me this error message whenever I try installing ANY app
```
Requires installation of untrusted packages
```I then have to use apt-get but I really want a solution because I like Ubuntu Software Center

Thanks:)

---

### Post by jbrown96 on 2009-11-11
What software repository did you add? You also need to add the key for that repository. The website that has the repository should have instructions for adding the key.

---

### Post by Atomic_kemo on 2009-11-11
Thanks I removed unused sources & it worked

---

### Post by iswan on 2009-12-07
Is that because I installed Ubuntu Tweak ? I have the same problem but I never change any configuration in software sources before...

---

### Post by jwm93k on 2010-10-07
I have the same problem. I am just trying to install items already in the software center and not anything else. I have not added or removed or changed any settings in my software center before this happened. I have used the Software center to download some games and Gimp when I first installed a few months ago. Now when I try to install something I get this error for any attempt. The post here don't explain what is going on, and what am I looking for to fix this.
Any Ideas?

---

### Post by jwm93k on 2010-10-10
Deleted: I was wrong. It did not work and all my systems have problems.

---

### Post by jwm93k on 2011-02-14
Hi, I have found out my previous post was totally in error and wrong. Please disregard or even delete it if you can. I still have the problem. I loaded Mint thinking I could get around it and I still have the problem. I'm thinking this issue my be related to the Update issues with "something wicked happen" messages from trying an update. I have made changes to my router and hosts file, and sources.list file, and selected and unselected sources in the Update GUI, and I have chosen different sites to Update or install from. It all fails. I have 4 Ubuntu and 2 Mint systems failing the same. These are mostly fresh vanilla loads with no changes that have problems updating or loading software. I found a few more things to try tonight, but so far this has been a very big headache. I can not help anyone else move or use Ubuntu when the update or software center does not work. It is a full halt to any progress in promoting Ubuntu. I hope the manual DNS change to my router's listed DNS paths or to Googles DNS 8.8.8.8 and 8.8.4.4 will work.  If not I am out of things to try and using the stinking windows again.

---

### Post by jwm93k on 2011-02-15
Hi, I don't know if anyone will read this but I have limited success. I did try the adding the outside DNS address to the resolv.conf file. "nameserver 8.8.8.8" I used the google DNS. I could have used my ISP DNS address just as well. Update would now work. It did complain about the "getdeb" addresses, but I found that is a different issue. I was able to use the GUI to Update my system, and load a game that I was unable to load before.
During my many searches I found may suggestions and ideas about what was wrong and what to do. 90% of those links were clueless, wrong, lost, and headed in the wrong direction. Last night I happened upon a place that recognized the issue and actually called it a bug. It seems these many related problems are caused by the apt-get not being able to resolve the host names. You can manually go to the locations but apt-get could not. Some think it may be a timing issue not waiting long enough, or routers that respond slowly. You can see in the /etc/resolv.conf usually has the router IP address as the nameserver. The router then forwards the request out to the listed ISP DNS server. This takes time. By putting the specific DNS in the resolv.conf file you are effectively bypassing the router's DNS processing. This seems to fix the problem. All this is theory because this did not use to be a problem and no one seems to know why this is becoming a problem. :D

---

