---
title: "4gb ram but only 3.2Gb with PAE or 64bit, intel i945PM chipset"
date: 2010-06-24
forum: General Help
---

### Post by 987a654 on 2010-06-24
Could people with Chipset : Intel i945PM confirm whether they can use 4Gb ram. I came across lot of posts that their sys will not go beyond 3.2Gb even when they use PAE enabled kernel or 64bit OS.  I have this chipset and 4Gb ram and does not matter what I use it will not show more than 3.2Gb.  I know that lot of 1st gen netbooks used the same chipset. 

 I read on some forums that it's a chipset limitation, but intel documents do not say this instead they say that it should support up to 4Gb. 

I just want to get a consensus.

Thankyou
Yudi

---

### Post by CharlesA on 2010-06-24
It's probably memory that is hard allocated to video. It's got integrated video, after all.

---

### Post by 987a654 on 2010-06-24
it's got dedicated nvidia gforce go 7400 64mb ram, I think it grabs another 64mb from system ram.

yudi

p.s look at this link, quite a few people have this problem.
[http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/#comment-48049](http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/#comment-48049)

---

### Post by JoelOl75 on 2010-06-24
I have the same chipset in my notebook and like you it won't access the full 4gb of memory.  Seems normal as the bios doesn't report all 4gb either and yes, I'm using a seperate Nvidia Quadro FX3500 card so the gfx arn't using any memory.

Chipset limitation.

---

### Post by 987a654 on 2010-06-25
there is a small difference between yours n my sys. System BIOS sees 4Gb as installed memory but says it only 3.2GB can be used because of allocating the rest for the sys use.

yudi.

p.s 
Thanks for posting.

---

### Post by gacanuck on 2010-08-10
I am also using a laptop with similar specs:
 [LIST]
[*]Toshiba Techra M5
[*] I945GM chipset
[*] Intel 945GM Chipset integrated video
[*] 4GB memory installed
[*] Ubuntu 9.10 w/2.6.31-22-generic-pae
[/LIST]

The bios reported 4GB installed.
free -m shows 3268 (3.2GB) total Mem.

---

