---
title: "modem-manager signal 15 + video?"
date: 2010-08-03
forum: General Help
---

### Post by ajlain on 2010-08-03
I am running Karmic on an old IBM thinkpad (yes IBM) Z60t going on a solid year now and am perplexed at this new problem that has arisen. My laptop has picked up an annoying habit of shutting down anytime a video is playing. It doesn't matter how long usually but before it happens the video and sound jump and then poof I get the shutdown logo and just before it shuts off for good the prompt tells me that "modem-manager caught signal 15: shutting down". Now I have looked online in the Ubuntu bug list and found this same signal but none of the bugs have anything to do with video. I am suspecting my video chip is getting too hot, but I honestly have no idea where to even begin looking to solve this. If I need more hardware specifics listed here let me know. thanks.

---

### Post by prodigy_ on 2010-08-03
Signal 15 is SIGTERM, which is sent to all apps (asking them to quit nicely) **after** a shutdown has been initiated. So this log entry is irrelevant and you may ignore it.

You mentioned that the laptop is old. Have you ever cleaned it? If there's too much dust inside, it can choke ventilation and cause overheating.

---

### Post by ajlain on 2010-08-03
that seems much easier than the ridiculous software problem I was imagining. I will do just that and see what happens, thanks.

---

