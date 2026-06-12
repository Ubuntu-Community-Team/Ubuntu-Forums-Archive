---
title: "cpu very high , because i have not swap file?"
date: 2011-11-05
forum: General Help
---

### Post by Gianmaria on 2011-11-05
Hi
under ubuntu 10.10 i got a high cpu consuming

i have not swap file
and 3gb of ram

the lack of swap file could be the issue?

thanks
cheers

---

### Post by Gremlinzzz on 2011-11-05
> **Gianmaria said:**
> Hi
under ubuntu 10.10 i got a high cpu consuming

i have not swap file
and 3gb of ram

the lack of swap file could be the issue?

thanks
cheers

:popcorn:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by BillyBoa on 2011-11-05
This problem occurs as well, when you are not using proprietary video drivers.

---

### Post by Gianmaria on 2011-11-05
> **Gremlinzzz said:**
> :popcorn:

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

> **BillyBoa said:**
> This problem occurs as well, when you are not using proprietary video drivers.

Thanks

so do you think could be the lack of swap file and video card drivers

---

### Post by 2F4U on 2011-11-05
What is the output of

free -m

Before we start guessing, we should find out if you are running out of RAM or not.

Also, did you run top or htop to see if particular processes are causing a high CPU load?

---

### Post by Gianmaria on 2011-11-05
> **2F4U said:**
> What is the output of

free -m

Before we start guessing, we should find out if you are running out of RAM or not.

Also, did you run top or htop to see if particular processes are causing a high CPU load?
the only program that causes high cpu consuming in idle is the process monitor:(

thanks

---

