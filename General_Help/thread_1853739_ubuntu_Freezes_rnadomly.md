---
title: "ubuntu Freezes rnadomly"
date: 2011-10-02
forum: General Help
---

### Post by matta89 on 2011-10-02
Hello Everyone,

I love ubuntu, but I'm having a small issue... ubuntu is freezing up on me ... sometimes a few times a week, sometimes a few times a day. I can't quite figure out what the issue is.

My laptop is a Satellite M55-s331

the error its giving in syslog is this:

-
Oct  2 19:02:50 matt-Satellite-M55 kernel: [22412.432168] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Oct  2 19:02:50 matt-Satellite-M55 kernel: [22412.433591] [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -11 (awaiting 194333 at 194331, next 194334)
Oct  2 19:02:50 matt-Satellite-M55 kernel: [22412.433736] [drm:i915_reset] *ERROR* Failed to reset chip.
Oct  2 19:03:01 matt-Satellite-M55 wpa_supplicant[548]: WPA: Group rekeying completed with d8:5d:4c:a4:59:04 [GTK=TKIP]
-

I'm able to restart via the terminal. Any idea on what the issue is? I can seem to connect it to anything I'm doing. Its happened when writing a document, watching a youtube video or simply nothing. Doesn't seem to have a stable pattern. 

If anyone can help me out... I'd greatly appreciate it!

Matt

---

### Post by 2F4U on 2011-10-03
The term i915 points to a problem with the graphics driver and I found this bug report

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507504](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/507504)

What version of Ubuntu are you running?

---

### Post by matta89 on 2011-10-03
Thank you, looking that over now. I'm running 11.04, classic desktop

---

