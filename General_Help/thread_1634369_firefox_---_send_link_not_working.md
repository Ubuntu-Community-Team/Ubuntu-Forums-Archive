---
title: "firefox --- send link not working"
date: 2010-11-30
forum: General Help
---

### Post by Silvernail on 2010-11-30
Ubuntu 10.4 -- all updates
Firefox 3.6.12
Thunderbird 3.0.10

File > Send link

Does not work.  It use to.

Is this a known issue with the latest updates?
Is there a workaround other than cut & paste?
Is it just me?

TIA
Dave

---

### Post by Silvernail on 2010-12-03
Does no response mean I'm the only one having this problem?

---

### Post by Silvernail on 2010-12-05
Turned out update manager or somebody listed 'thunderbird' on a different path than listed in 'firefox'.

Trace down your 'mailto' path. Be sure it leads to where your email client is installed.

---

### Post by namiller on 2010-12-06
I'm having this problem which I just noticed yesterday.  As I rarely find myself using the "mailto:" feature I can't say how long it's been a problem.

You gave fine advice, Silvernail; I'm only surprised I could follow it.  As an FYI for others, I found that I could get into Firefox Preferences (Edit/Preferences) and under the Applications tab scroll down to "mailto."  It was set at "Use Thunderbird (default)" but from the dropdown menu I chose "Use Other" and navigated to /usr/bin/thunderbird.  So far it works now.  Time will see if it works after restarting FF or if it will revert to previous behavior.  I'll try it and report back.

---

### Post by namiller on 2010-12-06
Just restarted FF, and things are working fine.  Joy and rapture are mine once more - ok, that was a bit of an exaggeration.

---

### Post by Silvernail on 2010-12-08
I got to the path a little differently:
```
dave@dave:~$ locate thunderbird | grep bin
**/usr/bin/thunderbird**[COLOR="Red"]This is what I was looking for.[/COLOR]
/usr/lib/thunderbird-3.0.10/thunderbird-bin
/usr/lib/thunderbird-3.0.10/modules/gloda/databind.js
dave@dave:~$ 

```
Cursor on top of the Firefox Tool Bar icon for Thunderbird, right click then right click 'properties.
Mine said,[COLOR="Red"]/usr/sbin/thunderbird %u[/COLOR]

I removed '/usr/sbin/'.

---

