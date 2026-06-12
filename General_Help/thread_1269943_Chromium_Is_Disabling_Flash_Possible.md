---
title: "Chromium: Is Disabling Flash Possible?"
date: 2009-09-18
forum: General Help
---

### Post by DirtDawg on 2009-09-18
The title says it all, I would like to disable Flash in Chromium, but can't figure out how.

I checked /usr/lib/chromium-browser/plugins/ for a file I could rename or delete, but there's nothing. I also tried entering 'about:config' in the address bar, but that doesn't work.

My good friend Googley McGoogle is also little help. Most people want to enable Flash, but there's no information about disabling it that I can find.

Does anyone know what else I could try? Thanks.

---

### Post by falconindy on 2009-09-18
Running Chromium without the --enable-plugins flag should prevent flash from loading.

---

### Post by DirtDawg on 2009-09-18
> **falconindy said:**
> Running Chromium without the --enable-plugins flag should prevent flash from loading.

Thanks, but it is already being run without that option. At some point in the last few builds, Flash seems to have been enabled by default.

---

### Post by falconindy on 2009-09-18
Mmm... they're getting confident, I suppose. The latest build has an --enable-printing flag.

FWIW, you're able to right click on the title bar, open the task manager for Chromium and kill the flash process. That's a poor solution though. I found [this page](http://www.chromeplugins.org/google/chrome-tips-tricks/disable-extensions-chromium-8316.html) which is dated quite recently (9/8/09), but the --show-extensions-on-top option didn't work at all for me.

---

### Post by falconindy on 2009-09-19
So how about this... using --disable-extensions works as advertised. Or, I should at least qualify this and say that it works in 4.0.212.0 (build 26556).

---

### Post by DirtDawg on 2009-09-20
> **falconindy said:**
> So how about this... using --disable-extensions works as advertised. Or, I should at least qualify this and say that it works in 4.0.212.0 (build 26556).

This actually doesn't work for me using the same build. I'm not sure why it wouldn't if it worked for you. Strange.

I've also been playing with some user scripts as well that are supposed block Flash. So far, they only seem to break the entire page.

So is the risk of using developer's alpha software, I suppose.

Thanks again for the suggestions. I'll post if I find a solution.

---

