---
title: "Swapfiles on hard drives Vs USB flash"
date: 2011-05-22
forum: General Help
---

### Post by Nerotriple6 on 2011-05-22
So once more am I attempting a shot with Swapboost.

I inserted my practically free 2GB USB flash drive unmounted my two swap partitions and mounted the USB as swap with the Swapboost script.

It is working well. However as I already was running two swap partitions on two separate IDE channels I'm not sure if I'm actually gaining something with this.

Logic says that least I should have increased I/O performance from my drives since I am sparing them from swapping, right?

I will make some experiments later today to see how this affects file transfer speed over my IDE channels and my USB ports (I have in the past noticed a decrease in USB performance with this enabled).

But for now, Swapboost is working nicely.

```
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	976892	0	-2
/dev/sdb1                               partition	1855500	0	-3
/media/DOOM_2GB/swap                    file		1946964	176432	-1
```
Yes I know it's more swap than I need :tongue:
Buuut.. if I made the swap areas smaller and it would use all of them would it then lead to performance boost?

I am running on small amounts of RAM and some applications I use are very RAM hungry. Mobo only supports 1GB which I'm running on and because of this I put in a video card with 1GB worth of VRAM to save the RAM as much as possible.

---

### Post by dcstar on 2011-05-23
> **Nerotriple6 said:**
> So once more am I attempting a shot with Swapboost.

I inserted my practically free 2GB USB flash drive unmounted my two swap partitions and mounted the USB as swap with the Swapboost script.

It is working well. However as I already was running two swap partitions on two separate IDE channels I'm not sure if I'm actually gaining something with this.

Logic says that least I should have increased I/O performance from my drives since I am sparing them from swapping, right?
..........

Any "increased I/O performance" gained from proper hard drives will be lost using the pathetic I/O performance that a USB flash drive will deliver.

This exercise is probably a total waste of time.

---

### Post by Nerotriple6 on 2011-05-23
Yes... probably.. and this is probably why this project appears to be abandoned and this **is** why I stopped using it in the past, and definitely what I noticed yesterday.. While a flash drive has no moving parts which makes it excellent for something like this ...USB performance is rubbish.. :(

---

### Post by jerome1232 on 2011-05-23
Isn't flash media's life determined by the number of writes? (ie writing swap to it frequently is likely to shorten the lifespan of a flash drive)

---

### Post by satanselbow on 2011-05-23
> **jerome1232 said:**
> Isn't flash media's life determined by the number of writes? (ie writing swap to it frequently is likely to shorten the lifespan of a flash drive)

Very true! It is an approximation not a definite whole number though ie your drive won't fail on exactly the billionth write...

Also - USB ports share bandwidth - so if you have a lot of activity across the flash drive you may see problems with other USB devices on the same hub ie mouse / keyboard / printer / scanner / wifi adaptor etc etc which would then translate to you the user as a slowdown rather than the expected speedboost.

---

### Post by Nerotriple6 on 2011-05-23
Yes. This is practically killing a flash drive, but a 2GB costs practically nothing and hard drives should degenerate with an active swap partition as well. I would rather use my cheap flash drives and have them broken than the data lost on my drives.. So if USB had faster transfer rates this would be a great idea IMO.

---

### Post by Nerotriple6 on 2011-05-23
> **satanselbow said:**
> Very true!

Also - USB ports share bandwidth - so if you have a lot of activity across the flash drive you may see problems with other USB devices on the same hub ie mouse / keyboard / printer / scanner / wifi adaptor etc etc which would then translate to you the user as a slowdown rather than the expected speedboost.

Also true. This is what I remember from my first try at this, I think I mentioned it in the OP. The mouse and etc got laggy.. USB ports should not use the same bus.. regardless of what they are used for... ](*,)

---

### Post by lithopsian on 2011-05-23
Lastly, in case you aren't convinced, swapping should be very low compared to other disk I/O.  If you are doing significant amounts of swapping then your performance will suffer whatever you do.  Significant means continuously writing and reading a lot to and from swap, not just slowly building up swapped pages which is how it ideally should work.  If you are just slowly accumulating a bunch of swapped pages, mostly written and not read back too often, then a hard drive works just fine.

---

### Post by Nerotriple6 on 2011-05-23
Yes, thanks. I am convinced, also I realized this.

Windows uses a larger amount of swap than Ubuntu. Where Ubuntu will utilize RAM and will operate faster than Windows the latter will in some (or many) cases use it's paging file.

...So..... I'm back at reminding myself to be patient and wait for Bulldozer. When Bulldozer gets here I will have 8 gigs worth of DDR3 RAM and no use for swap whatsoever..

---

