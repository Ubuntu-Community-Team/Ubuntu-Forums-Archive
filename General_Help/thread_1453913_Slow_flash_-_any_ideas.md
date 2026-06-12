---
title: "Slow flash - any ideas?"
date: 2010-04-13
forum: General Help
---

### Post by TigerEar on 2010-04-13
Hey dudes and dudettes.

I'm a new Ubuntu convert and as far as I'm concerned everything about Ubuntu is better than Windows 7. One thing's really bugging me, though.

I'm into photography and photojournalism and a lot of websites use flash-based galleries. These galleries chug by really slowly and perform terribly. It's not a big issue, but it's annoying.

Everything flash based seems really slow. I'm using Lucid Lynx and Chromium and I can't seem to get flash-based sites to play smoothly. Examples are [www.life.com](www.life.com) and [www.lens.blogs.nytimes.com](www.lens.blogs.nytimes.com)

Does anyone have any tips or tricks to make the experience better?

Thanks

---

### Post by nitstorm on 2010-04-13
Have you tried disabling IPv6???

---

### Post by gradinaruvasile on 2010-04-13
Open a new page, type in the address bar:

about:plugins

press enter.
How many flash plugin entries do you have there?

---

### Post by TigerEar on 2010-04-13
I've got two, ShockWave Flash and FutureSplash Player. Both are enabled. 

What's IPv6?

---

### Post by gradinaruvasile on 2010-04-14
> **TigerEar said:**
> I've got two, ShockWave Flash and FutureSplash Player. Both are enabled. 

What's IPv6?

Like in my screenshot? You see there is only 1 instance of Flash (Flash can open both futuresplash and shockwave). The point is that only 1 section is supposed to be there.

Also, flash-intensive sites tend to be slow on older hardware.

IPv6 is Internet Protocol 6. The protocol in use these days is IPv4. But all OSes have already iplemented the 6 protocol and it is in use in some parts of the world (like Japan AFAIK). But it is not used widely. I disabled the support for it a lon time ago and never bumped in any IPv6 sites yet.
The word is that it sometimes can slow your browsing. There are many how-to s and discussions around, use the search function.

---

### Post by TigerEar on 2010-04-14
I don't have old hardware. As I said, the sites run perfectly fine on Windows 7 and XP on the same computer. 

Is this something that just happens in Ubuntu? is there actually no way to make flash work properly?

---

### Post by TigerEar on 2010-04-14
Just disabled IPv6 and it hasn't had any effect on Flash performance. Any ideas?

Cheers,

Tiger

---

### Post by Septi on 2010-04-14
Ugh, flash... The Horror. Not to lose our calm now, HTML5 is coming to our rescue :)

But yes, flash happens to be abnormally slow on linux. This can be frustrating at times, but at least you won't fall prey to flash games, that's for sure.

But there might be something to resolve the issue. Have you heard of a Brain**** Scheduler? It's alternative to default scheduler, so to use it, you need a kernel with it. But people who tried it reported a noticeable increase in responsiveness, including perfomance boost for flash. Dunno why it happens so, maybe flash does threading wrong or something.. Anyway, there's been a thread about this on the launchpad, and I think someone even got a repository with ready-made packages. I'd like to try it myself, but didn't get down to it just yet. So I can only give you a couple of links and a stern warning: USE AT YOUR OWN RISK.

Here's a description of what BFS is by it's creator: [http://ck.kolivas.org/patches/bfs/bfs-faq.txt](http://ck.kolivas.org/patches/bfs/bfs-faq.txt)
And a bug on launchpad.net, where there're some instructions: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424927)

I don't think it can cause any permanent damage. If anything goes wrong, you should be able to boot with an old kernel and remove BFS. Fingers crossed, so

Take care.

---

### Post by TigerEar on 2010-04-14
Cheers, I'll have a look

Thanks very much for your help dude

---

### Post by tilixibr on 2010-04-30
What I did was turn off desktop graphics when i was using a flash object that is graphic intense (ex: flash games), somehow, flash performed better and faster, but not as good as in Windows, but still pretty good :)

---

### Post by mikemikemike on 2010-04-30
If you are using 64-bit flash it wont work perfect.

---

### Post by tilixibr on 2010-04-30
Really? I just installed 10.04 (x64) and flash performs better on 64 bit than on my 9.10 (x86) install =\, maybe my graphics card may have something to do with it, since it's not busy dealing with desktop graphics when i disable them

---

