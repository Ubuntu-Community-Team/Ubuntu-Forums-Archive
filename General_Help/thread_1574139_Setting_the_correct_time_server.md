---
title: "Setting the correct time server"
date: 2010-09-13
forum: General Help
---

### Post by Chethan S on 2010-09-13
I live in India and my computer's time is always a minute ahead. I have selected the option to keep it synchronized with internet time servers but as there does not appear to be a time server for ubuntu in India I am not sure what to do. As of now I tried selecting foreign server but can't see anything happen.

---

### Post by srs5694 on 2010-09-13
One minute is a peculiar amount to be off. Even with huge intercontinental delays, I wouldn't expect NTP to be off by anywhere near that much. How are you determining that your time is one minute off? Perhaps the standard by which you're measuring it is off, not the computer.

To more directly answer your question, though, check [this page](http://support.ntp.org/bin/view/Servers/WebHome) on how to locate a time server near you. Alternatively, you can use [the NTP server pool,](http://www.pool.ntp.org/en/) although that can be a bit hit-or-miss. One trick I sometimes use is to try to locate a server operated by my ISP. Most ISPs have time servers, and most allow customers to use them. Since these servers are typically very nearby in a network sense, they can produce very clean results.

---

