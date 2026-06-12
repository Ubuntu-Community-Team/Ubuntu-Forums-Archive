---
title: "Why does &quot;shut down&quot; now require confirmation?"
date: 2010-05-29
forum: General Help
---

### Post by RobertL on 2010-05-29
Since I upgraded to 10.04 Lucid the Shut Down applet puts up a window titled "Shut Down" that has two buttons "Cancel" and "Shut Down".  In 9.04 this confirmation window didn't appear. How can I make "Shut Down" skip the confirmation and shut down directly? I've looked around for a preference item about that a couple of times but didn't find it.

---

### Post by howefield on 2010-05-29
> **RobertL said:**
> How can I make "Shut Down" skip the confirmation and shut down directly?

Open a run dialogue window, (press Alt + F2 keys) and type 

> gconf-editor

Navigate the Configuration editor to apps > indicator-session and place a check against "suppress_logout_restart_shutdown.

---

### Post by RobertL on 2010-05-29
Wow! What a fast answer!  And correct. I just tried it and it worked.

I must say that's a pretty obscure way to provide a preference. Only someone who knows what it means in advance will be able to use it.

---

### Post by Splat_NJ on 2010-11-23
I tried this with 10.10 and it doesn't work for me. Still getting the menu whenever I click the power icon.

---

