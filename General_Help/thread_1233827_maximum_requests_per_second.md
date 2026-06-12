---
title: "maximum requests per second"
date: 2009-08-07
forum: General Help
---

### Post by ryan1414 on 2009-08-07
Is there a maximum requests per second that ubuntu can handle? For example, a site like wikipedia gets at least 30,000 requests per second, so could ubuntu handle that many requests? Some people told me that ubuntu cannot and i would need to get a custom kernel.

---

### Post by SyL on 2009-08-07
> **ryan1414 said:**
> Is there a maximum requests per second that ubuntu can handle? For example, a site like wikipedia gets at least 30,000 requests per second, so could ubuntu handle that many requests? Some people told me that ubuntu cannot and i would need to get a custom kernel.


The answer is much more complex than your question.

You are asking about the amount of concurrent http requests a server can handle. It depends not only on the Operating System. Indeed the OS will be a significant variable but not the most important in my opinion!

You have to take into account:
- hardware
- cluster sizing --> behind wikipedia you have hundreds or even thousand of instances
- technology used for your Web Server --> Java will consume a lot of memory for instance
- and so on ...

So there is NO answer to your question!
Ubuntu could definitely handle 30 000 concurrent requests. It's only a question on how the cluster is configured. And it will be a huge cluster. This mean a important amount of different computers, running the same web server software, on an Ubuntu.

Now, if you look at what companies use, you won't find Ubuntu quite often. Rather SuSe, RedHat and Debian...

---

### Post by Johnny B on 2009-08-07
[Wikipedia adopts Ubuntu for its server infrastructure]("http://arstechnica.com/open-source/news/2008/10/wikipedia-adopts-ubuntu-for-its-server-infrastructure.ars")

---

### Post by 3rdalbum on 2009-08-07
> **ryan1414 said:**
> For example, a site like wikipedia gets at least 30,000 requests per second, so could ubuntu handle that many requests? 

Wikipedia runs on Ubuntu. But it's not like they use one single machine for it - they would have a load balancer that distributes the serving load across multiple machines.

---

### Post by SyL on 2009-08-07
> **3rdalbum said:**
> Wikipedia runs on Ubuntu. 


Wow, i did not know that ...
[http://www.ubuntu.com/products/casestudies/wikimedia](http://www.ubuntu.com/products/casestudies/wikimedia)



> **3rdalbum said:**
> But it's not like they use one single machine for it - they would have a load balancer that distributes the serving load across multiple machines.

[http://en.wikipedia.org/wiki/Cluster_%28computing%29](http://en.wikipedia.org/wiki/Cluster_%28computing%29)

---

