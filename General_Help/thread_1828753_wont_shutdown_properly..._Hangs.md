---
title: "wont shutdown properly... Hangs"
date: 2011-08-19
forum: General Help
---

### Post by jewfromdahood on 2011-08-19
Hi all... Everything runs great for my Ubuntu Linux 11.04 on my computer. But when I shut it down it never actually shuts down, the splash pops up... Then the buttons move, and it never actually shuts down until I press and hold the power button.

---

### Post by jfed on 2011-08-19
Try opening a terminal and typing

```
sudo shutdown -r now
```

when prompted for your password, enter it.

this worked for me in a similar situation

---

