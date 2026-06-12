---
title: "Kernel: 2.6.38, since upgrading to it I'm seeing issues patching."
date: 2011-09-10
forum: General Help
---

### Post by ZhiZaki on 2011-09-10
So I've had more time at home and in the office to play with ubuntu and lubuntu and I've started to notice something weird about the 2.6.38-11 kernel release. I have 3 separate systems I've upgraded from 2.6.38-8 to 2.6.38-11 and all the systems have problems opening files while patching.... actually, I stopped and reinstalled lubuntu before submitting this thread and it seems that the issue exists with 2.6.38-8 as well, so perhaps something changed in the `build-essential` package.... 

I've attached the strace I ran on the following command:

zhizaki@zhidesktop:/usr/local/src/compat-wireless-2.6.38.2-2-ns$ sudo strace -o strace.log patch -p1 mac80211.compat08082009.wl_frag+ack_v1.patch

The issue occurs with all patches I've attempted to apply to compat-wireless, but I have tried to patch any other source code at this time.

---

