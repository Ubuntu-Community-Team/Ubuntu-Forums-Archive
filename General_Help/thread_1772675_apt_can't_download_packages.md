---
title: "apt can't download packages?"
date: 2011-05-31
forum: General Help
---

### Post by enimeizoo on 2011-05-31
Hello,
I don't know where it can come from, but apt won't download any package. Here is the error I get (after a few minutes) :
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  plasma-widget-lancelot
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 504 kB of archives.
After this operation, 1,942 kB of additional disk space will be used.
Get:1 http://mq.archive.ubuntu.com/ubuntu/ natty/main plasma-widget-lancelot amd64 4:4.6.2-0ubuntu3 [504 kB]
Err http://mq.archive.ubuntu.com/ubuntu/ natty/main plasma-widget-lancelot amd64 4:4.6.2-0ubuntu3                            
  Connection failed [IP: 91.189.92.170 80]
Failed to fetch http://mq.archive.ubuntu.com/ubuntu/pool/main/k/kdeplasma-addons/plasma-widget-lancelot_4.6.2-0ubuntu3_amd64.deb  Connection failed [IP: 91.189.92.170 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```I have no clue where it can come from, since every other application that needs Internet works fine. I can ping the indicated address, so that is not a routing issue (I guess). 

I believe it uses http, so that is not a protocol blocked by the ISP.

And it is not automatic : last time I was about to report it here, the bug disappeared (and I didn't report because I thought it could have been fixed somehow, and I couldn't get the error message)

And wired connection works fine, too.  

Actually, I just download the package from the address in the log via firefox. I really have no clue, since it is a pretty fresh install (no more than two weeks)

The only thing I can think of would be some bug in apt.  I googled for an apt bug, and I saw that apt's http method 'doesn't handle redirects', but that was in 2005. Besides, I wouldn't be the only one to have this problem, and that doesn't explain why it works with a wired connection.

 If anyone have an idea about what is going on, it would help a lot.

(edit) It works right now... I didn't do anything but writing this post. It really looks random. What can I do when it happens to find out where it comes from?

---

### Post by searchfgold6789 on 2011-05-31
Have you *tried* apt-get update???

---

### Post by enimeizoo on 2011-05-31
Actually, that was more of a brain bug than an apt bug... Embarrassing. 
Thank you anyways, I don't know how long it could have taken to realize that. ](*,)

---

