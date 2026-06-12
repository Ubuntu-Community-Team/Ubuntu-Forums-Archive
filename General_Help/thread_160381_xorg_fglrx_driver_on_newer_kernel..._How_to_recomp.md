---
title: "xorg fglrx driver on newer kernel... How to recompile restricted modules?"
date: 2006-04-14
forum: General Help
---

### Post by zi99y on 2006-04-14
Hi,

I've had repeated nightmares using the latest fglrx driver for my ati x700 graphics chip, mostly the machine freezing when shutting down. Now I have decided it's just not worth it, and have reinstalled the 8.6.20 version that comes from the repos package, and it works fine for me.

The problem I'm having now, is that in order to get DRI working I have had to revert to using an old kernel that has linux-restricted-modules pre-packaged in the repos. I cannot get DRI / OpenGL working without it. :-k 

I cannot find any information regarding recompiling these restricted modules for a later kernel, and I think this is what I need to do to fix this problem.

Anyone with any thoughts/ ideas / links on how to do this would be very gratefully appreciated.

---

### Post by uteck on 2006-04-17
If you have the src lines enabled in your sources.list, you can try downloadng the source package and compiling it.  But I am not sure if there is a source package for it since it is restricted.

---

### Post by zi99y on 2006-04-17
thanks, for the reply!

I have got the source from the repos, but I have no idea what to do with it :(

Still running an old kernel for now, but I'd love it if someone could show me how to recompile this.

---

