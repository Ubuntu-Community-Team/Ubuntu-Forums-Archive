---
title: "What processor?"
date: 2011-06-27
forum: General Help
---

### Post by itsmilesdavis on 2011-06-27
Hello all.

I want to build a new desktop/server (running linux, of course). I'm really torn between AMD and Intel. Why do I need multiple cores? I work in computational biology and will be sending simulation tasks to as many cores as I have. The problems are 
generally embarrassingly parallel.  Languages of choice: python and R.

Since I don't want to spend $1000 on an Intel six-core, it looks like my options are 6-core AMD or 4-core Intel.

Will I be disappointed in the performance of an AMD processor?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103913)

Intel went to the 32nM chips. Would I be happier with this?
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070](http://www.newegg.com/Product/Product.aspx?Item=N82E16819115070)

I am also considering a liquid cooling option: for several reasons (one being just pure fun). Does anyone have experience in overclocking these chips?

I'm not looking for a flame war about which is better, AMD or Intel. I thought if I posted on here, then someone might offer me some advice which I haven't considered yet.

I'd also like to hear comments on motherboards. I've had best of luck with Asus. This PC will not be used as a gaming machine.

Thanks,
-JJ.

---

### Post by pqwoerituytrueiwoq on 2011-06-27
i know in AMD CPUs using any non-stock cooling device voids the warranty idk wiht intel CPUs
newegg is having server issues right now
that said
i am very pleased with my AMD Phenom(tm) II X4 965
if you go with a I7 go with the quad core 4 extra threads are not worth 700$ imo

---

### Post by ptminh20 on 2011-06-27
in my opinion,  you should choice AMD processor. i am using it now, really good men.

---

### Post by idoitprone on 2011-06-27
> **itsmilesdavis said:**
> Hello all.

I want to build a new desktop/server (running linux, of course). I'm really torn between AMD and Intel. Why do I need multiple cores? I work in computational biology and will be sending simulation tasks to as many cores as I have. The problems are 
generally embarrassingly parallel.  Languages of choice: python and R.


 In terms of cpu speed, it not about the number of cores you have, it is all about the cpu architecture and the kernel scheduler. Good thing about linux, is that ingo design the scheduler so it can scale up well which is to the distaste of con kolivas. One more thing, do not mix up logical vs real cores. It matter signification in terms of cpu speed. However, the only way we can know about cpu speed is that we actually have to benchmark it. Otherwise, it is impossible to know as most cpus do not surpass 3.0 ghz and yet they get faster every year with the same clock cycles.

Bottom line, find benchmarks.
> 

I'd also like to hear comments on motherboards. I've had best of luck with Asus. This PC will not be used as a gaming machine.



If your software is gpu accelerated , then you might reconsider. Gaming rigs are just computers decent cpus but really good gpus. [https://en.bitcoin.it/wiki/Why_a_GPU_mines_faster_than_a_CPU](https://en.bitcoin.it/wiki/Why_a_GPU_mines_faster_than_a_CPU)

---

### Post by tgalati4 on 2011-06-27
I'd get a used Dell PowerEdge or HP Proliant rack-based server with dual Xeon's.  You'll get faster RAM and IO pathways and faster disk IO which will probably help you more than simple core count.  You can always add a low-profile graphics card if you need workstation graphics.

---

### Post by RoyLongbottom on 2011-06-28
[FONT=Verdana][SIZE=2]You might look at my benchmark results via:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/linux%20benchmarks.htm](http://www.roylongbottom.org.uk/linux%20benchmarks.htm)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]These include resulps on my quad core Phenom and core 2 Duo. For Phenom and Core i7, but via Windows, see:[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/quad%20core%208%20thread.htm](http://www.roylongbottom.org.uk/quad%20core%208%20thread.htm)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][http://www.roylongbottom.org.uk/windows7-64.htm](http://www.roylongbottom.org.uk/windows7-64.htm)[/SIZE][/FONT]
[FONT=Verdana][SIZE=2][/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]For embarrassingly parallel computation, you should look at nVida CUDA programming. My results show example speeds using different GeForce graphics cards vs same calculations using multiple threads on normal CPUs.[/SIZE][/FONT]
[FONT=Verdana][SIZE=2] [/SIZE][/FONT]
[FONT=Verdana][SIZE=2]Roy[/SIZE][/FONT]

---

### Post by scu-ba-de-buntu on 2011-06-28
> **RoyLongbottom said:**
> you should look at nVida CUDA programming. My results show example speeds using different GeForce graphics cards vs same calculations using multiple threads on normal CPUs.

from a computational chemistry point of view, I second that. Look into GPU programming

as for x86-ish processors, i prefer AMD 64bit series

---

### Post by itsmilesdavis on 2011-06-29
@tgalati4: I hadn't considered this option. I took a brief look at Dell's site. Do you recommend any specific sites to buy used servers? Thanks for the idea.

@RoyLongbottom: Thanks for the websites. Very informative.

@others: I am reluctant to go the GPU route, because I need my software to be platform independent. While programming for GPU is tempting, it would be a hindrance.

---

### Post by Foxcow on 2011-06-29
I can't recommend the 1090T or 1100T enough.  80% of the performance for 1/4 the cost.  Ubuntu and Windows flies with my setu (check out my signature).  As far as motherboards, for the past few builds, I've used MSI and have been pretty happy.

---

### Post by Ozymandias_117 on 2011-06-29
I would advise against Gigabyte for the Motherboard.  I have two and have had multiple problems with each.

---

### Post by 3Miro on 2011-06-29
> **Ozymandias_117 said:**
> I would advise against Gigabyte for the Motherboard.  I have two and have had multiple problems with each.

I guess millage varies, I have 4 Gigabyte Mobos and I am very happy with all of them.

As for the CPU, there were big discussions on several thread. For AMD you get more power per dollar. Also, 6 real cores tend to be better for multi-threading then the Intel 4+4 HT scheme. If money is not the issue, top of the line Intel CPUs are faster than top of the line Intel ones, however, they are significantly more expensive.

AMD is about to release a new CPU model for 32nm that is re-engineered from the ground up. You may want to consider waiting a month or two either for a gamble with "bleeding edge" technology or for the drop in prices that it usually brings.

---

