---
title: "RT Performance"
date: 2010-01-14
forum: General Help
---

### Post by esrrms on 2010-01-14
Hello, I'm using UbuntuStudio 9.10 with the RT kernel that came with it. My problem is the performance I'm getting with the RT kernel. In the past I was using UbuntuStudio 8.04 with the stock RT kernel and when running jack with a small buffer, could run a full session with no drop outs and jack would report only about 50% "computer" usage (or whatever it is that qjackcontrol shows you). With 9.10 though I have to have a huge buffer to even get it running and when only running one thing (like zynaddsubfx) it jumps to like 75%. Everything works, it just seems to work badly with 9.10.

I've tried compiling my own kernel and got no better performance. I've read up on what the problem might be, and the only thing I can find is maybe something with IRQ's (which is a subject I don't really understand and haven't found a way to change them anyway)

So if anyone knows of areas to look at for RT performance, I would appreciate it. I'm hoping it's some configuration thing that's different with this install or something, but I'm at a loss on where to look.

Some random info that people might want to know for this post...

I'm using a fire wire device. (Presonus FP10)
Main file system is on one drive while the file system I record to is a separate drive.

Software versions that I use...
kernel: 2.6.31-9-rt
libffado: 2.0.0
jack: 1.9.4
ardour: latest 2.0 from svn

There's probably more info someone answering would want to know, so ask and I will post the info you need.

Any help is much appreciated.

- esrrms

---

