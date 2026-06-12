---
title: "Kernel compile with no o/s installed??"
date: 2011-08-19
forum: General Help
---

### Post by ClientAlive on 2011-08-19
I have a real simple question:

I'm wondering if I have to have an operating system installed on the machine in order to compile/ install a kernel on it. If there's a way to do it that way I would prefer it - I think. The only reason I wouldn't want to do it that way is if it takes dramatically longer or is prone to error or something like that.

What I'm thinking is I could run something live and just compile it right onto the blank disk. I'm wondering if that's really right though. If it is, I wonder how to direct the o/s running live to the disk I want the thing compiled on. I also wonder whether having the disk formatted with some file system would be a prerequisite or not.

I've done some looking around but don't see that this particular question is really addressed. I think all the manuals and tutorial just assume you know that part going into it. In my situation, it's a fresh, clean machine I'm compiling on and not to have anything like a standard installation of Linux once it's all said and done.

Does anyone have some advice on these things? I've got my hardware all prepared and ready to rock. It's time to do this thing!  :D

Thanks in advance for your help.

---

### Post by ClientAlive on 2011-08-19
Well, so, I should clarify - actually . . .

I'm not opposed to installing something, just that that something will probably end up being removed later anyhow (and that's fine). Speed and accuracy are high on my priorities list. After thinking about it a min maybe running live would take forever - I don't know. So if it came to installing something in order to do the compile, my next thought would be to choose something very light weight and fast. The minimum necessary to get the job done. In fact that (lightweight and fast) would be my desire whatever route must be taken.

The bottom line is this:

I'm sitting here with this base machine that has perfectly blank disks in it and wanting to build something on it. What is the best, fastest, most reliable way to do that with regard to the very next step (to install or not to install the tools needed to do the compiling).

---

### Post by Bachstelze on 2011-08-19
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/) is probably what you want.

---

### Post by spiky001 on 2011-08-19
Building a LFS system will build you a base platform, which you can progress on installing only what you want/need

---

### Post by ClientAlive on 2011-08-19
Well, part of what's going on is that enough different concepts have come into play that I'm not really sure how to end up with the result I want. Here, in this thread, I posed a fairly specific question. In my own mind though there are a lot more questions that effect what I'm trying to do than just what's in that op. It's like the whole whole project is filled with question marks. I've done a lot of reading and learned a lot so far but the thing itself is big! Real big!! At least to me it is.

Xen requires a specific type of kernel to operate. I thought I read somewhere that you can start with a regular kernel and run some tool on it (some xen specific tool or something) that converts it to the kind that Xen can use. That information though, came from documentation that is fairly old - back from like when Xen first started.

Then, last night, something I was reading led me to believe there is a way to just compile the kernel for Xen right from the the start. All this though, is separate from what I brought up in my original post. Whether it seems ugly to folks for someone to have a half dozen different questions on an issue in their post I don't know. I just know I have a very specific goal that I'm trying to find my way to and these things seem to be connected to one another.

I can read but if it comes down to the next year of reading and something like half a million pages before I get to actually do anything - I'd find that a bit discouraging. And whether doing something 10 times over (because you inadvertantly do the things that lead you to the wrong goal) to get to what I'm after is any better, well I'm not so sure about that either.

Really, what would help me most is to identify information that is much much more specific to my intentions. The reality of it is that, that information probably constitutes just a tiny, tiny fraction of the entire body of information just on compiling kernels and all the multitude of ways to do that and reasons for choosing one over the other. If I have to find that needle in a haystack (the half a million pages thing) I'll probably go insane before I ever get started.

I'm reading things and googling like a madman but it's taking forever and I seem to be spinning my wheels reading everything but what I really need to. This isn't just some general do anything type of deal. It's very very specific with a definite goal/ goals in mind. I keep asking myself, what do I do to get to the doing?

Ahhh  . . . The frustration of the newbie. Well this newbie isn't scared of BIG challenges at all, he's just praying to God he'll find his way a little less painfully (and so far this is absolutely excruciating).

I've heard of lfs before. The main book is 1.3 MB. I'm not sure how many pages that is but it souds like a lot. Also, it's but one of half a dozen books on their site. By chance have you read that book before? Do you know if it has anything in it to do with what I'm trying to accomplish?

Ahhh  . . . The frustration of the newbie. Thanks for letting me share mine. I'll be doing my homework. Not sure I understand enough terminology or just well enough to even navigate this massive body of information but I'll sure take a stab at it. I'll add lfs to my list too.

Thanks guys.

---

