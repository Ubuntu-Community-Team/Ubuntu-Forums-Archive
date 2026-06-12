---
title: "Real mess with outgoing mails using Evolution"
date: 2010-12-17
forum: General Help
---

### Post by IronArjen on 2010-12-17
I have used Evolution for 5 years with no problems but it really makes a mess now. It keeps on copying or moving already sent messages to my Outbox, hence it keeps on sending mails again and again (and again).

Is there a bug I should fix?
Is there a (better) alternative for evolution?

I already reinstalled evolution, no effect.
My mail is Gmail.

---

### Post by BlueSpecial on 2010-12-17
I prefer using Thunderbird. Never really liked Evolution.

---

### Post by dcstar on 2010-12-17
> **IronArjen said:**
> I have used Evolution for 5 years with no problems but it really makes a mess now. It keeps on copying or moving already sent messages to my Outbox, hence it keeps on sending mails again and again (and again).

Is there a bug I should fix?
Is there a (better) alternative for evolution?

I already reinstalled evolution, no effect.
My mail is Gmail.

Messages only stay in the Outbox if Evolution does not believe they have actually been sent correctly. You could have connectivity problems to your mail service or your profile is corrupt.

Create a fresh Evolution profile by:[LIST=1]
[*]Close Evolution
[*]Rename the (hidden) .evolution folder.
[*]Restart Evolution and set up your e-mail account again.
[/LIST]
If sending e-mails now works correctly, you can shut Evolution down and then copy all of your old e-mails etc from the renamed profile to the new .evolution profile.

---

