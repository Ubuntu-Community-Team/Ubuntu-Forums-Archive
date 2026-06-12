---
title: "&quot;find&quot; command and linux cache"
date: 2011-07-18
forum: General Help
---

### Post by masamunedark on 2011-07-18
Hello everyone.

I've noticed that subsequent runs of the "find" command are way faster than the first run, I believe this is due to the great caching performed by the kernel.

So, I was wondering if there is a way to make commands such as find run faster ( by utilizing cache ), everytime they are run ( even the first time ).

Ofcourse I know that this can't be done for free, but is it possible for example to let the kernel cache stuff automatically ( without me running "find" or any other command ), maybe by running commands in the background when there are free system resources or when the system is idle. 

Thanks guys, and any feedback would be appreciated. ( please excuse my poor English ).

---

### Post by psusi on 2011-07-18
The kernel does cache stuff automatically.  The whole point of a cache is that it keeps recently accessed data in ram so that it can be used again quickly in the future.  That precludes having it there before it is accessed for the first time.

---

### Post by jerrrys on 2011-07-19
another way to speed things up is "readahead"

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=readahead&sa=Search&cof=FORID:9#911](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=readahead&sa=Search&cof=FORID:9#911)

---

### Post by masamunedark on 2011-07-22
Thanks for the replies guys, and sorry for my late reply.

> **psusi said:**
> The kernel does cache stuff automatically.  The whole point of a cache is that it keeps recently accessed data in ram so that it can be used again quickly in the future.  That precludes having it there before it is accessed for the first time.

Yes, I understand that the data needs to be accessed first before it's cached.

What I am mainly talking about is the "find" command. for example when I run "find / ", this leads to caching my entire directory info ( I think ), and leads to faster results in the future. However, the first run would be slow, so I thought about adding a cron job to start " find / " at boot time and every now and then, this gives me impressive results whenever I try looking for some files, since the directory info is already cached. 

So, I am wondering if there's a better a better approach to what I am trying to do.

---

### Post by WorMzy on 2011-07-22
Use locate. It's faster than find, but not as thorough.

---

### Post by masamunedark on 2011-07-22
> **WorMzy said:**
> Use locate. It's faster than find, but not as thorough.

Thanks, I will look into it. :P

But, I am wondering if the way I am trying to force caching is ideal ? :confused:

---

