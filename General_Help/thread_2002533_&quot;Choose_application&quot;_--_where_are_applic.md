---
title: "&quot;Choose application&quot; -- where are applications located?"
date: 2012-06-12
forum: General Help
---

### Post by Catlike on 2012-06-12
I want to subscribe to an RSS feed using Akregator, a news feed program I got from the Ubuntu Software Center. When I click on the blog page "Subscribe to RSS" link, I get a window with an undesired default choice and a "Choose application..." choice. When I click "Choose application", a window opens in the Pictures folder, and I can path around to find the Akregator application. But -- where is it? I cannot find it anywhere, not in /[Me]/bin nor elsewhere. 
Where are applications hidden in my Ubuntu file system?!
Thank you.

---

### Post by mikewhatever on 2012-06-12
You can find out where an executable is by using 'which', for example, **which akregator**. Most of the executables would be in /usr/bin (where the applications are is irrelevant).

---

### Post by Catlike on 2012-06-15
Hmm... strange. I did the "which akregator" and it did indeed answer with "/usr/bin" . However, I find no executable -- in fact, nothing at all -- with the name "akregator" nor anything like it! Why would it say it is there if it is not? Or is it hidden somehow?
Thank you again.

---

### Post by SDX0 on 2012-06-15
Does "cat /usr/share/applications/akregator.desktop | grep Exec" return anything useful?

Edit: Sorry, this wouldn't actually help at all.  I forgot only my own desktop files have the full path to the executable.

---

### Post by Catlike on 2012-06-15
@ SDXO -- Well, thank you for looking at it. 
I'm still flummoxed. Akregator boots up (via the "dashboard" thing). And the "which akregator" still says "/usr/bin" .  But -- no can find the executable!

---

### Post by Catlike on 2012-06-15
> **Catlike said:**
> @ SDXO -- Well, thank you for looking at it. 
I'm still flummoxed. Akregator boots up (via the "dashboard" thing). And the "which akregator" still says "/usr/bin" .  But -- no can find the executable!

Solved, I think -- I just looked again and there it is, where I did not see it before. I must have done something subtly different.

Thanks to all you helpful people!

---

