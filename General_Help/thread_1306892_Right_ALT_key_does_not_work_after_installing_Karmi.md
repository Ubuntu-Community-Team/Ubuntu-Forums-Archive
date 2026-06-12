---
title: "Right ALT key does not work after installing Karmic from Alternate CD"
date: 2009-10-30
forum: General Help
---

### Post by sefs on 2009-10-30
Right ALT key is disabled/or does not work after installing karmic from Alternate CD.  Anyone else experiencing this?

There was some fix floating around about commenting out a line in /etc/default/console-setup  but that did not work.

Thanks.

---

### Post by Johannes Eva on 2009-11-18
Same problem - but I installed 9.04 from the live CD.
Maybe related to:
[https://bugs.launchpad.net/ubuntu/+bug/382473](https://bugs.launchpad.net/ubuntu/+bug/382473)
or:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226676](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226676)

---

### Post by sefs on 2009-11-22
This solved it for me.

1) System -> Preferences -> Keyboard

2) Layouts tab

3) Layouts Options... button

4) Expand "Key(s) to change Layout"

5) Uncheck "both alt keys together"

Then both my alt keys now work as expected.

I picked up that tip from someone who made a post to a bug listing I had made on launchpad.net.

---

