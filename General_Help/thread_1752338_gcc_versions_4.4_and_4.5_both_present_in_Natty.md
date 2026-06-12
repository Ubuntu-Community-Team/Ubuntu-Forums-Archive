---
title: "gcc versions 4.4 and 4.5 both present in Natty"
date: 2011-05-07
forum: General Help
---

### Post by james_mcl on 2011-05-07
Hi all,

I've just done an upgrade install from Maverick to Natty, and noticed (while poking about in Synaptic) that version 4.4 of g++ was installed alongside 4.5. (Further investigation revealed that this was the case for both gcc and gcj as well.)

If anyone here installed Natty from scratch, could they look in Synaptic and tell me if both versions come installed by default? Or can I assume the presence of 4.4 is simply because it was installed under Maverick and get rid of it?

Thanks,

James McLaughlin.

PS. I'm using the "Ubuntu Classic" interface (i.e. Gnome) and admit that I don't know if it's possible to get the required information from Unity's "Ubuntu Software Centre".

---

### Post by mc4man on 2011-05-07
The default gcc for natty would be 4.5.2 and you should be able to remove 4.4.X if desired (though no harm in having installed

You can d. check with - 
gcc --version

---

