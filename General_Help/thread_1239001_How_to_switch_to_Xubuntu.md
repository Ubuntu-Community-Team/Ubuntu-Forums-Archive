---
title: "How to switch to Xubuntu?"
date: 2009-08-13
forum: General Help
---

### Post by jstrevino on 2009-08-13
Let me start by saying that I've been a Linux user for about a week now, so apologies if this question reflects my ignorance more than anything else.

In brief, I've got a Dell Mini 10v netbook that I like quite a bit, purchased specifically for Ubuntu use. 99% of the time, I've only got two things open -- Conky and Opera (which I use for both mail and browsing). And ... things get a little slow pretty quickly.

I'm wondering if maybe swapping GNOME for XFCE would help, as the latter is reputed to be tailored for low-resource environments. My questions: 

1) How do I do this without zapping all my programs, data, etc.?
2) Should I actually d/l an Xubuntu install, or just work with an xfce install from the command line?

Again, sorry for this basic-level query. Any pointers are appreciated.

---

### Post by kerry_s on 2009-08-13
open synaptic & install xfce4, don't install xubuntu-desktop it's to slow.

logout, select xfce4 from the session menu & log back in

---

### Post by P4man on 2009-08-13
> **kerry_s said:**
> open synaptic & install xfce4, don't install xubuntu-desktop it's to slow.

logout, select xfce4 from the session menu & log back in

Im curious, why would you not install xubuntu-desktop ? In what way is it slower than installing only xfce? The xubuntu-desktop meta package was made specifically to enable xubuntu, so im not sure what the difference is or what you're missing out on when you only install the xfce desktop manager?

---

### Post by kerry_s on 2009-08-13
> **P4man said:**
> Im curious, why would you not install xubuntu-desktop ? In what way is it slower than installing only xfce? The xubuntu-desktop meta package was made specifically to enable xubuntu, so im not sure what the difference is or what you're missing out on when you only install the xfce desktop manager?

because it's a meta-package that installs a whole bunch of stuff, when all you actually want is the speed of xfce4 desktop.
also using a meta-package ties everything together, so say there some part you don't want or need & decide to uninstall it, it will take a lot of other stuff with it cause it's tied to each other.

---

### Post by P4man on 2009-08-13
looking at the package list, Id say there is quite a bit in there that you probably want when using xfce. I mean, powermanagement tools, thunar file manager, etc.. Im not sure its a better idea to use all gnome tools under xfce? Or are those dependencies of xfce4 ?

Anyway, Ive never tried it, I assume it works with some limitations, I do know installing xubuntu-desktop works. Im not sure if the trade off is worthwhile. I guess the OP can always install xubuntu-desktop later on if he finds stuff missing.

---

### Post by kerry_s on 2009-08-13
straight xfce4 is very minimal. 
i use a debian testing base install + xfce4, makes it very easy to keep things light & fast.

---

### Post by martinbaselier on 2009-08-13
If you just started, you could install xubuntu-desktop. I prefer to just install xfce4 and the packages I need. But it takes some time to learn which ones you want. If you search for xfce4 in package manager, you can probably see from the description what you want and what you don't

What you probably don't want is gnome-numeric and abiword. Open office is much better (preferably 3.0 ).

---

### Post by jstrevino on 2009-08-13
Thank you sirs. That was remarkably easy. I'm operating off of XFCE now, and it really is quite a bit faster (albeit buggy with Adobe Air apps like Tweetdeck, which does not seem to wish to work).

I had it in my head that a new desktop environment meant an OS reinstall, which clearly it does not in the Linux universe. Again, many thanks!

---

### Post by kerry_s on 2009-08-13
> **jstrevino said:**
> Thank you sirs. That was remarkably easy. I'm operating off of XFCE now, and it really is quite a bit faster (albeit buggy with Adobe Air apps like Tweetdeck, which does not seem to wish to work).

I had it in my head that a new desktop environment meant an OS reinstall, which clearly it does not in the Linux universe. Again, many thanks!

:lolflag: will let you try before you buy.

you could do that if you want a clean install, but i would suggest you just use what you have now to just find out what you like.

the prepackaged distro versions are great as they save you from having to do it yourself. that way you don't have to install something you don't want, to get what you actually want.

the next lighter desktop from xfce4 is "lxde" you might want to give that a go as well. you try it the same way you did with xfce4. the distro version is crunchbang, for those lxde fans.
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

**sudo apt-get install lxde**

then log out, select lxde & log back in.

try & have fun, don't be afraid to try things. in linux you can install as many times as you want there is no limit, if you break it you learn. :)

---

### Post by gfh316 on 2009-08-16
Great tips from everyone.  Had same question days ago, beat head on wall figuring out.

Could have checked this forum, saved lots of time.

Learned a lot, though.. :)

Have netbook, most distros too slow.  Xubuntu desktop best at doing everything out of 3 desktops and 4 distros tried.

lxde sounds interesting, too.

Thanks to all.

---

### Post by lessgov2007 on 2009-08-16
Have you considered giving Ubuntu Netbook a try? [http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

I looked and your model netbook has already been tested with this version of Ubuntu. It might be just what you need.

---

