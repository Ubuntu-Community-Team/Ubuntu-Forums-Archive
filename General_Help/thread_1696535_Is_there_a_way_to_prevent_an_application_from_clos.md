---
title: "Is there a way to prevent an application from closing/make it persistent?"
date: 2011-02-27
forum: General Help
---

### Post by ahorriblemess on 2011-02-27
I'm using Ubuntu on an old 9" Eee PC and I want to prevent Chromium from closing. I don't want to simply not close Chromium, because I do it out of habit. I would like to know if there's a way to keep the program open, or have it reopen when it's (accidentally) closed.

Thanks for your time.

PS- Chrome OS builds I've tried don't boot when installed on the SSD. I'm assuming it's a driver issue. Also, I like the option of having a complete operating system if I need it. I do not want to use Jolicloud either.

---

### Post by Krytarik on 2011-02-27
I know it from my own experience, you simply want to close the (last) tab, and instead of blanking Chromium quits entirely. ;-)

You can use those extension to improve the situation a bit, but it won't work on build-in pages:
[https://chrome.google.com/extensions/detail/dlopnnfglheodcopccdllffcijjeenkj](https://chrome.google.com/extensions/detail/dlopnnfglheodcopccdllffcijjeenkj)

---

### Post by ahorriblemess on 2011-02-27
Thank you for the suggestion, but that doesn't work. I wish I understood code more, I could possible look through the Chromium OS source code and find out how the browser stays open. 

Actually I might try that, even though I have no idea what I'm looking at.

---

### Post by Krytarik on 2011-02-27
I just before searched for it, and tested it. But, like I said, it doesn't work on build-in pages, meaning for example the "New Tab" page with the "fast dialer", or the extensions pages.

---

### Post by ahorriblemess on 2011-02-27
Yes, I know. I tried it on this page actually. Not a big deal, and I appreciate that you tried to help.

---

### Post by Krytarik on 2011-02-27
> **ahorriblemess said:**
> Yes, I know. I tried it on this page actually. Not a big deal, and I appreciate that you tried to help.
Ah, then you close it definitely the other way, with the window's "X", that seems not to be preventable. ;-)

---

### Post by Krytarik on 2011-02-27
If the previously stated is true, let me ask you another question: Do you use Compiz, or are you running the Netbook Edition, on which it doesn't work?

Background: There is a way to avoid the unintended closure and I tested it, but it requires
- to set the use of the system's window decoration
- removal of those by Compiz to keep the upper part of Chromium slim (you can make it completely non-closable by another option if you need to)

---

