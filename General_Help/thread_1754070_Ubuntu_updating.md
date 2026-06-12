---
title: "Ubuntu updating"
date: 2011-05-09
forum: General Help
---

### Post by An Sanct on 2011-05-09
Hello all!

info: I am using Maverick 10.10, but other versions apply too.

I've noticed lately, that updates download one-by-one so one finishes, then the next one starts.

I have seen on new installs, that this is not always the case, a fresh Maverick will download multiple updates at a time.

So, where is the magical checkbox/setting for that?

---

### Post by Frogs Hair on 2011-05-09
I don't know  of a setting for this , but have noticed on a fresh installation  more than one update is downloading at a time . It could be the method of delivery is different. I was able to download icons at the same time the system updates were downloading ??

---

### Post by An Sanct on 2011-05-09
> **Frogs Hair said:**
> I don't know  of a setting for this , but have noticed on a fresh installation  more than one update is downloading at a time . It could be the method of delivery is different. I was able to download icons at the same time the system updates were downloading ??

I don't understand what you are saying :)

So here is my situation:

I have my home machine with multi-boot: Maverick (main)/Natty/Win7 and all three OSes also in VirtualBox.

When I update Maverick on my main machine, it does it in one single thread. 
When I update Maverick in my VM and have the same updates, it updates multi threaded (multiple simultaneous downloads)

I try to keep both machines as similar as possible, so I can test software in VM and then install it on my work machine if it is good or fall back to a snapshot if it is not good. So they should be almost identical.

PS. This might be about the "method of delivery" you mentioned.
My update server is '*[http://ftp.arnes.si/pub/mirrors/ubuntu](http://ftp.arnes.si/pub/mirrors/ubuntu)*' by default after installation, but if I run then selection for best server, it assigns the same server ('*[http://ftp.arnes.si/pub/mirrors/ubuntu](http://ftp.arnes.si/pub/mirrors/ubuntu)*') into the dropdown. After that, multithread downloading is disabled.
But if this is what is causing this behavior, then that is really strange...

---

