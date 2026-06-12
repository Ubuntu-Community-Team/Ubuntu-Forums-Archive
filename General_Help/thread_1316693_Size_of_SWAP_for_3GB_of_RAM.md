---
title: "Size of SWAP for 3GB of RAM?"
date: 2009-11-06
forum: General Help
---

### Post by nitish_nit555 on 2009-11-06
Is the size of the swap should be twice of the RAM.

or it should be equal to the RAM.

Is there any problem if I do not create SWAP.

I have 3GB of RAM.....

---

### Post by P4man on 2009-11-06
If you never use more than 3GB its  fine to run without swap. Except you will not be able to hibernate. 

I rarely exceed 1 GB and only use more than 1GB  when running virtual machines. i dont think i ever needed swap and i got just 2gb ram, but your mileage may vary. 

OTOH ubuntu will not swap unless its really needed, so there is no harm or performance loss in defining swap. The only downside is a tiny bit of lost diskpace. 

Up to you to make the tradeoff based on your usage.

---

### Post by t0p on 2009-11-06
I've got 2GB of RAM on one computer and haven't bothered with swap.  I haven't experienced any problems.  But I don't hibernate.

---

### Post by shaon3343 on 2009-11-06
**I have 2GB of ram but I created 1.9GB of swap :p .My Ubuntu runs smoothly with this swap. Now I often notice that its not using swap at all ( except oneday when  it uses only 0.1% of swap).**

---

### Post by TenPlus1 on 2009-11-06
1.5Gb memory here and no swap partition, everything works great...

---

### Post by 3rdalbum on 2009-11-06
With that amount of RAM, you don't need swap at all, unless you really want to hibernate.

---

### Post by The Funkbomb on 2009-11-06
I'm gonna go against the crowd here and tell you to partition off a 2gb swap.

My machine has 8gb of ram (video editing, rendering etc) and it still uses swap, even if the physical memory isn't at capacity.  For example, right now I'm using 950mb of physical memory and 1.2mb of swap.

It's 2 gigs.  You'll hardly even miss it.

---

### Post by scoon on 2009-11-06
> **nitish_nit555 said:**
> Is the size of the swap should be twice of the RAM.

or it should be equal to the RAM.

Is there any problem if I do not create SWAP.

I have 3GB of RAM.....

Hey there, 

There probably isn't any problem if you don't create swap, but why worry about it.  It could be a bigger PITA if later down the road you find you need/want it.  There are lots of varied opinions out there on how much swap should be created.  It may not be a bad idea to set up at least 1G of swap so that if you need it, you have.  Since you have 3G's of ram, I bet you have even more HD space and could afford the the 1G loss.  On my machine, I have 1G of ram and 2G of swap.  I have 3/4T of space so the 2G for swap doesn't bother take anything from me.

Thanks.

---

### Post by P4man on 2009-11-06
> **The Funkbomb said:**
> 

My machine has 8gb of ram (video editing, rendering etc) and it still uses swap, even if the physical memory isn't at capacity.  For example, right now I'm using 950mb of physical memory and 1.2mb of swap.


You really think you'd suffer from eliminating the swap and using 1.2 Mb RAM extra :D ?

Ive seen ubuntu do that for unclear reasons those tiny amounts of swap but its really not a concern, neither performance wise nor becuase youd be running out of memory with 7GB unused RAM lol.

But like i said, it doesnt hurt either way

---

### Post by rajesh1136 on 2009-11-06
i use 2 GB RAM and 1 GB Swap. everything is fine for me.

---

### Post by nitish_nit555 on 2009-11-06
Thanks to all:popcorn:


So if i don't create the swap partition,the only loss will be that i can't be able to hibernate my PC :lolflag:

---

### Post by The Funkbomb on 2009-11-06
> **P4man said:**
> You really think you'd suffer from eliminating the swap and using 1.2 Mb RAM extra :D ?

Ive seen ubuntu do that for unclear reasons those tiny amounts of swap but its really not a concern, neither performance wise nor becuase youd be running out of memory with 7GB unused RAM lol.

But like i said, it doesnt hurt either way

Not likely :)

I don't think it matters either way either.  I'm more of a "be on the safe side" kind of guy.  It's 2gb.  Even most laptops ship with 160gb drives which is more than enough for most people.  I have a 750gb hard drive and even with Win7, Ubuntu, all my music and nonsense, I'm using less than 20% of my drive.  Pony up the 2gb for a decent swap just in case.

---

### Post by -=hazard=- on 2009-11-06
> **The Funkbomb said:**
> Not likely :)

