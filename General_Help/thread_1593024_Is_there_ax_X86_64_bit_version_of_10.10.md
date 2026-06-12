---
title: "Is there ax X86 64 bit version of 10.10"
date: 2010-10-11
forum: General Help
---

### Post by Scunnered on 2010-10-11
In the past I was informed that I should be using X86 64 bit for my system.  On looking into updating to 10.10 I only found the AMD 64 offering.  

Has the X86 64 bit been dropped and if so will the 64 bit offering be suitable for my use?

---

### Post by cascade9 on 2010-10-11
x86-64 is AMD64 (AMD got the 1st x86 64-bit instruction set out, so they named it).

---

### Post by Scunnered on 2010-10-11
Thanks for your reply.

Previously there was a separate X86 64 and AMD 64 listed for download which prompted the question.

Will give the 64 bit a go and see how things work

---

### Post by mastablasta on 2010-10-11
you must have confused it with i386 which is 32bit verison. i don't remember any X86 64 version.

---

### Post by cascade9 on 2010-10-11
> **Scunnered said:**
> Thanks for your reply.

Previously there was a separate X86 64 and AMD 64 listed for download which prompted the question.

I dont recall ever seeing x86-64 for any of the ubuntu .isos.

---

### Post by Vaphell on 2010-10-11
probably he used **uname -m** someday and he remembers wrong that it was on the iso :)

---

### Post by Scunnered on 2010-10-11
My thanks to each for all their contributions.

I am pleased to say that I was not under the afluence of incohol when I claimed that there was an X86 64 bit version.  On backtracting an old post I found that this was available in Karmic and Lucid.

Following the earlier details I applied Maverick to the web address and found this:-

[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

which confirms my that it is available.

I will download this and see how it works.

---

### Post by cascade9 on 2010-10-11
> **Scunnered said:**
>  On backtracting an old post I found that this was available in Karmic and Lucid.

If its from a post, somebody just used x86-64 instead of AMD64 (some distros use AMD64, some x86-64). 9.10 (karmic koala) and 10.04 (lycid lynx) have never had a x86-64 (naming), its always been AMD64 following the debian naming (and all the other versions of ubuntu with a 64-bit version AFAIK). 

[http://www.ubuntu.com/getubuntu/downloadmirrors#bt](http://www.ubuntu.com/getubuntu/downloadmirrors#bt)

[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by srs5694 on 2010-10-11
> **Scunnered said:**
> I am pleased to say that I was not under the afluence of incohol when I claimed that there was an X86 64 bit version.  On backtracting an old post I found that this was available in Karmic and Lucid.

Following the earlier details I applied Maverick to the web address and found this:-

[http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

which confirms my that it is available.

If you're saying that the page to which you've linked confirms the availability of a 64-bit x86 version, then please specify what text on that page confirms this in your mind, since I don't see it. The string "x86" occurs several times on that page, never associated with "64-bit."

In fact, strictly speaking, "x86 64-bit" is an oxymoron, since "x86" refers to the 80x86 architecture, which tops out at 32 bits. Only the x86-64 (aka AMD64 or EM64T) extension to the basix x86 architecture supports 64-bit operation.

One more comment: "x64" has developed as another synonym for x86-64. This usage is uncommon in Linux-land, though; it seems to be a Microsoftism.

---

### Post by Scunnered on 2010-10-11
I am well confused with the 64 bit position. 

I am told that my system should run the 64 bit ok but when I tried this earlier today as a live DVD it totally stalled when I clicked on the required button.

Downloaded the 32 bit only to find that the screen display does not work. Have posted this as a separate problem.

As far as I am concerned I will stick with Lucid for the moment until such time as things improve and someone can advise which version I should be using

---

