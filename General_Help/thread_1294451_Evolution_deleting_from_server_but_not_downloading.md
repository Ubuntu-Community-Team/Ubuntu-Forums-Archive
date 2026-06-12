---
title: "Evolution deleting from server but not downloading"
date: 2009-10-18
forum: General Help
---

### Post by epee on 2009-10-18
A couple of times this week Evolution has deleted emails from my email server (POP) without downloading the emails.

The account is on a Ntlworld (Virgin Media) server, and I frequently check the email using webmail (on a Windows laptop), and then download to my desktop (Ubuntu 9.04, fully updated) machine in the evening. This has been working fine for over 2 years btw.

I did some checking this afternoon, and I could send myself email from my Gmail account, and checking it with webmail I could see the message in the inbox. Then I fire up Evolution, it checks the email - nothing new in the inbox. Go back to my webmail, and the message is gone.

I have now disabled the account in Evolution, because at this rate I could lose something important.:mad:

I wonder if anyone else has experienced anything like this. Is the problem with Evolution or Ntlworld/Virgin?

---

### Post by epee on 2009-10-23
<bump/>

Anyone? Is no-one else seeing problems like this with Evolution/Ntlworld?

---

### Post by plucky on 2009-10-23
> **epee said:**
> <bump/>

Anyone? Is no-one else seeing problems like this with Evolution/Ntlworld?

Check your **Junk** mail folder.This happened to me a while ago and under **Edit > Preferences > Mail Preferences** I had to untick the box that said "Check incoming messages for Junk".

Just a thought

Good Luck

---

### Post by epee on 2009-10-25
> **plucky said:**
> Check your **Junk** mail folder.This happened to me a while ago and under **Edit > Preferences > Mail Preferences** I had to untick the box that said "Check incoming messages for Junk".
Thanks for that suggestion. I checked the junk mail - Wasn't like there was loads of emails there that shouldn't have been. (There were only 2...)

Hmmm...

---

### Post by fancypiper on 2009-10-25
Did you configure it to use a local mailbox? Do you see anything in /var/mail?

---

### Post by epee on 2009-10-29
At some point the problem disappeared.

I don't think there had been any system updates, so I have to assume my email to Virgin tech support rattled someone's cage. Mind you, if it did, they didn't let me know - I'm still waiting for a reply.

Thanks for those that gave suggestions though.

---

