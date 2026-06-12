---
title: "KABOOM! Hard freeze followed by GDM breakage."
date: 2006-06-06
forum: General Help
---

### Post by musicinmybrain on 2006-06-06
So I was using krdc on my Inspiron 8600 today when I experienced a hard freeze. That is, this wasn't just a single-program crash; while I could still move the cursor, nothing else worked. Clicking on things had no effect, keystrokes had no effect, I couldn't Ctrl+Alt+F1 to another terminal, I couldn't Ctrl+Alt+Backspace, and pushing the power button to initiate shutdown had no effect.

I eventually just held in the power button until the computer turned off. Experiencing a crash that went beyond userland was a surprise, but the real problems came when I turned the computer back on: the boot sequence worked fine until it came time to start gdm; this failed and I was dumped at the console, where I could log in to tty1 through tty6 with no trouble.

I tried sudo /etc/init.d/gdm start, which resulted in a [fail]. I've poked around a little (haven't had much time) but I'm not sure what's broken here, and while I'm pretty comfortable at the command line, I'm not sure where to start looking for this particular problem. Is there anyone out there who has experienced a similar issue or has an idea of how I could try to diagnose and fix the problem?

**Edit:** Looks like nobody has any ideas. It's kind of hard to track a problem down without any error messages. Oh, well. The only thing I can think of, drastic as it is, is to do a clean reinstall. It's frustrating because I'm sure there's an easier way to fix this problem, if I could only figure out the actual cause. I'll probably do the reinstall this evening.

**Edit:** A reinstall cleaned things up, but I really wish I knew what had happened.

---

