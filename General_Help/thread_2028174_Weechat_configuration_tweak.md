---
title: "Weechat configuration tweak"
date: 2012-07-17
forum: General Help
---

### Post by StormeRider on 2012-07-17
I'm wondering if there's a way to tell Weechat to ignore notifications in the status bar for channel joins/parts. I watch the weechat window inside of tmux, and I'd like the indicator to pop when someone says something, not the inevitable spam of people bouncing in and out of channels (or netsplits).

I know it keeps track of things separately, because it will show activity like "[Act: X(Y,Z)]", and Y and Z are separated between real messages and bouncing. I'm just not sure how to tell it to completely ignore the bouncing.

I can pastebinit any files you want to see for this, but it's currently a pretty vanilla config (outside of irc.conf and a slight tweak to weechat.conf to remove the time from the status bar since it's already shown on the tmux status bar, and just serves to constantly flag the weechat window as active in tmux).

It's a minor thing, but it would help smooth out my user experience if it were possible to achieve. Thanks in advance for any help.

---

### Post by matt_symes on 2012-07-17
Hi

[http://www.weechat.org/files/doc/weechat_faq.en.html](http://www.weechat.org/files/doc/weechat_faq.en.html)

The section 6.2 How can i filter join/part/quite messages in IRC filter.

Nice move using weechat :) It's what i use.

Kind regards

---

### Post by StormeRider on 2012-07-17
Interesting. I was more looking for a way to ignore the notifications for other windows, but I guess this would prevent join/parts from flagging the current window as active in tmux due to join/parts as well.

I'm not sure if that's exactly what I want, but I'll have to play around with it and see. Thanks for the heads up!

---

