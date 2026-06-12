---
title: "Is TraceMonkey used in 64-bit versions of Firefox?"
date: 2010-04-15
forum: General Help
---

### Post by mgol on 2010-04-15
I've from different sources that the TraceMonkey JS engine is available:
1) in 32-bit Fx 3.5+ and 64-bit Fx 3.6+
2) only in 32-bit Fx 3.5+ (and 64-bit nigthly builds)
3) in both 32- and 64-bit Fx 3.5+
etc. I've heard that to run TM one has to have the entry javascript.options.jit.content set to true - I have this entry and it is set to true by default (and I use 64-bit Fx 3.5).

I'm confused - what's the truth, finally?

---

### Post by lovinglinux on 2010-04-15
[https://wiki.mozilla.org/JavaScript:TraceMonkey](https://wiki.mozilla.org/JavaScript:TraceMonkey)

> TraceMonkey is currently available and enabled by default in stable 32-bit Firefox 3.5+ and nightly builds. If you want to modify the types of JavaScript that are executed using TraceMonkey:

    * open a new tab;
    * type “about:config” and hit enter;
    * read the warning and heed its wisdom;
    * enter “jit” in the filter field;
    * change the value of “javascript.options.jit.content” to enable (true) and disable (false) TraceMonkey for JavaScript in Web content;
    * change the value of “javascript.options.jit.chrome” to enable (true) and disable (false) TraceMonkey for JavaScript in XUL/chrome.

---

### Post by mgol on 2010-04-15
> **lovinglinux said:**
> [https://wiki.mozilla.org/JavaScript:TraceMonkey](https://wiki.mozilla.org/JavaScript:TraceMonkey)

I do know this page. But it doesn't answer my question - why do I have those entries in about:config although I use 64-bit Firefox 3.5?

---

### Post by lovinglinux on 2010-04-15
> **mgol said:**
> I do know this page. But it doesn't answer my question - why do I have those entries in about:config although I use 64-bit Firefox 3.5?

Because there is no official 64bit version builds of Firefox, so Ubuntu developers need to grab the 64bit versions from the nightly repository.

---

