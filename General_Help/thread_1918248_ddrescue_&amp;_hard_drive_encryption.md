---
title: "ddrescue &amp; hard drive encryption"
date: 2012-01-31
forum: General Help
---

### Post by directors on 2012-01-31
I was hoping someone here could maybe point me in the right direction? or right location for this post?

I was using ddrescue to clone a hard drive from a music server because it has one bad sector and I am afraid it will soon fail. I was successful in doing so, but the server seems to only like the original hard drive. Is there a work around for this? I'm only assuming the software does a check for the hard drive serial #? I have tried numerous clones and different hard drives (even the same exact brand and size), but it fails to boot all the way through. It knows it is a copied (or non authorized) hard drive and states to contact technical support. Unfortunately, the original software company is no longer in existence and another company wants a huge fee to license an new hard drive.

Is there anything I can do as a work-around?

---

### Post by seawolf167 on 2012-01-31
> **directors said:**
> Ioriginal software company is no longer in existence and another company wants a huge fee to license an new hard drive.?

This is a common issue with a lot of proprietary software (like Windows, Adobe, etc.), during software install it records hardware information, then if the hardware info changes on a subsequent run/install (for that license key), it deactivates itself. This is why Microsoft has [this page ]("http://support.microsoft.com/default.aspx/kb/950929/en=us")so you can activate your Windows install on a replacement hard drive.

So, unfortunately, you'll have to deal with the software developer :(

You can try [Clonezilla]("http://ubuntuforums.org/www.clonezilla.org"), but I doubt it'll resolve the issue.

---

### Post by directors on 2012-01-31
Thanks for the reply. I tried Clonezilla with the same result. That is why I think the software is confirming/checking for the hardware serial #'s. There has to be a way to change or trick something to make it work.

I wonder if there is software that can look at the original proprietary software to see where exactly it is checking for this information (search the code) so I can manually change it???

---

### Post by directors on 2012-01-31
Or maybe someone knows where to look for this in the proprietary files???

---

### Post by dcstar on 2012-02-01
> **directors said:**
> I was hoping someone here could maybe point me in the right direction? or right location for this post?

I was using ddrescue to clone a hard drive from a music server because it has one bad sector and I am afraid it will soon fail. I was successful in doing so, but the server seems to only like the original hard drive. Is there a work around for this? I'm only assuming the software does a check for the hard drive serial #? I have tried numerous clones and different hard drives (even the same exact brand and size), **but it fails to boot** all the way through. It knows it is a copied (or non authorized) hard drive and states to contact technical support. Unfortunately, the original software company is no longer in existence and another company wants a huge fee to license an new hard drive.

Is there anything I can do as a work-around?
[I][B]
"What"[/B][/I] fails to boot, Ubuntu does not bother with these things as I have cloned many Ubuntu partitions.

---

### Post by mips on 2012-02-01
What software are you referring to? We need details!

---

