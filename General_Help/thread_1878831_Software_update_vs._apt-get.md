---
title: "Software update vs. apt-get"
date: 2011-11-10
forum: General Help
---

### Post by taylorkh on 2011-11-10
This is a strange one... I have Ubuntu 11.10 newly installed as a VMWare virtual machine. Software update tells me that there are a bunch of updates needed. So I click Install Updates and enter my password as prompted. I get and error about not being able to download updates, check Internet connection. The network/Internet connection is fine. The offending address is shown in the error detail > Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/i/indicator-session/indicator-session_0.3.7-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/i/indicator-session/indicator-session_0.3.7-0ubuntu1_amd64.deb) 404  Not Found [IP: 91.189.92.182 80]

So I closed the Software Update utility and opened a terminal. I issued the commands sudo apt-get update and sudo apt-get upgrade and the necessary packages were downloaded and installed. 

The question is... how can apt-get access the repositories when Software Update cannot???

Ken

---

### Post by redbook4574 on 2011-11-10
I can't answer ur question but I will say I always prefer a manual update.

---

### Post by missmoondog on 2012-01-14
just did a search for this ip address 91.189.92.182 and this was one of two results.

basically the same problem except i have a whole long list of repos that aren't being fetched.

hopefully, just a temporary issue as it was working fine last night.

---

### Post by 2F4U on 2012-01-14
> **taylorkh said:**
> The question is... how can apt-get access the repositories when Software Update cannot???

I guess part of the problem is that with Software Update you get at least one additional layer of software and this layer may be buggy. Thats why I prefer to use apt-get directly in a terminal.

---

### Post by Cheesemill on 2012-01-14
I don't think that your problem has anything to do with Software Update vs apt-get,

It just looks like there were network problems when you tried with Software Update which had resolved themselves by the time you tried apt-get.

Software update basically just calls apt-get commands with a GUI interface.

---

