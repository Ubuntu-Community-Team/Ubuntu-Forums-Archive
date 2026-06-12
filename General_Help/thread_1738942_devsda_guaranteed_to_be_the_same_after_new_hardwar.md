---
title: "/dev/sda guaranteed to be the same after new hardware plugin"
date: 2011-04-25
forum: General Help
---

### Post by ankenyr on 2011-04-25
Hello everyone,
I was needing to use dd to copy a hard drive from one computer to another the other day. The computer was launched from a live cd and looking in /dev/ i saw there was the main hard drive sda. There was nothing else in there. After i plugged in a external hard drive i checked /dev again and sdb came up. I did the dd from sda to sdb hoping to copy the computer to the external. The thing is that it did the opposite. I am wondering if this is normal. Should I have any expectation that the information in /dev before i plug in a new external will be the same?

---

