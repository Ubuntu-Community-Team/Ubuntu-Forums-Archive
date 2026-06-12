---
title: "TV Card stops working after installing nVidia drivers"
date: 2005-03-09
forum: General Help
---

### Post by martijntje on 2005-03-09
Like the title says. I have a TV card. Works perfectly under linux. Simply install xawtv and start watching. Doesn't even need configuration, because that is all done by my digital receiver.

However, after installing the nvidia drivers for my card, all i get is a blue screen.

The card is correctly detected and installed under /dev/video0
There's no video4linux there, but it used to work fine without.

Oh, i was doubting a bit about posting it to software or hardware support. Figured this is a software issue, so i post it here, feel free to move it.

---

### Post by martijntje on 2005-03-09
OK, i found it out myself. After installing, somehow, xawtv decided not to use the /dev/video0 resource by default anymore.

So now i start it with "xawtv -c /dev/video0" and it works again.

---

