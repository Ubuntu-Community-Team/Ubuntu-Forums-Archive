---
title: "installer encountered an error copying files"
date: 2009-08-18
forum: General Help
---

### Post by jiapei100 on 2009-08-18
It seems the following installation error has no standard solution yet.
Can anybody give me a hand please?

Rgds
JIA Pei


```
Installation Failed

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers+, to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.


```

---

### Post by slakkie on 2009-08-18
Check your CD. You can boot from CD and then do a check (see one of the options). If all goes well, then try again. If you still have the issue, could be your hard drive..

---

### Post by jiapei100 on 2009-08-18
Thanks for your prompt reply.

Checking now !!!

This seems to be a normal problem because I can google a lot of such topics, without a standard solution yet.

I'm wondering is there anything to do with the wrong device detection? Anyway, try checking first.

Thank you.

Rgds
JIA


> **slakkie said:**
> Check your CD. You can boot from CD and then do a check (see one of the options). If all goes well, then try again. If you still have the issue, could be your hard drive..

---

### Post by jiapei100 on 2009-08-18
Right !! Hehehehehe...

Check finished: errors found in 1 files !!!!

So, what to do? Redownload Ubuntu and rerecord it.
Cheers
JIA

---

### Post by nikhilk on 2009-08-18
> **jiapei100 said:**
> Right !! Hehehehehe...

Check finished: errors found in 1 files !!!!

So, what to do? Redownload Ubuntu and rerecord it.

Download again only if the image itself is corrupted. First check the md5sum of the downloaded iso image and verify it with the one on Ubuntu site.

If iso is OK just burn another CD at the *least* possible speed in your CD burner and you should be fine.

---

### Post by jiapei100 on 2009-08-18
Still the same.

Even I downloaded a fresh .iso, I still have 1 error files.

Is it possible that current 9.04 does contain 1 error file?

Rgds

---

### Post by HiImTye on 2009-08-18
try using 8.10 then upgrading

when youre done installing 8.10 go to a terminal (accessories > terminal) and type in the following:

```
sudo apt-get update
```

ubuntu updater should pop up after a little bit and tell you there is a new version available. click upgrade and it should be fine

hope this helps :)

---

### Post by slakkie on 2009-08-18
Download the minimal CD, and then you can do a netinstall.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then you don't get a nifty installer, but one that is very basic, but fetches all the packages from the web.. So less error prone.

---

### Post by jiapei100 on 2009-08-18
Thanks for your advice.
I downloaded a fresh Ubuntu 8.04, still the same.
It seems I'm using RW/CD, and Roxio to burn the image ISO. 
I can't control the burning speed, so that it's not well burned??

Even now, Ubuntu 8.04 contains
errors found in 1 files !

What can I do? My god...

Rgds

> **slakkie said:**
> Download the minimal CD, and then you can do a netinstall.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Then you don't get a nifty installer, but one that is very basic, but fetches all the packages from the web.. So less error prone.

---

### Post by nikhilk on 2009-08-18
> **jiapei100 said:**
> Thanks for your advice.
I downloaded a fresh Ubuntu 8.04, still the same.
It seems I'm using RW/CD, and Roxio to burn the image ISO. 
I can't control the burning speed, so that it's not well burned??

Could be either the burning software or the media.
You are burning the iso from Windows right? Try some other alternative burning software first like InfraRecorder. A list can be found [here]("http://en.wikipedia.org/wiki/List_of_optical_disc_authoring_software").

If burning through an alternate software at the lowest speed also doesn't work, try using a different media.

All the best!

---

