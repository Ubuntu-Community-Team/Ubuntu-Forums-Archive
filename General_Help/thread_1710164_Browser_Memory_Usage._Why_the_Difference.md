---
title: "Browser Memory Usage. Why the Difference?"
date: 2011-03-19
forum: General Help
---

### Post by cottfcfan on 2011-03-19
At the moment Chromium is my preferred Browser of choice, but there's a massive difference in memory usage. While on the Home page I observe this:

Chromium Mem. Usage 450-500mb
Opera    Mem. Usage 100-120mb
Firefox  Mem. Usage 60-90mb

Why does Chromium use so much memory, particularly when Firefox has twice the extensions?

---

### Post by gradinaruvasile on 2011-03-19
Because every browser is made in differeent ways. 
Chromium uses separate threads for each tab (+1 for control +1 for plugins) so it has some overhead. But It has very good memory management because if a tab is closed that is effectively removed from memory unlike in other browsers where sometimes memory usage builds up in time.

What are the circumstances of this test? Same pages/etc? Do not test the browsers right after start with saved session, you might have cached elements not loaded in memory, etc.
Instead open an empty session and load each page, make sure you emptied the cache before.

---

### Post by cottfcfan on 2011-03-19
Hi,

I opened all 3 browsers on the same web page and left for about 60 seconds. Ive just cleared the cache and retested and have roughly the same results.
Its not a problem and i have the spare memory, it's just that using 4 times the resources of Firefox seems a bit excessive!

---

### Post by gradinaruvasile on 2011-03-19
What page is that?

---

### Post by cottfcfan on 2011-03-19
Just the google home page:
[http://www.google.co.uk/](http://www.google.co.uk/)

---

### Post by gradinaruvasile on 2011-03-19
And that accounts for 400 MB+ on Chromium?
I have 67+46+29=142 MB.

Do a test with 5-6 tabs open with the same pages. Loading only one static page does not reflect the true web page handling of a browser.

---

### Post by cottfcfan on 2011-03-19
With just my home page open my usage is this:
78+78+42+36+35+30+31+30+29+20+10
With 6 tabs open on the same page usage is:
89+64+64+63+40+36+39+36+31+29+20
Not a great deal of difference really.

---

### Post by gradinaruvasile on 2011-03-19
Close Chromium and check if it still runs. You might have some chrome processes there that are noy stopped.

---

### Post by cottfcfan on 2011-03-19
According to system monitor all processes close when i close chromium.
Like i said its no big deal, just a query.

---

### Post by idoitprone on 2011-03-20
[http://blog.chromium.org/2008/09/google-chrome-memory-usage-good-and-bad.html](http://blog.chromium.org/2008/09/google-chrome-memory-usage-good-and-bad.html)

Who cares about memory these days. It so cheap, anyways. Chromium does manage memory well, which means your not wasting a bit of ram and it is faster too. When their sandbox models matures, you wont experience random crashes. I rather have those feature than free memory

we should abide by the old unix principle; unused ram is wasted ram. Things that windows try to implement but screwed up with the thing called superfetch

---

