---
title: "Non networked pc and updates."
date: 2009-08-08
forum: General Help
---

### Post by nbo10 on 2009-08-08
Hi all,
If I have a system that I can't connect to the internet how would I install system updates? Thanks

---

### Post by rudihawk on 2009-08-08
Everything downloaded by apt including the updates that have been downloaded are kept in ```
 /var/cache/apt/archives/ 
```

So you can copy the updates from there, to a directory on the new PC and run:

```
sudo dpkg -i *.deb
``` - if you want to install all the packages in your new directory. 

Hope this helps.

---

### Post by tommcd on 2009-08-08
You may also want to try APT on CD:
> 
APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you've downloaded via APT-GET or APTITUDE, creating a removable repository that you can use on other computers.

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by CatKiller on 2009-08-08
One thing to consider is that Ubuntu only provides security updates, not feature updates, between releases. Since this computer isn't connected to the Internet, the need for security updates is lessened considerably.

---

### Post by rudihawk on 2009-08-08
> **CatKiller said:**
> One thing to consider is that Ubuntu only provides security updates, not feature updates, between releases. Since this computer isn't connected to the Internet, the need for security updates is lessened considerably.

That is true, but its always a good idea to have your OS as up to date as possible :D

---

### Post by elliotn on 2009-08-08
I always have problem restoring archievs with aptoncd

---

### Post by rudihawk on 2009-08-08
> **elliotn said:**
> I always have problem restoring archievs with aptoncd

I've used AptOnCD and it always seems to make things far more complicated than it should be. Although I haven't had a major train smash with it yet.

---

### Post by CatKiller on 2009-08-08
> **rudihawk said:**
> That is true, but its always a good idea to have your OS as up to date as possible :D

I don't think that that is true in general.

Updates change the behaviour of some program from State A to State B. State B is only *better* than State A if the behaviour of State A is undesirable in some fashion and the behaviour of State B is more desirable. This isn't always the case. State B may introduce a different undesirable behaviour (new bug) or break something that used to work (regression). If State B patches a security problem *that you are vulnerable to* then State B is clearly desirable. If State B patches a security problem *that you are not vulnerable to* then it's a wash, and you might as well not bother changing state. If State B patches a security problem *that you are not vulnerable to* and has bugs then State A is clearly desirable. If State B patches a security problem *that you are vulnerable to* **and** has bugs then you need to investigate further :) Whether something has bugs is something that can only be determined through extensive testing, and you can never establish for certain that a given piece of software *doesn't* have bugs.

Newer is not necessarily better.

How and when to install updates has been the topic of extensive debate since the second piece of software was written, and I doubt it will get resolved here :)

---

### Post by nbo10 on 2009-08-08
Thanks guy. I'll try aptoncd and the manual method.

---

### Post by rudihawk on 2009-08-09
> **CatKiller said:**
> I don't think that that is true in general.

Updates change the behaviour of some program from State A to State B. State B is only *better* than State A if the behaviour of State A is undesirable in some fashion and the behaviour of State B is more desirable. This isn't always the case. State B may introduce a different undesirable behaviour (new bug) or break something that used to work (regression). If State B patches a security problem *that you are vulnerable to* then State B is clearly desirable. If State B patches a security problem *that you are not vulnerable to* then it's a wash, and you might as well not bother changing state. If State B patches a security problem *that you are not vulnerable to* and has bugs then State A is clearly desirable. If State B patches a security problem *that you are vulnerable to* **and** has bugs then you need to investigate further :) Whether something has bugs is something that can only be determined through extensive testing, and you can never establish for certain that a given piece of software *doesn't* have bugs.

Newer is not necessarily better.

How and when to install updates has been the topic of extensive debate since the second piece of software was written, and I doubt it will get resolved here :)

All of that is true, but who has time to go an research every single update and have a look at possible bugs etc that might arise from installing it? :guitar:

---

### Post by CatKiller on 2009-08-09
> **rudihawk said:**
> All of that is true, but who has time to go an research every single update and have a look at possible bugs etc that might arise from installing it? 

IT admins that get paid to do it. The rest of us just have to do the best we can :)

---

