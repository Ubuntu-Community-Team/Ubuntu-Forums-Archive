---
title: "Chromium Memory Leak &amp; futex_wait_queue_me Problem"
date: 2011-04-03
forum: General Help
---

### Post by eitsuop on 2011-04-03
When I first installed Ubuntu & Chromium, all its processes in System Monitor were in the poll_schedule_timeout waiting channel. Recently, however, extra processes in the futex_wait_queue_me waiting channel have appeared.

At first this was hardly a problem, but whenever I saw them come up I would close down Chromium and reopen it. They'd be gone, and not come back for some time. Each of these processes took ~10-30MB of RAM.

Now, the big problem comes in. Today, I noticed a TON of these processes. I shut down Chromium, reopened it, and they were still there! Again, not *that* big of a problem. However, I soon noticed a huge lag in my page load time, and looked at System Monitor again.

Now, Chromium seems to have a terrible memory leak. One of the futex processes starts to use more memory every 5 seconds or so, going up in 2MB increments, seemingly indefinitely.

What can I do to fix/prevent this?

Screenshot: [http://bit.ly/go8ZtQ](http://bit.ly/go8ZtQ)
This is not the highest I've caught it, either.

---

### Post by techunit on 2011-04-03
Everything in chromium is sandboxed! so everything has an independant process so if one thing fails the whole thing won't.

---

### Post by eitsuop on 2011-04-04
> **techunit said:**
> Everything in chromium is sandboxed! so everything has an independant process so if one thing fails the whole thing won't.

I know this, but these futex processes are a recent occurrance and are starting to inhibit my ability to use the browser. I'm going to have to use FF... gag.

---

### Post by eitsuop on 2011-04-06
Seriously, though... this has gotten so bad that I can't even use Chromium anymore!

Does ANYONE have a solution?

---

### Post by techunit on 2011-04-06
Where are you installing chromium from? are you running the latest stable or are you running tye version in the repo? you might consider installing the beta which I have expierenced only going as high as 900MBs of RAM at its worse. though it seams to have gotten much better recently.

IDK you could try Chrome.

Let me know what you figure out please.

---

