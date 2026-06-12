---
title: "Can't get email to work"
date: 2011-08-30
forum: General Help
---

### Post by shelbyvision on 2011-08-30
I just did a full install of Ubuntu 10.04 on my wife's computer, and set up Thunderbird, it wouldn't work, then Evolution, and it won't work either. Thunderbird does nothing at all when I click on receive, and Evolution keeps asking for the POP password, which I fill in, and it rejects. My wife is very unhappy, and so am I. I've done new installs several times and never had a problem like this before. Any help would be appreciated.
Steve

---

### Post by seawolf167 on 2011-08-30
Why type of account are you attempting to access? (Yahoo, Hotmail, Gmail, etc.)
Do you have all your port numbers configured correctly to work with that email account?
Are you sure you are using the correct username/password?

---

### Post by shelbyvision on 2011-08-30
ISP email, [email]_____@embarqmail.com[/email]. It works on the ISP webpage, but not with Thunderbird or Evolution.

---

### Post by seawolf167 on 2011-08-30
Check your incoming and outgoing server settings, it looks like you should have the following:

Incoming mail: pop.centurylink.net (previous posts suggest to use pop.embarqmail.com for those email addresses)
Incoming port: 110

Outgoing mail: smtp.centurylink.net (previous posts suggest to use smtp.embarqmail.com for those email addresses)
Outgoing port: 25

See item #7 from [here ]("http://www.centurylink.net/files/centurylink/support/EmailPrograms/outlook_2007.php")for the above information source.

Looks like your username should be your full email address:  [email]xxxxxxx@embarqmail.com[/email]

---

### Post by Topsiho on 2011-08-30
when I have trouble like this it's "always" my user name. Some providers want the complete email address, and others only the part before @

Topsiho

---

### Post by seawolf167 on 2011-08-30
> **Topsiho said:**
> when I have trouble like this it's "always" my user name. Some providers want the complete email address, and others only the part before @

Haha, yea - this is always the first thing I check as well :P

---

### Post by shelbyvision on 2011-08-30
Thanks for the suggestions. Thunderbird is working now. I had originally used the wrong password. It needed to be closed and reopened with the right password. Evolution, on the other hand, still won't work, but my wife doesn't care about Evolution anyway, so I'm not going to worry about it.

---

### Post by seawolf167 on 2011-08-30
At least it was a nice and simple fix for Thunderbird :) If it is working now, please mark this thread as "Solved" under "Thread Tools"

---

