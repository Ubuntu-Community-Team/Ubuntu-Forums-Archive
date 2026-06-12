---
title: "Can't boot Ubuntu with Graphics mode"
date: 2011-04-09
forum: General Help
---

### Post by Andy Chang on 2011-04-09
Hi All,
 
In these days I install ubuntu 9.10 64bit on several notebook (**Intel + AMD Switchable Graphics, NVIDIA Optimus Hybrid graphics**), but the same problem is it can't boot ubuntu with graphic mode. I only can install it with text mode, and after installation, it still boot with text mode. I tried to execute startx, but failed to switch to graphics mode. I didn't see this issue with some notebooks with ATI/NVIDIA graphics, so I think this issue may relate with VBIOS VBE mode settings.
But I can't find root cause and have no idea on how to fix it.
Anyone can help me ?
Thanks.
 
When I try to execute "startx" under the text mode, some error information appears as below.
 
(EE) open /dev/fb0: No such file or directory
(EE) No devices detected.
Fatal server error:
no screens found

---

### Post by TeoBigusGeekus on 2011-04-09
Instead of trying with 9.10, try with 10.04 or 10.10, which are newer versions; perhaps they'll provide better support for your graphics card.

---

### Post by Andy Chang on 2011-04-10
> **TeoBigusGeekus said:**
> Instead of trying with 9.10, try with 10.04 or 10.10, which are newer versions; perhaps they'll provide better support for your graphics card.
 The problem is I must use 9.10 64bit version for some special reason.

---

### Post by Andy Chang on 2011-06-25
Now my issue was solved. After trying 10.04 and later verison, the issue disappear. I think it was 9.10 limitation. So somebody who want to install Ubuntu on Switchable Graphics notebook (AMD PowerXpress or NVIDIA Optimus tech.) DO NOT install 9.10 or previous version, or you will not boot into graphics mode (even when installing).

---

