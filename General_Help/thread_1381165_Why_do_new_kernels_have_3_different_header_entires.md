---
title: "Why do new kernels have 3 different header entires in GRUB?"
date: 2010-01-14
forum: General Help
---

### Post by Donalb on 2010-01-14
Guys, I'm sorry for asking this potentially very dumb question, but I tried multiple search terms here & on google, and couldn't find an answer.

So today 2.6.31.17 came. Thanks to the b1tch of a cat sleeping on the keyboard, I was forced to a restart before I wanted. (Not relevant).

Anyway why does each have have entries for :
linux-headers-2.6.31.17
linux-headers-2.6.31.17-generic
linux-headers-2.6.31.17-generic-pae

How do I know which one I should use from the choice of 3 for the current kernel (I just currently choose first on the list)?
And if I understand which one to use, can I delete the others from the same image?

And what's the recovery mode option?
Also, in start-up manager I have choice of 4 from the drop down list.  Why?

I understand about removing old kernels.  I just don't understand what I have left.

Sorry for the apparent idiocy.

Regards

---

### Post by awils1 on 2010-02-09
> How do I know which one I should use from the choice of 3 for the current kernel (I just currently choose first on the list)?
And if I understand which one to use, can I delete the others from the same image?

And what's the recovery mode option?
Also, in start-up manager I have choice of 4 from the drop down list.  Why?

I understand about removing old kernels.  I just don't understand what I have left.

Hi there :).

No, you're totally not an idiot - it's a worthwhile question!

Each new kernel revision adds an option to GRUB. If the newest is working for you, keep that, and you can ```
apt-get install purge
``` the rest. Sometimes a new kernel might break something on your PC (it's happened to me!), so it's advisable to keep the one previous to the latest around for a little while.

As for the generic options, it's my understanding that they boot and detect your processor specific kernel requirements. The specific kernels (i386, i686, Athlon, etc) are optimised for your computer.

Indeed, you can remove the generic option, but the only difference between the two types is a small speed increase if you use the optimised form.

---

### Post by lotharmat on 2010-02-09
and the pae one is to do with 32bit being able to address more than 3 gig of ram I believe

---

### Post by Donalb on 2010-02-09
Thanks guys. 

So since I have 4gb ram I should use PAE and delete the others?

But what are the recovery options then also?

I usually keep 3 kernels, just in case.

I wonder how many others are confused by the start-up options? It's not like there's a lot of easy to find info on it.

---

