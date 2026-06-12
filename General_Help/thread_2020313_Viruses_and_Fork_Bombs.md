---
title: "Viruses and Fork Bombs"
date: 2012-07-08
forum: General Help
---

### Post by nankura on 2012-07-08
hey guys

i was just wondering how viruses in linux work and fork bombs and how to stop one if it happens and how to prevent it happening. or if its nothing to worry about

---

### Post by carl4926 on 2012-07-08
Is this a trick question?
What's a Virus anyway?

---

### Post by Habitual on 2012-07-08
Using a mail client to download suspect email attachments over the POP[3] Protocol is a risk. You do not risk being infected but you can risk spreading infections, if such attachments are infected.

Linux + email in IMAP and you're relatively safe from the above scenario.

[http://en.wikipedia.org/wiki/Fork_bomb](http://en.wikipedia.org/wiki/Fork_bomb)

Disclaimer, What is 'impossible'  today, is not impossible tomorrow. Given enough time and resources, Linux users may not remain safe for very long.

HTH.

Edit: And this smacks of Low Hanging Fruit.

---

### Post by stderr on 2012-07-08
The usual security rules apply: don't go clicking on things randomly. Exercise intelligence when dealing with attachments & websites. Keep your system up-to-date. 

As for your specific question, *viruses* per se don't tend to exist in the Linux world. The ones that have existed have mainly been proof of concepts. That's not to say they *can't* exist, but just that it's a tougher platform for many reasons.

As for fork bombs, these are just DOS toys. No attacker would use a fork bomb - attackers' motives are usually the direct opposite of taking a system down. Attackers want to keep systems up, hide their code, and maintain access serupticiously. The only risk you face from fork bombs is from your mates.

---

