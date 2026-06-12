---
title: "Hardware support in Ubuntu vs other distros"
date: 2010-07-15
forum: General Help
---

### Post by feistybill on 2010-07-15
Why does Ubuntu and its variants have better hardware support than its "dad" Debian and than other distros? Where is the difference I wonder?
Is it just a matter of having hardware support enabled in the Kernel config and populating /lib/firmware as much as possible?
Thanks for your replies :)

---

### Post by 3rdalbum on 2010-07-15
Pretty much. I think Ubuntu has some more drivers patched into the kernel as well, ones that are not upstream. Debian would definitely err on the side of stability, whereas Ubuntu is more likely to put in drivers that may conflict with others (although they might not be aware of problems, or might know that they won't be widespread).

---

### Post by QLee on 2010-07-15
[QUOTE=feistybill]Why does Ubuntu and its variants have better hardware support than its "dad" Debian and than other distros? Where is the difference I wonder?[/QUOTE]

I hear your opinion but I do not hold that same opinion. I think you are not really stating something about hardware support but really about how easy one may be to install and configure to a "working" (depending on how one defines that term) system and this in reference to the inexperienced user. Knowledgable and experiences users don't have difficulty with hardware as long as the module is in the kernel or available. inexperienced users often have trouble even with Ubuntu. One of the reasons Ubuntu does so well is that it uses modern kernels with modules for lots of modern hardware (all but the very newest and some of the oldest). 

[QUOTE=feistybill]Is it just a matter of having hardware support enabled in the Kernel config and populating /lib/firmware as much as possible?
Thanks for your replies :)[/QUOTE]

Nope, it's because Ubuntu developers have worked to make it as easy as possible to install (on a wide range of hardware) for people who are too inexperienced to install some of the other operating systems. People often call that better "support". It's a matter of the ability of the sys admin who installs the system. And, as for new hardware, Ubuntu has the same troubles as the others until someone has written the open source module or the manufacturer has issued a proprietary one.

A lot of the time inexperienced people equate, "I just click on it and it installs and does everything (i.e. plays MP3s, movies, etc.)" with "support" because they don't understand why some things can't legally be distributed. But, GNU/Linux distros do "support" hardware as long as there is a module for it and the person installing is capable of installing and configuring it and the distros do "support" using proprietary codecs, they just don't have the legal right to distribute them as part of the system any more than Ubuntu does.

I wonder if this should be moved to the community cafe, it's not a discussion asking for help with an Ubuntu problem. And it is likely to draw some conflicting opinions.

---

### Post by feistybill on 2010-07-15
> **QLee said:**
> I hear your opinion but I do not hold that same opinion.

Whoa. What I meant was: Does Ubuntu work OUT OF THE BOX because of compiled kernel drivers & installed firmware, or is it because it's also using other patches/scripts that I'm not aware of?

I never meant to start a religious war on free software VS the 3vi1n3ss of proprietary stuff. And I since I use Debian, Slackware and OpenBSD on my laptops and I added kernel modules, drivers etc. myself, I'm not exactly an inexperienced user looking for an easy to use distro.

@ 3rdalbum: Thanks for your reply, that's what I was looking for.

---

### Post by QLee on 2010-07-15
[QUOTE=feistybill]Whoa. What I meant was: Does Ubuntu work OUT OF THE BOX because of compiled kernel drivers & installed firmware, or is it because it's also using other patches/scripts that I'm not aware of?[/QUOTE]

Now what you were asking is clear. My answer still the same, Ubuntu works "out of the box" so well because of the consideration and skill of the Unbuntu installer developers.

[QUOTE=feistybill]I never meant to start a religious war on free software VS the 3vi1n3ss of proprietary stuff. And I since I use Debian, Slackware and OpenBSD on my laptops and I added kernel modules, drivers etc. myself, I'm not exactly an inexperienced user looking for an easy to use distro.[/QUOTE]

Didn't mean to suggest *you* were inexperienced, was trying to answer your question, certainly never wrote anything about *you* looking for an easy to use distro. Glad you are knowledgable and experienced, in that case, you're one of the people I was referring to who could use any distro.

Interesting nick you've chosen, Bill.

---

