---
title: "ethtool ioctl's"
date: 2012-03-29
forum: General Help
---

### Post by the red ninja on 2012-03-29
Hi all,

Just a general question:
I'm writing some sort of mini driver for verification purposes over linux (never mind the kernel and stuff...).
I'm trying to set and get the steering rules (ntuple's)
Anyone has any experience with the following ethtool commands:
ETHTOOL_SRXNTUPLE
ETHTOOL_GRXNTUPLE

using ioctls?

The get command is deprecated... Anyone has any idea how to use the set command? Or any other way for the get info on rules?
That's the first time I'm dealing with ethtool ioctl's, and they don't seem too user-friendly to me... :(

Roy

---

