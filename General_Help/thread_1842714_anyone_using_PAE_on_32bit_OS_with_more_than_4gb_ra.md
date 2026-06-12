---
title: "anyone using PAE on 32bit OS with more than 4gb ram? need feedback"
date: 2011-09-12
forum: General Help
---

### Post by fuzzylogic25 on 2011-09-12
I am currently using Ubuntu 10.04 32bit with 4GB ram and about 8GB swap. I am constantly going over the 4gb limit, using about 2-4GB of swap. I need more memory so am wondering whether to get more ram and just run it through this PAE thing, because I do not have time to reinstall with a 64bit OS.

So anyone using it currently out there? I wanted to know what the performance was like, especially when you go past the 4GB limit.

---

### Post by 3rdalbum on 2011-09-12
That's definitely an option. Performance shouldn't be a drama, as PAE is done mainly through the CPU itself.

What are you doing that's using so much RAM?

---

### Post by fuzzylogic25 on 2011-09-12
well i have heaps of browsers (with heaps of tabs) running. Some are viewed daily, some weekly, others I will view them within a few weeks when i have time. I prefer this over just adding to bookmarks. i move the ones i wont need to view within the next week to one workspace, i have another workspace dedicated to sites related to linux/ubuntu stuff (so i can learn more!), another workspace related to my school work. and the last one is just the everyday websites i check.

really its just heaps of browsers..couple of lectures/tutorial videos running at once but on pause (i watch lil by lil), some pdf/text documents running...stuff like that.

does this seem crazy?? if there is a better way to manage this let me know! but i like to have all the stuff easily available. i also organize my browsers...one chrome browser might have uni work sites, another for linux.etc

---

### Post by ubudog on 2011-09-12
On [this]("http://usa.asus.com/Notebooks/Gaming_Powerhouse/G71Gx/#specifications") system, I'm using the PAE kernel with 6GB of ram, and it works great.

---

### Post by fuzzylogic25 on 2011-09-12
So you don't notice any slow down? I heard that once the OS starts accessing the ram region thats past 4GB, the performance is a little slower (according to the official ubuntu help section).

Also, how do I enable it? Do I just simply put in the 6Gb of ram and the OS will recognize it automatically?

---

### Post by ubudog on 2011-09-12
Well, I can't recognize any performance decreases, maybe because I've never ran 64-bit on this machine.

In my case, I had the 6GB in the laptop at install time, and it automatically installed the PAE kernel.

---

### Post by 3rdalbum on 2011-09-12
> **fuzzylogic25 said:**
> So you don't notice any slow down? I heard that once the OS starts accessing the ram region thats past 4GB, the performance is a little slower (according to the official ubuntu help section).

I don't believe it will be much slower. You probably won't notice it.

> Also, how do I enable it? Do I just simply put in the 6Gb of ram and the OS will recognize it automatically?

You just need to install the linux-generic-pae package and then from the next boot you'll be using the PAE kernel.

Your use case does sound a little crazy to me, but it's your computer. If you want to buy more RAM to run a hundred browser tabs, then go for it.

---

### Post by fuzzylogic25 on 2011-09-13
Well I guess the main comparisons we have here are:
1. 6GB on 64bit OS
2. 6GB on 32bit OS with PAE
3. 4GB on 32bit OS with plenty of swap to make up for the missing 2GB of ram

I guess it is obvious that 1 is better than 2 and 3. 2 Is better than 3. Thats all that really matters.

Currently I am suffering every time I use more than 4GB of memory as the OS starts to run my hard disk like crazy. It is moving stuff to the swap but wow it sure takes a lot of hard disk read/writes (i can literally hear it going insane!). Its worse when I have like 3.9GB of main memory used and already like 2GB of swap used. Then I load some application and this long crazy process of hard disk reads/writes go on. After that process I end up with like 2.8GB of main memory used and something like 3+GB of swap used.

6GB with PAE on 32bit should at least avoid this issue. So I will switch to that. Cannot be bothered going to 64bit yet.



> **3rdalbum said:**
> 
Your use case does sound a little crazy to me, but it's your computer. If you want to buy more RAM to run a hundred browser tabs, then go for it.

You are probably right haha. Basically It is structured as follows:

Workspace 1 - Daily things I always do like check email, watch some videos etc.

Workspace 2 - Lots of articles opened relating to my hobbies/interests along with some documents

Workspace 3 - Anything Linux related so I can learn more about it. Eg guides to using certain things like shell programming

Workspace 4 - Anything uni related.

When I am not working on uni stuff, I would like to not even see it. I find this separation a lot nicer and easier to manage than having it all on one workspace. I guess thats the whole reason why they have workspaces. But having to open/load something everytime I want to see it is a pain! 

If you can think of a better way, please let me know as I would definitely love to avoid the ram usage. But this is my way of utilizing plenty the large amounts of ram. I cant see how anyone else can utilize it unless they were playing games, doing some crazy graphics processing or running some software that requires Gigs of ram!

---

### Post by dcstar on 2011-09-15
> **3rdalbum said:**
> I don't believe it will be much slower. You probably won't notice it.


PAE is a workaround with it's own overheads when using more than 4GB of RAM.

To put it simply, no 32-bit OS (or app) can ever use more than 4GB of Address Space, PAE gets around this by basically splitting the available RAM into addressable 4GB sections and then allowing separate processes to run in each individual chunk.

Whenever data needs to be moved between the different chunks, that's when the extra overhead comes in because a 64-bit OS does not need to do this sort of thing as it is not restricted to the 4GB limit.

PAE gets less efficient as the RAM increases above 4GB, so a relatively trivial 2GB increase will probably have little overhead.

---

### Post by oldos2er on 2011-09-15
> **fuzzylogic25 said:**
> Well I guess the main comparisons we have here are:
1. 6GB on 64bit OS
2. 6GB on 32bit OS with PAE
3. 4GB on 32bit OS with plenty of swap to make up for the missing 2GB of ram

I guess it is obvious that 1 is better than 2 and 3. 2 Is better than 3. Thats all that really matters.

Currently I am suffering every time I use more than 4GB of memory as the OS starts to run my hard disk like crazy. It is moving stuff to the swap but wow it sure takes a lot of hard disk read/writes (i can literally hear it going insane!). 

Have you tried changing the default swappiness value? The default '60' is a bit high, in my opinion. Per [https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F) add the line **vm.swappiness=10** to the end of /etc/sysctl.conf then run **sudo sysctl -p** to test it.

---

