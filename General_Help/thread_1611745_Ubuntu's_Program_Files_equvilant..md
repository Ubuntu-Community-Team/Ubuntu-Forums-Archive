---
title: "Ubuntu's Program Files equvilant."
date: 2010-11-02
forum: General Help
---

### Post by fmuise on 2010-11-02
Just curious where my program go once installed.

---

### Post by TheAnachron on 2010-11-02
Depends on application. Some go to /opt, some to /home/$username/, some into the systems core.
You can install them anywhere on the system though.

---

### Post by WorMzy on 2010-11-02
Most go into /usr

/usr/bin for executables (_bin_aries),
/usr/lib for _lib_raries,
/usr/share for shared data.

---

### Post by fmuise on 2010-11-02
> **TheAnachron said:**
> Depends on application. Some go to /opt, some to /home/$username/, some into the systems core.
You can install them anywhere on the system though.
 
hmm scary, I'll do my best!

---

### Post by fmuise on 2010-11-02
> **WorMzy said:**
> Most go into /usr
 
/usr/bin for executables (_bin_aries),
/usr/lib for _lib_raries,
/usr/share for shared data.
 
There is hope

---

### Post by TheAnachron on 2010-11-02
Ah! Well we need to clean things up.
While the program data is in /opt or in /home/user, the program itself is installed to /usr. I am sorry, I missunderstood the question.

---

### Post by WorMzy on 2010-11-02
Er.

Some things do get installed to /opt (e.g. XAMPP), though /usr is the more common installation point on Ubuntu.

Nothing gets installed to /home/username, but if you compile something yourself, you'll probably build the source files here. You can also create a bin folder for your own personal executables (/home/user/bin) which won't be used by anyone else.

Oh, I forgot to mention that configuration files get installed to /etc. Programs which get run as a user often generate config files inside that user's /home directory, which may be what Anachron meant.

---

### Post by philinux on 2010-11-02
> **fmuise said:**
> Just curious where my program go once installed.

See this.

---

