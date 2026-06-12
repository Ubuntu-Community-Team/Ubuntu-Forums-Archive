---
title: "what does this mean???"
date: 2010-02-03
forum: General Help
---

### Post by drink_stir on 2010-02-03
how come everytime i try to update or download a package it gives me this error? (pic attached) it happens in both the gui and terminal and tty.

---

### Post by ad_267 on 2010-02-03
What do you get if you run this in a terminal:
```
sudo dpkg --configure -a
```

This will try to configure all (-a) packages that require configuration.

---

### Post by rocket16 on 2010-02-03
This may also mean, that it your OS has Broken Packages. Try Synaptic.

---

### Post by ad_267 on 2010-02-03
Yeah, Edit -> Fix broken packages under synaptic might help, but I find most of the time it just gets stuck and you have to fix stuff yourself. The command I posted will hopefully give a bit more information about what's wrong if Synaptic can't fix it.

---

### Post by drink_stir on 2010-02-03
i tried the sudo dpkg --configure -a before i posted this but i havent tried to fix packages in synaptic. will do that and get back to you.

---

### Post by drink_stir on 2010-02-03
0 broken packages. and when i do sudo dpkg --configure -a this is what i get... and im not sure how to fix them manually.

---

### Post by fr3ak.m3 on 2010-02-03
I got stuck to such problem some days ago and I found this over the internet. This worked for me. Hope it works for you too.
[URL="http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/"]
Here is the tutorial.[/URL]

---

### Post by drink_stir on 2010-02-03
thanx fr3ak.m3. just what i was looking for. got it all fixed and working beautifully.

---

