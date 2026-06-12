---
title: "Celeron faster than AMD64 dual core?"
date: 2010-10-09
forum: General Help
---

### Post by VanceVEP72 on 2010-10-09
This doesn't make sense and was wondering if someone could shed some insight.

I have two Compaq Presario laptops... Both CQ60 series. One has a Celeron processor and the other has an AMD Athlon X2.  I thought FOR SURE that Ubuntu would run faster on the AMD machine, right?  WRONG!  It runs much faster on the Celeron machine. Why?

I have both Ubuntu installations setup the same with this exception... The AMD machine is setup as a dual-boot with Windows Vista Premium and the Celeron machine is setup as a full Ubuntu installation with Windows XP Pro running in VirtualBox.

Can anyone shed some light on this for me? I really wanted to make the AMD my primary laptop as it has a built-in card reader and the Celeron does not. 

Links to the machine specs can be found here:

[https://docs.google.com/document/edit?id=1kZmCLcwhw8OOU0yavd7iQxRCuhadUpEdiyNIR58wvOI&hl=en&authkey=CKfWtssM](https://docs.google.com/document/edit?id=1kZmCLcwhw8OOU0yavd7iQxRCuhadUpEdiyNIR58wvOI&hl=en&authkey=CKfWtssM)

[https://docs.google.com/document/edit?id=18iLHds1UnECiExad_Y3sn9lNoC6Me3GkGs7TwhI_92o&hl=en&authkey=CLWqntgK](https://docs.google.com/document/edit?id=18iLHds1UnECiExad_Y3sn9lNoC6Me3GkGs7TwhI_92o&hl=en&authkey=CLWqntgK)

Thanks in advance!

---

### Post by ezsit on 2010-10-09
How are you judging "faster?" Are you just going by the responsiveness of the desktop? Are your running disk benchmarks? Are you compiling programs? Running videos? It really depends on what you are doing. You need to specify what you mean by faster and in what contexts for any one to have any ideas.

---

### Post by VanceVEP72 on 2010-10-09
Sorry... to clarify... I am not running any benchmarks. It is just a noticeable difference in response. I haven't compared running videos, just opening programs and surfing the web.

---

### Post by Vaphell on 2010-10-09
single app can run better on celeron if the performance of its core is higher than that of a single core in X2 - most apps are single threaded and don't benefit from dual core at all. What dual core processors are better at is multitasking when the load gets divided so you don't get the effect of computer totally chocking on a single cpu intensive program

there is also a dozen of things that can cause that difference: misconfigured system, compiz running/not running (it adds to a gui lag), cpu being set to powersaving mode (running at lowest frequency), etc.

You need some testing to evaluate which scenarios look better on which configuration.
For example run few copies of a video clip and see how it scales up. Dual core should perform better when you got 2+ clips played simultaneously (depends on quality, small res can require let's say 3 to hit 100% of a single core)

---

