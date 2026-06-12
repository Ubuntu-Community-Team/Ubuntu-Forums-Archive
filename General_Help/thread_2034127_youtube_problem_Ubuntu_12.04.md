---
title: "youtube problem Ubuntu 12.04"
date: 2012-07-27
forum: General Help
---

### Post by ExcitedCartoon on 2012-07-27
Hey everyone, I'm a new ubuntu user so please don't criticize or insult me. Usually, i try to find the answers myself but this time I've tried many things but non of them seem to work and it's driving me crazy.  I'm aware that flash is a problem but many seem to resolve their issues.

Here's my issue: When I turn my computer on and go to youtube i can see 2 maybe 3 videos. After that it never loads up the video, says, "An error occurred. Please try again later." and instead of the infamous green screen there's is static effect. Sometimes i can't even watch those 2 videos right after startup. This happens both in firefox and chromium

How can I solve it?

If this can help, here it is:
Ubuntu 12.04
AMD Athlon(tm) II P340 Dual-Core Processor
amd radeon hd 4250

If you need more info please reply. Thanks

---

### Post by Nixarter on 2012-07-27
I had this problem, too.  It's really annoying hahaha.

The issue comes from new versions of Firefox automatically opting-in to the HTML 5 trial at [www.youtube.com](www.youtube.com).

The easiest solution is to go to: [http://www.youtube.com/html5](http://www.youtube.com/html5)

Go down until you see the bit about HTML5, and then leave the trial.  Restart your browser and it will force flash instead of html5.

Alternatively, you can figure out which part of your setup is not compatible with HTML5 and upgrade it to get HTML5 to work properly... but that's just an option.  Flash is fine with me.

---

### Post by ExcitedCartoon on 2012-07-28
well the html5 option has always been off and still cant watch videos.

---

### Post by vipulkumar7 on 2012-07-28
just install flash player it will work and install all plugine:)

---

### Post by ExcitedCartoon on 2012-08-01
Flash is already installed. i also have ubuntu restricted extras

it still doesn't work

---

### Post by Frogs Hair on 2012-08-01
Do you clear your browser caches occasionally ? The janitor in Ubuntu Tweak works well for this . [http://www.webupd8.org/2012/05/ubuntu-tweak-071-available-for-download.html](http://www.webupd8.org/2012/05/ubuntu-tweak-071-available-for-download.html)

---

### Post by webmadman on 2012-09-28
Was banging my head against this one for a bit- figured out that it was using https that was mucking me up (I have the HTTPS Everywhere plugin for my laptop). Once I was using regular http all was good in YouTube world...

Thought I'd post this reply for others stumbling on this issue.

---

