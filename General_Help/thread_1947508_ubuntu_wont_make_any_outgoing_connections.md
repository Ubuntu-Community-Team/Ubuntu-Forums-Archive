---
title: "ubuntu wont make any outgoing connections"
date: 2012-03-26
forum: General Help
---

### Post by Kr0nZ on 2012-03-26
hey im running ubuntu 10.10,
but over the past 2 days ive noticed my HTPC has been making any outgoing connections, I noticed it initially when sabnzbd wasnt downloading. So when i started looking into it i tried to do "wget http://www.google.com"
but i just keep getting

```
--2012-03-26 19:21:07--  http://www.google.com/
Resolving www.google.com... failed: Temporary failure in name resolution.
wget: unable to resolve host address `www.google.com'
```

I havnt changed my hostname or username or anything, it was working then just stopped working for no reason.
Something i have noticed is, I also have a wifi card in the PC but it topped working along time ago so i have has it connected to the ethernet instead, now i have noticed the wifi has started working again, So whenever my pc starts up it makes to network conenction (eternet and wifi), but i ussually disconnect the wifi

could the wifi be interfering? even tho i disconnect it?
how can i disable it completely? its the in-built wifi manager not wicd, i can seem to find anywhere to configure it

---

### Post by Kr0nZ on 2012-03-26
fixed it,
for some reason my '/etc/resolv.conf' file was empty.
I copied the one from my main pc and its working now.
Not sure how it became empty tho.
I set 'chattr +i /etc/resolv.conf' so it shouldnt happen again.

---

### Post by sammiev on 2012-03-26
> **Kr0nZ said:**
> fixed it,
for some reason my '/etc/resolv.conf' file was empty.
I copied the one from my main pc and its working now.
Not sure how it became empty tho.
I set 'chattr +i /etc/resolv.conf' so it shouldnt happen again.

Thanks for giving us folks the update as it will likely help others. Now could you please mark this thread as Solved. :)

---

