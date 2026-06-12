---
title: "Setting Up Second Instance of Conky"
date: 2011-09-12
forum: General Help
---

### Post by DobsonM on 2011-09-12
So on my left hand side I have my initial instance of conky and I want to put a second one on the right hand side.  I have had a google and what I have found haven't been very clear on how to do this, can someone please tell me how to do this?

Thanks in advance.

---

### Post by Toz on 2011-09-12
You would create 2 separate configuration files (for example ~/.conkyrc and ~/.conkyrc2). Then in your startup, execute conky twice and specify the configuration file to use.

Have a look at: [http://ubuntuforums.org/showthread.php?t=885992]("http://ubuntuforums.org/showthread.php?t=885992") for examples.

---

### Post by DobsonM on 2011-09-13
Thanks for the reply.

---

