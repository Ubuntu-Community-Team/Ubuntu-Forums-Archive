---
title: "BEEP! for new emails in Thunderbird :)"
date: 2011-01-12
forum: General Help
---

### Post by Splat_NJ on 2011-01-12
Folks, all I wanted was a "beep!" when new emails arrived in Thunderbird.  There is a little program by Johnath that allows you to get your "beep!" back and also customize it. You can get the latest version from his site [here]("http://johnath.com/beep/") or sudo apt-get install beep which doesn't install the latest version but works for me.

This is how you get beeped for new emails in Thunderbird.  Install [Mailbox Alert]("https://addons.mozilla.org/en-us/thunderbird/addon/2610/")  .  Once installed you then need to set the alert to the beep command. Under "Tools" in  Thunderbird select "Mailbox Alert Preferences".  Select the "Execute a  command" option and enter "/usr/bin/beep"(or wherever you installed "beep" to). If you have child(sub)  folders that you want to be alerted when new mail arrives in them select the "Alert for child folders (if they ....." option. Finally, hit  the "Test these settings" button to test the beep. If you get a beep  you know it's working so hit the OK  button and you're good to go.

---

### Post by mercvrivs on 2011-12-28
Sorry for the offtopic, but I think that you can read the subject/sender/etc aloud, as well, using some voice synthetizer like espeak passing the variables (i dunno if the the addon has variables as I use alpine) via pipe |.

I just would like to share the idea with the mankind. 8)

ps: something like:

> echo 'You have new mail from %sender' | espeak

---

### Post by Splat_NJ on 2011-12-28
> **mercvrivs said:**
> Sorry for the offtopic, but I think that you can read the subject/sender/etc aloud, as well, using some voice synthetizer like espeak passing the variables (i dunno if the the addon has variables as I use alpine) via pipe |.

Good idea, but that would mean your external speakers would be on all the time. Mine are usually off, which is why I wanted the PC's internal speaker to emit a sound upon new email arrivals.

---

### Post by pretty_whistle on 2011-12-28
I too have a custom sound for Thunderbird.  It works great!
:)

---

