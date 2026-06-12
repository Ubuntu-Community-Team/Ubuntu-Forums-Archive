---
title: "Distributing applications on Linux"
date: 2009-07-31
forum: General Help
---

### Post by petike on 2009-07-31
Hi all,
I am interested in developing applications in C++ language (so as an output of my coding I would like to have some executable binary file and if required also distributed with some additional libraries). And I also want they to be as portable as it can be because there are more operating systems in the world and each of them has different architecture and different requirements for the applications.

So there are many operating systems and the most famous are:
    ----Microsoft Windows
    ----Unix
        --------Linux
        --------BSD
    ----Macintosh
*(NOTE: This is my own opinion. If I am wrong I will be very happy if you correct me.)*

Certainly, I want my applications to be compatible with Windows because most people in the world have right this operating system *(again you can correct me if I am wrong)*.
And secondly, I also want my applications to be compatible with Linux system (which is not so widely-spread as Windows) because I "like" the idea of "free" software and I "want" to support it.
With Macintosh I don't have any experience and for now I am not interested in that (sorry Apple, :-) ).

So, after this "very long" introduction I am coming to my main problem: "distributing applications on Linux" and here is a simple question:
**"If I have some executable file which I can run for example on "Ubuntu", can I run it also without problems on any other type of Linux (for example "Fedora") just by copying that file to that specific platform without any additional recompilation?"**
Or in other words, does the executable file depend on the Linux kernel or also on the "more specific" platform (e.g. Ubuntu)?

Thanks in advance.

---

### Post by HermanAB on 2009-07-31
If you link it statically with all required libraries, then yes.

However, note that in terms of many of the lincences used, you would have to also supply full source code with your application to your customer upon request (or publish it on a server for everybody).

---

