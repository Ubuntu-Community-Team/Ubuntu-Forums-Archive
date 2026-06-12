---
title: "Why are Ubuntu packages optimized for i386 architecture?"
date: 2006-05-02
forum: General Help
---

### Post by elettronicha on 2006-05-02
Sorry if I've opened an already discussed thread, but I've searched and found nothing.

Ubuntu is a desktop-oriented distro, easy to use and configure, user-friendly, whose target most probably is a new to GNU/Linux user or a more experienced user who wants a simple and stable distro (heritage from Debian) but doesn't want to waste time in personalizing or hand-configuring it.

It is reasonable to think that this kind of users have got a quite recent desktop pc or a laptop. So, how about optimizing Ubuntu's packages for 686 or at least 586 architectures? 386 architecture is a late 80's architecture and I think it is almost estinguished in desktop applications (office, multimedia, internet, ...). Moreover, let's suppose that someone is still using a 386 for this kind of applications, was he able to make Gnome 2.10 (or 2.8 ) running on his machine, without sweating?

So, **why are Ubuntu packages optimized for i386 architecture?**

---

### Post by Yagisan on 2006-05-02
[QUOTE=elettronicha]Ubuntu is a desktop-oriented distro, easy to use and configure, user-friendly, whose target most probably is a new to GNU/Linux user or a more experienced user who wants a simple and stable distro (heritage from Debian) but doesn't want to waste time in personalizing or hand-configuring it.[/quote]That isn't always true. While a common case, it doesn't cover all uses of Ubuntu.

[QUOTE=elettronicha]It is reasonable to think that this kind of users have got a quite recent desktop pc or a laptop.[/quote]That would depend on your country and economic status.

[QUOTE=elettronicha]So, how about optimizing Ubuntu's packages for 686 or at least 586 architectures?[/quote]It already is. it uses an i486 instruction set with the instructions odered to provide the most benefit to pentium4 systems.

[QUOTE=elettronicha]So, **why are Ubuntu packages optimized for i386 architecture?**[/QUOTE]i386 is the name of the architecture. It would probally surprise you to learn that there are many new systems being sold today that don't support a full i586 or i686 instruction set.

Ubuntu is already tuned for pentium4 systems, and it has been demonstrated that for almost all applications the is zero speedup when built specifically for i586 or i686. (i586 optimised applications actually run slower on i686 and later machines). If an application does benefit from i686 or later, it has an -i686 package. Two cases in point, glibc and the kernel. All others recieve no benefit.

---

### Post by elettronicha on 2006-05-02
> **Yagisan]That isn't always true. While a common case, it doesn't cover all uses of Ubuntu.[/QUOTE]
Yes, I know it is a very common case, but also 2% is very close to 0% :) Which other uses for Ubuntu?

> That would depend on your country and economic status.
That is very true, I do know that most south-american, african and south-eastern people doesn't own a modern pc or doesn't own one at all, but as I told: "let's suppose that someone is still using a 386 for this kind of applications, was he able to make Gnome 2.10 (or 2.8 ) running on his machine, without sweating?".  

> It already is. it uses an i486 instruction set with the instructions odered to provide the most benefit to pentium4 systems.
I don't understand, sorry :) I was talking about 586 or 686. You say "it uses an i486 instruction set with the instructions odered to provide the most benefit to pentium4 systems", but why packages have "386" flag? What kind of parameters do they pass to the configure? I see you're a debian packager, so I'm speaking with the right person. said:**
> i386 is the name of the architecture. It would probally surprise you to learn that there are many new systems being sold today that don't support a full i586 or i686 instruction set.
Yes! You surprised me! What kind of systems?

> Ubuntu is already tuned for pentium4 systems, and it has been demonstrated that for almost all applications the is zero speedup when built specifically for i586 or i686. (i586 optimised applications actually run slower on i686 and later machines). If an application does benefit from i686 or later, it has an -i686 package. Two cases in point, glibc and the kernel. All others recieve no benefit.
Could you link me something on that, please? I'd appreciate it, it's interesting.

Thanks.

---

### Post by az on 2006-05-02
[QUOTE=elettronicha]Yes, I know it is a very common case, but also 2% is very close to 0% :) Which other uses for Ubuntu?

[/QUOTE]

Servers, routers, database, lots of stuff.  Anyway, As stated, you cannot really get userspace applications much more optimised.

[QUOTE=elettronicha]Y
That is very true, I do know that most south-american, african and south-eastern people doesn't own a modern pc or doesn't own one at all, but as I told: "let's suppose that someone is still using a 386 for this kind of applications, was he able to make Gnome 2.10 (or 2.8 ) running on his machine, without sweating?".  
[/QUOTE]

I don't think you will actually be able to install ubuntu-desktop on a 386.  But if you have a pentium one with enough ran, sure she can.  The one-laptop-per-child ($100 laptop) project is aiming to ship something like a 500Mhz Celeron.  Not too powerful in comparision with a new DEll....

   

[QUOTE=elettronicha]Y
Yes! You surprised me! What kind of systems?
[/QUOTE]

Via C3, for example.

[http://en.wikipedia.org/wiki/VIA_C3](http://en.wikipedia.org/wiki/VIA_C3)

---

### Post by elettronicha on 2006-05-02
[QUOTE=azz]Servers, routers, database, lots of stuff.[/QUOTE]
I thought few people used Ubuntu for those stuff since imo they would have prefered Debian. Maybe I'm underrating my favourite distro. :)

> The one-laptop-per-child ($100 laptop) project is aiming to ship something like a 500Mhz Celeron.  Not too powerful in comparision with a new DEll....
But a celeron 500 is something like a 586, or not?

Anyway, I remember the time to get firefox 1.5.0.2 running and to browse pages and I see the time to get swiftfox 1.5.0.2 (firefox optimized for newer architectures ) running and to browse pages. No comparison! Why?

---

### Post by Yagisan on 2006-05-03
[QUOTE=elettronicha]I thought few people used Ubuntu for those stuff since imo they would have prefered Debian. Maybe I'm underrating my favourite distro. :)[/quote] I have it on 1 router, 2 servers, several thin clients, and 0 (yes zero) desktops. Ubuntu can be useful for a varietry of reasosn. It fits my needs (and I don't want to support multiple operating systems. The i386 systems themselves range from i486 class, to i686, and the new amd64 architecture).
[QUOTE=elettronicha]But a celeron 500 is something like a 586, or not?[/quote]All celerons are i686 class. That doesn't mean however they support extensions like sse, or sse2.
[QUOTE=elettronicha]Anyway, I remember the time to get firefox 1.5.0.2 running and to browse pages and I see the time to get swiftfox 1.5.0.2 (firefox optimized for newer architectures ) running and to browse pages. No comparison! Why?[/QUOTE]Most likely, they change to a faster algorithm. Often the biggest speed improvements come from looking at what you do, then finding a smarter way to do it.

I suppose the best way to compare cpu class is to a car. all i386 style cpu's have the same architectural features regardless of model, just like a car. However, like a car each new model has some improvement over the previous model, but it still has the same basic functions.

---

