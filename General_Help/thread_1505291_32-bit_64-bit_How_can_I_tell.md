---
title: "32-bit? 64-bit? How can I tell?"
date: 2010-06-09
forum: General Help
---

### Post by 3-Ball on 2010-06-09
I have a Gateway system I bought from Best Buy. When I got it, it was running Vista Home Premium, 64-bit.

I downloaded Ubuntu, burned the image, installed from the new disk. Everything works fine. My question: How do I know if I'm running 32-bit or 64-bit Ubuntu? I checked SYSTEM>ABOUT UBUNTU and that tells me nothing.

Thanks in advance for the help. Anybody?

---

### Post by jocko on 2010-06-09
Run this command in a terminal:
```
uname -m
```
"x86_64" means you run 64 bit, "i386" means you run 32 bit.

---

### Post by clhsharky on 2010-06-09
3-Ball


Open terminal

Applications>Accessories>Terminal

```
uname -a
```


Sharky

---

### Post by 3-Ball on 2010-06-09
OK fellers, it's this way:

When I run "uname -m" I get "i686"

When I run "uname -a" I get "2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux"

I don't know what to make of that. Let me know what you think, please.

---

### Post by w0Rm210 on 2010-06-09
You're running a 64-bit symmetrical multi-processor kernel. But you could also be running a 32-bit OS on a 64-bit arcitecture but considering you ran uname -m and got i686 you're on a 64 bit system running a 64 bit OS, congrats :)

---

### Post by Yellow Pasque on 2010-06-09
> **w0Rm210 said:**
> You're running a 64-bit symmetrical multi-processor kernel. But you could also be running a 32-bit OS on a 64-bit arcitecture but considering you ran uname -m and got i686 you're on a 64 bit system running a 64 bit OS, congrats :)
Uh.. no. i686 is still 32-bit.

---

### Post by karthick87 on 2010-06-09
It means that you are running 32 bit kernel.

---

### Post by WorMzy on 2010-06-09
It's 32-bit with a [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension") kernel, which allows you to overcome the ~4GB memory limitation that 32-bit OS' have. You cannot run 64-bit applications, but you can make use of all your RAM.

Hope this cleared things up for you. :)

---

### Post by 3-Ball on 2010-06-09
Thanks, guys! I don't know how to decipher the Linux lingo but I guess from what you tell me that I'm running 32-bit.

I noticed when I installed Ubuntu that it didn't offer me a choice between 32- and 64-bit installations. I assumed, therefore, that the software would make the correct choice automatically. Of course, I was wrong. . . .

So the next logical question is: What did I do wrong and how can I get 64-bit Ubuntu running on my 64-bit system?

Thanks again! Suggestions?

---

### Post by philinux on 2010-06-09
> **3-Ball said:**
> Thanks, guys! I don't know how to decipher the Linux lingo but I guess from what you tell me that I'm running 32-bit.

I noticed when I installed Ubuntu that it didn't offer me a choice between 32- and 64-bit installations. I assumed, therefore, that the software would make the correct choice automatically. Of course, I was wrong. . . .

So the next logical question is: What did I do wrong and how can I get 64-bit Ubuntu running on my 64-bit system?

Thanks again! Suggestions?

You'll have to download the 64 bit iso or torrent and re-install.

---

### Post by jwbrase on 2010-06-09
> **3-Ball said:**
> Thanks, guys! I don't know how to decipher the Linux lingo but I guess from what you tell me that I'm running 32-bit.

I noticed when I installed Ubuntu that it didn't offer me a choice between 32- and 64-bit installations. I assumed, therefore, that the software would make the correct choice automatically. Of course, I was wrong. . . .

So the next logical question is: What did I do wrong and how can I get 64-bit Ubuntu running on my 64-bit system?

Thanks again! Suggestions?

You choose between 64 bit and 32 bit when you download it, not when you install it.

On the download page it gives a choice between 32 and 64 bit, though it says that 64 bit is "not recommended for daily desktop usage". I don't know why: It's probably just there so non-technical users don't try downloading 64-bit Ubuntu for a 32-bit system. (A 32 bit OS will run on a 64 bit system, but not vice versa).

---

### Post by 3-Ball on 2010-06-09
If I do this thing, will the install destroy my current data?

---

### Post by philinux on 2010-06-09
> **3-Ball said:**
> If I do this thing, will the install destroy my current data?

Yes unless /home is on it's own partition. If not then you would have to backup whatever is in your home or just the important stuff.

---

### Post by 3-Ball on 2010-06-09
Thanks, phillinux!

I'm glad I got curious and started checking this out. I don't yet have much invested in this present install, so there won't be much to backup. I'll just burn a few files onto a DVD and copy them into the new install.

So as far as I'm concerned, we done on this thread. You guys have been a big help, answered all of my questions, and didn't make fun of me. So I'll be back on a NEW thread as soon as I <snip> mess up that 64-bit install. :lolflag:
Thanks again, fellers!

3-Ball

---

