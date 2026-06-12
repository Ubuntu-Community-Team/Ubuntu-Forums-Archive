---
title: "firefox apparmor=&quot;DENIED&quot;"
date: 2010-10-14
forum: General Help
---

### Post by MountainX on 2010-10-14
I see a seemingly endless stream of  apparmor="DENIED" messages in my log from Firefox. Furthermore, I can't save files I download to the locations of my choice.

Can anyone tell me how to resolve this? All I know is that I need to edit /etc/appamor.d/usr.bin.firefox-4.0.apparmor. I do not know what to edit in that file or how to change it. 

Here are some examples from my log:

[15006.769069] type=1400 audit(999999.533:28): **apparmor="DENIED"** operation="open" parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}" name=XXX_REALLY_LONG_XXX pid=3503 comm="firefox-4.0-bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

[15112.077815] type=1400 audit(999999.834:41): **apparmor="DENIED" **operation="open" parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}" name=XXX_REALLY_LONG_XXX pid=3515 comm="firefox-4.0-bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000

[15129.784227] type=1400 audit(9999999.543:45): **apparmor="DENIED" **operation="mknod" parent=1 profile="/usr/lib/firefox-4.0b8pre/firefox{,*[^s][^h]}" name="/my/downloads/Software/ubuntu-10.10-dvd-amd64.iso" pid=2035 comm="firefox-4.0-bin" requested_mask="c" denied_mask="c" fsuid=1000 ouid=1000

---

