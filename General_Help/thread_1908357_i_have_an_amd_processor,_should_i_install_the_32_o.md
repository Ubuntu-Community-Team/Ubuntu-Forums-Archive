---
title: "i have an amd processor, should i install the 32 or the 64 version?"
date: 2012-01-13
forum: General Help
---

### Post by tastro on 2012-01-13
i have an amd processor, should i install the 32 or the 64 version? and what are the benefits or what's the difference in this two versions of ubuntu?

my processor is: amd phenom ii x6 1090T

---

### Post by lukeiamyourfather on 2012-01-13
Use the 64-bit version. The differences between the two are the amount of memory applications can access (32-bit limited to 4GB) and what processing extensions can be used (like SSE4). The 64-bit version is better in every way assuming the processor supports it, which your's does.

---

### Post by howefield on 2012-01-13
Go for the 64 bit version.

Why not utilise the power in your machine ?

---

### Post by kc1di on 2012-01-13
> **tastro said:**
> i have an amd processor, should i install the 32 or the 64 version? and what are the benefits or what's the difference in this two versions of ubuntu?

my processor is: amd phenom ii x6 1090T

First thing you must determine is is your processor capable of 64 bit computing?

Next how much ram does your machine have?  32 bit version will run well on a 64 bit Machine but it will only see up to 3 Gigs of ram.  64 bit will address More ram , so if your system has more than 3 Gigs and you want to use it all , then 64 bit would be better.  (though there are ways to get a 32 bit install to recognize higher than 3 gigs of ram.)

I use the 64 bit on my machines that are able to run it. and it works fine for me. your mileage may vary :)

---

### Post by howefield on 2012-01-13
> **lukeiamyourfather said:**
> The differences between the two are the amount of memory applications can access (32-bit limited to 4GB)

These days the 32 bit installer will detect more than 4 gig and use the PAE kernel enabling all the installed memory to be used.

---

### Post by tastro on 2012-01-13
holy ****! that was fast :D thank you all for the fast replies.

ok then i think that i will go with the 64 bit version.

i have 4GB ram.

also that the only difference between 32 and 64 bit? that one supports only 3GB ram and the other one can handle more?

thank you again for helping me understand. ;)

---

### Post by howefield on 2012-01-13
> **tastro said:**
> also that the only difference between 32 and 64 bit?

To be honest, there are hundreds of threads in the forum on this subject that you can seek out and browse. Make sure and look for some of the recent ones.

Here are a couple of external links you can read also.. 

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

---

### Post by tastro on 2012-01-13
this link looks good: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

i already searched the help.ubuntu.com but didn't find this one. and when i searched the forums for this query: "32 or 64" i got 0 results. :S

thread closed. i think that now i know it all (or enough for me / i got my answer). :) thanks!

---

### Post by lukeiamyourfather on 2012-01-13
> **howefield said:**
> These days the 32 bit installer will detect more than 4 gig and use the PAE kernel enabling all the installed memory to be used.

Read the quote again, I said applications. Even if the kernel can see more memory the applications will still be limited to 4GB on a 32-bit operating system.

---

