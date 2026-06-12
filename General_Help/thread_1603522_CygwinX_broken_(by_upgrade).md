---
title: "Cygwin/X broken (by upgrade?)"
date: 2010-10-22
forum: General Help
---

### Post by jwbrase on 2010-10-22
I've been using PuTTY and Cygwin/X to access my Ubuntu laptop from our family XP desktop. I had had everything set up right, with X-tunneling working pretty much flawlessly, and then upgraded Cygwin to from version 1.5 to 1.7.

I'd mostly been doing command line stuff through PuTTY, so it took me a while to notice any problems, but today I tried tunneling some X Programs and most of them died. As I'd also upgraded from Jaunty to Lucid in the interim, I at first suspected that that upgrade had broken something, but I subsequently tried running various X programs locally on the Windows machine and found that local programs were having problems as well.

If I have a console open, I'll get various error messages, the most common seems to be "Fatal IO error 11 (Resource temporarily unavailable) on X server $DISPLAY".

I Googled that error and found a suggestion that the Cygwin command "rebaseall" might help, but have had no luck with that.

Another Google result turned up somebody who suspected that his Cygwin/X Start menu items may still be linking to v1.5 scripts that don't work with 1.7 and was asking for help correcting that issue (if that was in fact his problem, it may well be mine), but he seems to have gotten only one reply from the mailing list he was asking, which was absolutely no help at all.

Can anybody suggest how I might be able to get X working again under Cygwin?

---

