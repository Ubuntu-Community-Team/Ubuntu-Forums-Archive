---
title: "Will a Ubuntu 12.04 beta update to the final automatically?"
date: 2012-04-24
forum: General Help
---

### Post by sbw87 on 2012-04-24
Hi there,

I've recently got a computer pre-installed with a beta of Ubuntu 12.04. Will this beta automatically update to the final, or do I have to re-install everything from scratch?

By "update" I mean the following: I don't just like the packages to be updated (with rests of the beta version remaining somewhere on the disk), but I'd like to have a system which is in no way different from the final.

Thanks!

---

### Post by techsupport on 2012-04-24
> **sbw87 said:**
> Hi there,

I've recently got a computer pre-installed with a beta of Ubuntu 12.04. Will this beta automatically update to the final, or do I have to re-install everything from scratch?

By "update" I mean the following: I don't just like the packages to be updated (with rests of the beta version remaining somewhere on the disk), but I'd like to have a system which is in no way different from the final.

Thanks!

Yes. No worries. :)

As long as you did a fresh install of Ubuntu 12.04 LTS Beta, you shouldn't have to worry.

You may want to check out the helpful guide here:

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by OrangeCrate on 2012-04-24
Edit:

Techsupport beat me to a reply. As he said, just keep updating and you will have the final.

---

### Post by sbw87 on 2012-04-24
Does the same apply to Alpha versions (just noticed I don't know 100% whether it was a beta or an alpha version)?
Is there any way I can check myself (e.g. configuration file) whether it's the final version or some early predecessor?

Thanks!

---

### Post by techsupport on 2012-04-24
> **sbw87 said:**
> Does the same apply to Alpha versions (just noticed I don't know 100% whether it was a beta or an alpha version)?
Is there any way I can check myself (e.g. configuration file) whether it's the final version or some early predecessor?

Thanks!

You know I usually stick with the Beta. I don't do Alpha testing on Ubuntu OS.  If you do, I would imagine it would be the same as if you installed a Beta. Right?

---

### Post by OrangeCrate on 2012-04-24
> **sbw87 said:**
> Does the same apply to Alpha versions (just noticed I don't know 100% whether it was a beta or an alpha version)?
Is there any way I can check myself (e.g. configuration file) whether it's the final version or some early predecessor?

Thanks!

I've been using the same install since Alpha 2. There is no way to check that I'm aware of.

---

### Post by PaulW2U on 2012-04-24
> **sbw87 said:**
> Does the same apply to Alpha versions (just noticed I don't know 100% whether it was a beta or an alpha version)?

An alpha or a beta is just a snapshot of development up to that point and formally released with a little more testing of the ISO.

The first line of your sources list will give you an indication as to when and what you installed.

```
cat /etc/apt/sources.list
```

---

### Post by sbw87 on 2012-04-24
The last few posts have confused me a bit actually.

So is Alpha + all updates = final, code-wise (all files)?

Thanks.

---

### Post by forrestcupp on 2012-04-24
Yes. Even if you installed the earliest possible version of 12.04, if you keep updating, you automatically have whatever version is available right now. So no matter when it was installed, if it's up to date, you have the Beta2 right now. And if you keep it up to date past the 26th, you will have the final release.

What he was saying is that Alphas and Betas are just a snapshot of where they are at that stage of development, and it is all constantly updated to the latest stage of development.

---

### Post by OrangeCrate on 2012-04-25
As forrestcupp noted, the alphas and the betas are just snapshots in the development of the release. Look in the right column in the following link as to what were the milestones, and what their dates were in the overall development of 12.04. It should be easy to understand now, that wherever you jumped in, if you simply keep updating, you will get to the final. Take some time to read through that page, and associated links, and you'll feel pretty comfortable with the development process associated with a new release.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)

---

