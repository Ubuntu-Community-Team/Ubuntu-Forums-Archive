---
title: "Evolution - 1 Inbox - &quot;Inbox Empty&quot; Uhh??"
date: 2010-11-04
forum: General Help
---

### Post by Roasted on 2010-11-04
I have Evolution running with two Gmail accounts. I have a weird issue. Whenever I delete an email, it still gets re-sent to me. If I give it about 15 seconds and hit send/receive, I get the same email back I just deleted. This happens on either one of my Gmail accounts.

Any ideas?

EDIT - I'm learning that it seems to be an issue with Gmail and the way they have IMAP set up, and that it's not in compliance with how IMAP should be set up. It sounds like the only reason Gmail works properly via IMAP on other clients is because those clients have patched Google's screw up. At least, that's what I'm reading. I'm just confused over how IMAP makes sense. I mean, when I get a new email, I get it in inbox and all mail. Is it necessary to go to both locations? Then when I delete it from inbox, it still shows up as "all mail (1)" as if I have an active message there. Ultimately, if I want that email DELETED, I have to delete it in 2 locations now instead of 1.

Can anybody explain this to me? Perhaps why IMAP works the way it does or why Evolution handles Gmail the way it does? Any help is appreciated...

---

### Post by dcstar on 2010-11-05
> **Roasted said:**
> 
.........
Can anybody explain this to me? Perhaps why IMAP works the way it does or why Evolution handles Gmail the way it does? Any help is appreciated...

All Evolution IMAP accounts have their own "tree" separate from the default Inbox.

If e-mails end up in your default Inbox then you are either using POP somewhere or you have filters set to copy/move e-mails.

---

### Post by Roasted on 2010-11-05
> **dcstar said:**
> All Evolution IMAP accounts have their own "tree" separate from the default Inbox.

If e-mails end up in your default Inbox then you are either using POP somewhere or you have filters set to copy/move e-mails.

I'm not sure I follow. What are you suggesting? I have two separate GMail accounts set up in Evolution with IMAP. It's just a total pain to have it act this way. Do I just set BOTH accounts to not be default? Would it work better if it didn't have a default account?

---

