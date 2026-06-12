---
title: "GnoMenu not working on 10.10"
date: 2010-12-18
forum: General Help
---

### Post by scottykal12 on 2010-12-18
Hello,

I have had GnoMenu since 10.04 and have had no problems with it and for a while in 10.10 it was working fine but not to long ago I started getting and error message saying:

The panel encountered a problem while loading "OAFIID:GNOME_GnoMenu".

I've looked far and wide and cannot seem to find an answer.

Thanks in advance,

Scott

---

### Post by Frogs Hair on 2010-12-18
I had this problem once and I removed the Gnomenu rebooted and reinstalled it. This worked for me ,but gave no insight into what caused the problem.

---

### Post by scottykal12 on 2010-12-18
Thanks for the quick reply but it is still a no go

---

### Post by scottykal12 on 2010-12-18
OK I figured it out.
 It had to do with python. (I think I screwed it up trying to get pygame)

Anyways 
I just went into /usr/lib/gnomenu and changed the top from
#!/usr/bin/env python 
to
#!/usr/bin/env python2.6

---

### Post by al prince nofl on 2010-12-20
> **scottykal12 said:**
> OK I figured it out.
 It had to do with python. (I think I screwed it up trying to get pygame)

Anyways 
I just went into /usr/lib/gnomenu and changed the top from
#!/usr/bin/env python 
to
#!/usr/bin/env python2.6

I have the same problem
But i can't find the folder "gnomenu" in that pas
[IMG]http://oi53.tinypic.com/5cj9eo.jpg[/IMG]

---

### Post by ShatPank on 2011-05-02
> **scottykal12 said:**
> OK I figured it out.
 It had to do with python. (I think I screwed it up trying to get pygame)

Anyways 
I just went into /usr/lib/gnomenu and changed the top from
#!/usr/bin/env python 
to
#!/usr/bin/env python2.6


This is the exact same error I get, but I don’t understand what file you edited? could you explain a little more for me please? I'm quite new to Linux

---

