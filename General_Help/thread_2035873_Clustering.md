---
title: "Clustering"
date: 2012-07-31
forum: General Help
---

### Post by HeartM on 2012-07-31
I have three computers. One desktop and two netbooks. all I want to do is hook them together so I can play games without having to buy a new computer. I've heard of this thing called clustering, where the computers all work in tandem, and I'm pretty good at figuring things out, but all the instructions I find are way over my head. Even the simplest "how-to"s make my head hurt. Is someone able to give me instructions that are so simple, a ten year old can understand them? (I'm 21, but the simpler the instructions, the better.)

---

### Post by dbaile10 on 2012-07-31
I did my undergrad research on linux clusters. To put it simply,m this will not work. Clusters require an entirely separate field of software where the programmer has to know ahead of time that they are dealing with a networked cluster to truly take advantage of it. There are some softwares like mosix or open mosix that allow you to migrate forked processes but no game is going to be forking separate processes to handle computations. Further, with gaming, most of the heavy lifting is done on the gpu. 

I understand your sentiment, but the idea simply won't work. I could fire up crysis on blue gene and it wouldn't matter. The process would stick to one node because it wasn't programmed to take advantage of all of them. The game would actually run slower in that cluster than running it on my 10 year old laptop.

Thats the aerial view, I could explain further if you need.

---

### Post by Cheesemill on 2012-07-31
> **dbaile10 said:**
> I did my undergrad research on linux clusters. To put it simply,m this will not work. Clusters require an entirely separate field of software where the programmer has to know ahead of time that they are dealing with a networked cluster to truly take advantage of it. There are some softwares like mosix or open mosix that allow you to migrate forked processes but no game is going to be forking separate processes to handle computations. Further, with gaming, most of the heavy lifting is done on the gpu. 

I understand your sentiment, but the idea simply won't work. I could fire up crysis on blue gene and it wouldn't matter. The process would stick to one node because it wasn't programmed to take advantage of all of them. The game would actually run slower in that cluster than running it on my 10 year old laptop.

Thats the aerial view, I could explain further if you need.

A very big +1

The sort of software you want to run isn't designed to be used on a cluster, there is no way of getting the result you are trying to achieve.

---

### Post by Kirboosy on 2012-07-31
> **dbaile10 said:**
> I did my undergrad research on linux clusters. To put it simply,m this will not work...

+1

However if you have a database usage for clustering I would recommend using [Hadoop]("http://hadoop.apache.org/") to setup your cluster.

---

### Post by HeartM on 2012-07-31
Oh... I didn't know that... I guess this counts as "solved" then. Especially if doing so would give me the opposite result of what I want.

---

