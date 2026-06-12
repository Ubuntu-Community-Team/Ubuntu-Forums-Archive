---
title: "Problem with xine-ui since dapper upgrade"
date: 2006-06-05
forum: General Help
---

### Post by dcymbal on 2006-06-05
Hi,

xine-ui has been my preferred video player and has been working fine for me with warty and breezy.  This weekend I upgraded to dapper and things appeared to go smoothly but I am now seeing an issue with xine-ui that I haven't seen before and wondered if anyone else is seeing it:  playback (tried several different video types) will hiccup every 10 seconds or so for a couple seconds and then resume.  By hiccup I mean that the entire screen will blank out (almost as if you pulled the video cable) for a couple seconds, and then the desktop reappears and the vide will play for 10 or so seconds ok and then the hiccup.  This cycle continues.  I tried using the xine engine with some of the other frontends and they did not seem to experience this problem, so I assumed the engine was alright and the issue is specific to xine-ui.  Anybody else seeing this or any ideas on how to further debug?

Thanks.

dc

---

### Post by blackjack6.21.91 on 2006-06-05
Try upgrading it and it's dependencies

---

### Post by steve.horsley on 2006-06-05
I did a fresh install of Dapper over the weekend. I installed codecs and checked that xine could still play mpegs and DVDs. No problems here. So there's not a generic problem with xine in Dapper. Maybe you should check that DMA is enabled on the appropriate drive?

I assume that the command xine comes from the xine-ui package, because it's xine-ui that I installed.

---

