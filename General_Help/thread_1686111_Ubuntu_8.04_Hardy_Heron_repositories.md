---
title: "Ubuntu 8.04 Hardy Heron repositories"
date: 2011-02-11
forum: General Help
---

### Post by trasheddesk on 2011-02-11
Hi,

I would like to know if the Ubuntu 8.04 Hardy repositories are still there. I mean if I install Hardy on one of my computers, will I be able to install the software using Hardy repositories. Not updates but just installing the software. 

Also where can I get the human theme of 8.04. The human theme in the latest version is different and doesn't feel the same as the original.

Thanks.

---

### Post by snowpine on 2011-02-11
8.04 Hardy will be supported until April 2011 for desktops and April 2013 for servers. So yes, the repositories are still there.

[http://packages.ubuntu.com/hardy/human-theme](http://packages.ubuntu.com/hardy/human-theme)

---

### Post by Old *ix Geek on 2011-02-11
Just curious, but why are you sticking with such an old version?

(I'm doing the same thing, just with a different version! I'm sticking with 9.10 because I didn't like 10.04 when I upgraded to it on one computer last year. Reverted back to 9.10 and have no plans--as of this moment!--to upgrade to anything else.)

---

### Post by trasheddesk on 2011-02-12
> **Old *ix Geek said:**
> Just curious, but why are you sticking with such an old version?

I just liked it better than the latest version. Looks like the software is no longer being updated. But still I reverted back to the older version. 

I wonder why the kernel is also not updated. Software I understand but even the kernel updates stopped at 2.6.28.

---

### Post by snowpine on 2011-02-12
> **trasheddesk said:**
> I just liked it better than the latest version. Looks like the software is no longer being updated. But still I reverted back to the older version. 

I wonder why the kernel is also not updated. Software I understand but even the kernel updates stopped at 2.6.28.

The release number "8.04" indicates April 2008, therefore Hardy uses the stable kernel as of that date. Actually it should be 2.6.24 rather than 2.6.28. :)

---

### Post by Bucky Ball on 2011-02-12
> **Old *ix Geek said:**
> Just curious, but why are you sticking with such an old version?

Not old version. Still supported and current, if only for two more months. But about now is the time to update to the new LTS release, 10.04 LTS.

People who use LTS releases usually do so for a reason (particularly the server version, in the case of 8.04 LTS supported til April 2013) and stick with them until end of life. Relevant to production machines or any machines which need to stay up, reliable, and stable. ;)

---

### Post by jerrrys on 2011-02-12
hay, just gave up my last copy of 8o4.  it was hard to give up

---

### Post by trasheddesk on 2011-02-12
> **snowpine said:**
> The release number "8.04" indicates April 2008, therefore Hardy uses the stable kernel as of that date. Actually it should be 2.6.24 rather than 2.6.28. :)

I meant the kernel version in the hardy repositories. I just now updated the kernel using the repositories and the uname -a shows
2.6.24-28-generic, so I just quoted it in the previous post.

---

### Post by Bucky Ball on 2011-02-12
> **jerrrys said:**
> hay, just gave up my last copy of 8o4.  it was hard to give up

Know what you mean. I've recently done all four of our machines. Easy enough; hit the 'upgrade to 10.04 LTS' option in Update Manager and things are pretty much the same re. settings so not that much different. Some things are much better (noticeably bootup/shutdown times). ;)

---

### Post by snowpine on 2011-02-12
> **trasheddesk said:**
> I meant the kernel version in the hardy repositories. I just now updated the kernel using the repositories and the uname -a shows
2.6.24-28-generic, so I just quoted it in the previous post.

Gotcha, that makes sense. 2.6.24 is the kernel, and the "-28" refers to the various security patches Canonical has made since the release in April 2008, as you can see from the Changelog: [http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_2.6.24.28.30/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-meta/linux-meta_2.6.24.28.30/changelog)

---

### Post by davesmith on 2011-05-02
hi Snowpine

I use 8.04LTS because I cannot upgrade to 10.04. I have a fairly old Toshiba Satellite A30 and everything works with hardy - my cd/dvd rewriter, audio and video (with acceleration) display etc.

I have tried for a month now to upgrade to 10.04 without success. It will not load on a live cd but black screens halfway through - i think its a graphics issue, i get a set of coloured squares like big pixels after the purple screen and it dies. It does the same on the re-boot after upgrade via update manager

So I have a problem, what to do after LTS finishes shortly? Do you have any ideas on what I can do to solve this and achieve a successfull upgrade?

Thanks

---

### Post by snowpine on 2011-05-02
> **davesmith said:**
> hi Snowpine

I use 8.04LTS because I cannot upgrade to 10.04. I have a fairly old Toshiba Satellite A30 and everything works with hardy - my cd/dvd rewriter, audio and video (with acceleration) display etc.

I have tried for a month now to upgrade to 10.04 without success. It will not load on a live cd but black screens halfway through - i think its a graphics issue, i get a set of coloured squares like big pixels after the purple screen and it dies. It does the same on the re-boot after upgrade via update manager

So I have a problem, what to do after LTS finishes shortly? Do you have any ideas on what I can do to solve this and achieve a successfull upgrade?

Thanks

I suggest figuring out which graphics card you have using the terminal command:

```
lspci | grep 'VGA'
```

Then use the forum Search feature to find existing support threads related to your specific hardware. Another good resource is the [Ubuntu Wiki]("http://wiki.ubuntu.com").

---