I don't think it matters either way either.  I'm more of a "be on the safe side" kind of guy.  It's 2gb.  Even most laptops ship with 160gb drives which is more than enough for most people.  I have a 750gb hard drive and even with Win7, Ubuntu, all my music and nonsense, I'm using less than 20% of my drive.  Pony up the 2gb for a decent swap just in case.

I agree, just make a 2 gb swap partition, you don't loose anything :)

---

### Post by Nick Rhodes on 2009-11-06
> **P4man said:**
> You really think you'd suffer from eliminating the swap and using 1.2 Mb RAM extra :D ?

Ive seen ubuntu do that for unclear reasons those tiny amounts of swap but its really not a concern, neither performance wise nor becuase youd be running out of memory with 7GB unused RAM lol.

But like i said, it doesnt hurt either way

The reason it does it is that it is faster to page out unused virtual memory and allow the system to use spare memory for the file system cache - editing of large media files is where this is beneficial.

I will try and dig the link out, but I read about it a while ago, but it was explained by one of the Kernel devs.

Cheers, Nick

---

### Post by P4man on 2009-11-06
> **Nick Rhodes said:**
> The reason it does it is that it is faster to page out unused virtual memory and allow the system to use spare memory for the file system cache - editing of large media files is where this is beneficial.

I will try and dig the link out, but I read about it a while ago, but it was explained by one of the Kernel devs.

Cheers, Nick

Thats the general reason why some OSs are swappy. It can be argued in case you have iddle apps for a long time and you are short on RAM, Windows swaps all the time for this reason.  But in the above example with 7 GB unused RAM (or used as cache) those 1.2Mb swap is some kind of anomaly or weird side effect IMHO.

---

### Post by nitish_nit555 on 2009-11-06
I have found that I can later create a Swap file by 'dd' command.

So, if I need it, I can create a swap later.

thanks to all!

---

### Post by Nick Rhodes on 2009-11-06
You can tune how much swap is favoured by altering the swappiness setting.

Ubuntu default is 60 (out of 100).
A value of zero means when runnable memory gets low, the Kernel will only page out to swap when it has to and  prefer to reduce other things such as the file cache instead.
A value of 100  means the Kernel will swap prefer to swap out instead of reducing other things in memory.

I have never seen any evidence as to suggest how performance is affected by different settings in different scenario (only anecdotal comments) so leave it as default.

Here is a link for tuning it if you desire: [https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?](https://help.ubuntu.com/community/SwapFaq#What%20is%20swappiness%20and%20how%20do%20I%20change%20it?)

Edit: Found the link about Why to favour swap out instead of reducing cache: [http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

> 
My point is that decreasing the tendency of the kernel to swap stuff out is wrong. You really don't want hundreds of megabytes of BloatyApp's untouched memory floating about in the machine. Get it out on the disk, use the memory for something useful


Now, I'm not saying that its always best to have swappiness so high, but there are certain cases where having it high is best and certain cases where having it low (disc efficiency) is best and I personally believe somewhere in the middle, as Ubuntu is by default is a good compromise.

Cheers Nick

---

### Post by Kajoo on 2009-11-10
I got 1GB ram what size of swap i should set ? 1gb will be fine ?

---

### Post by Mighty_Joe on 2009-11-10
> **Kajoo said:**
> I got 1GB ram what size of swap i should set ? 1gb will be fine ?

As nearly everyone else in this topic has posted, it depends on what you use your computer for.  If you just do web browsing and OpenOffice documents, you'll probably be fine with none or 1GB.  If you are using Gimp to edit huge images, you'll probably need more.

---

### Post by kio_http on 2009-11-10
Your system will actually be slightly slower with swap on a system with so much RAM.

---

### Post by proxess on 2009-11-10
I've got 2GB and 3GB swap. I tend to fill up my ram quite easily (strangely enough) with the applications I usually use and the bunch of services I keep running (servers, desktop apps, I play with it all). I chose 3GB swap to hibernate and swap without any problem what so ever.

Also sometimes I tend to break applications and make my memory reach 100%, while doing things like encoding.

---

### Post by DocMindie on 2009-11-10
I've got 2GB RAM, I created an 8GB SWAP just in case.... my HD is about 500GB, so I won't miss the 8 for a LOOOOOONG while. Besides... although I'm not using anything extremely memory hungry right now, Maybe in 6 months, or 1 year... or 2 years.... I find that I needed the swap space after all.

For now though. I'm running World of Warcraft AND a virtual XP machine with 512MB (Gotta love virtual box, right? ;) ) and I don't even touch the swap space ;)

But as they say... "Better safe than sorry" ;)

---

