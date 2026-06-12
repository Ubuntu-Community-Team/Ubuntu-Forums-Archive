---
title: "Opera process does not end"
date: 2009-12-28
forum: General Help
---

### Post by pveurshout on 2009-12-28
After installing Opera on my newly installed Karmic Koala, I started noticing error messages when trying to start Opera (after having closed it before):

> "It appears another Opera instance is using the same configuration directory because its lock file is active: ~/.opera//lock"

I found out that the process was never ended, and could only be ended by killing it ('end process' didn't do anything). The code under the column 'Waiting Channel' (in System Monitor) shows 'futex_wait_queue_me' if it happens that I close the Opera window and the process keeps running.

By the way, it does not show this behavior all the time, just once every -more or less- 3 times I use Opera. Does anyone know what this 'futex_wait_queue_me' indicates, and perhaps what I can do to fix it? Thanks!

---

### Post by stigb on 2010-01-24
i experience the same in Firefox. I no longer heard sound from YouTube videos, so I Ctrl-Q'ed firefox, waited a little while and started it again. I got a message saying there already was a Firefox process running needing to be terminated, and in System Monitor it had 'waiting channel' futex_wait_queue_me. So I needed to end the process myself before I could restart Firefox.

---

### Post by seriyPS on 2010-02-11
Try to disable Assistive Technologies (~$gnome-at-properties).
I do'nt now why, but this help me at the similar situation

---

### Post by pveurshout on 2010-03-12
> **seriyPS said:**
> Try to disable Assistive Technologies (~$gnome-at-properties).
I do'nt now why, but this help me at the similar situation

Sorry for the late reply. I don't have Assistive Technologies enabled (unfortunately).

---

### Post by BlueJaeger on 2010-03-12
> **stigb said:**
> i experience the same in Firefox. I no longer heard sound from YouTube videos, so I Ctrl-Q'ed firefox, waited a little while and started it again. I got a message saying there already was a Firefox process running needing to be terminated, and in System Monitor it had 'waiting channel' futex_wait_queue_me. So I needed to end the process myself before I could restart Firefox.

This also happens to me with Firefox, usually after it has been running for a few hours. I most often notice it after leaving my computer on all night with Firefox running.

Assistive Technologies is not enabled.

---

### Post by jcbodnar on 2010-04-06
I opened a bug for this:

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/552845](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/552845)

Please let the Ubuntu team know if this affects you.

---

