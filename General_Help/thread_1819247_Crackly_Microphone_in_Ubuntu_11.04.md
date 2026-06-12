---
title: "Crackly Microphone in Ubuntu 11.04"
date: 2011-08-05
forum: General Help
---

### Post by Joseph Schwenker on 2011-08-05
I just did a fresh install of Ubuntu 11.04 onto a new hard drive I got, and I've been having a big problem with my microphone. Output from my microphone is crackly and barely understandable. I didn't have this problem with Ubuntu 10.10, so I'm sure it's not my microphone. An audio recording of the crackling is attached. How can I fix this?

---

### Post by Joseph Schwenker on 2011-08-05
Just went on #ubuntu on freenode and they told me to adjust my alsamixer levels, which can be accessed from the terminal by typing ```
alsamixer
```. I turned down Front Microphone Boost, and my quality was suddenly a lot better! Problem solved.

---

