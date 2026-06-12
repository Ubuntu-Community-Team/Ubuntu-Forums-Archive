---
title: "Partitioning a hard drive"
date: 2009-11-11
forum: General Help
---

### Post by gwvenus on 2009-11-11
Hi Everyone,
I've recently built an Ubuntu computer and it works great. My question is I've installed Ubuntu on the whole 500g hard drive. Is there any way to create separate partitions as in windows e.g. d,e,f etc. so when the time comes to reinstall all my data will still be safe on the other partitions? And I would only have to reinstall on the "c" partition?
I love the Ubuntu community, you guys are great!
Thanks,
Gary

---

### Post by whoop on 2009-11-11
Look here:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by gwvenus on 2009-11-12
Hi Whoop,
Thanks for the quick reply. Sounds very scary for a noobie like me!
Cheers,
Gary

---

### Post by Andreas1 on 2009-11-12
you don't have to mount the separate partition as /home if you don't want to. for example i have a separate partition mounted at /media/data, using /home only for settings, /media/data for my documents.

---

### Post by whoop on 2009-11-12
> **gwvenus said:**
> Hi Whoop,
Thanks for the quick reply. Sounds very scary for a noobie like me!
Cheers,
Gary

Does it sound scary to have a separate home, or does the tutorial intimidate you?

Having a separate home is not scary, allot of linux users do this (I am just one of them).
If the tutorial looks intimidating, there's not much I can do about that, but it even has screenshots ;). Maybe it is a little, I don't know.

You can also do what Andreas1 says, it's a easier than my suggestion.

---

### Post by gwvenus on 2009-11-14
Hi Whoop,
I have a spare computer so I jumped in, did a fresh install of 9.10 and followed your website to the letter. Of course I copied and pasted just to be on the safe side. I have a 200g hard drive so I split it in two. I would love to know how to create three partitions. It seemed to work perfectly, and I have two separate partitions. However, now when I start or reboot the computer I get the following error message:
"Could not update ICEauthority file /name/gort/.ICEauthority
I can hit o.k. and Ubuntu will load but now there are odd problems such as if I try to add an application to the panel or desktop that option is now greyed out. I tried a number of solutions posted on the forums but none of them fixed the problem.
Thank you for the cool website and the benefit of your knowledge and I'm sure this is just a bug that will be resolved sooner or later. Too bad Ubuntu dosen't have a program like Acronis Disk Director!
Thanks Again,
Gary

---

### Post by gwvenus on 2009-11-20
Hi Whoop,
I have just realized that I owe you an apology. I read your tutorial again and noticed that I missed the last part about how to fix my problem. I am going to try again this time paying more attention to your directions.
Thank You,
Gary

---

### Post by whoop on 2009-11-20
> **gwvenus said:**
> Hi Whoop,
I have just realized that I owe you an apology. I read your tutorial again and noticed that I missed the last part about how to fix my problem. I am going to try again this time paying more attention to your directions.
Thank You,
Gary

No problem, Looks like you don't have all the rights set correctly (yet).
Be sure not to copy and paste the solution of your problem directly out of the website as ".ICEauthority" is inside a user account and you most likely won't have a user account with the name "username". Looks like it's gort :D ? Also repeat the steps for every user on your machine, in case you have more than one user,

Taking a look at you comments a bit more closely I see a point of concern:
[QUOTE=gwvenus]
Could not update ICEauthority file /name/gort/.ICEauthority
[/quote]
I would expect something like:
> 
Could not update ICEauthority file /home/gort/.ICEauthority

Please take a look at that, could be that you did something wrong somewhere....

---

### Post by whoop on 2009-11-20
> **gwvenus said:**
> Hi Whoop,
 I would love to know how to create three partitions.
Gary

Well if you read the tutorial, not only copy and paste without thinking about what you are doing ;), you should be able to create three partitions.
You will probably want to do that with the partition editor (gparted), as it can create, delete, move and resize partitions.

---

