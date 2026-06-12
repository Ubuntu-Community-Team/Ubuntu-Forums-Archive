---
title: "Empathy group chat over MSN"
date: 2010-10-14
forum: General Help
---

### Post by kurtpete on 2010-10-14
After upgrading to 10.10, the newer Empathy (or possibly telepathy-butterfly) doesn't seem to be allowing me to create a group chat over the MSN network.  

It has always been a little cumbersome compared to other clients (open a chat window with one participant, select Coversation | Invite Participant, type in their name, add...repeat for each participant).  But now the "Invite Participant" menu item is always disabled.  I've tried removing/re-adding my account, rebooting, and a few other things, but no dice.  Lots of googling doesn't turn up anything current.  

Is anyone else having this issue, or is this isolated to my setup somehow?

---

### Post by Akavashi on 2011-06-06
Mmm... I seem to be getting this problem too; I'm using Ubuntu 11.04 though at the moment.
My friends can add me to the conversation, but the chat window never comes up.
I also have the problem of not being able to invite people to the chat room... where the "Invite to Chat Room" entry is disabled.

I wonder if anyone else has this problem? Or if it's just due to changes in the messenger protocol from Microsoft?

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **kurtpete said:**
> After upgrading to 10.10, the newer Empathy (or possibly telepathy-butterfly) doesn't seem to be allowing me to create a group chat over the MSN network.  

It has always been a little cumbersome compared to other clients (open a chat window with one participant, select Coversation | Invite Participant, type in their name, add...repeat for each participant).  But now the "Invite Participant" menu item is always disabled.  I've tried removing/re-adding my account, rebooting, and a few other things, but no dice.  Lots of googling doesn't turn up anything current.  

Is anyone else having this issue, or is this isolated to my setup somehow?

Did you make sure to install it from the PPA?

You can uninstall it completely with synaptic. 

Then run this in terminal:

```

sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install empathy

```

There a test PPA for this but I don't know it off hand at the moment, that you should try.

---

### Post by Triblaze on 2011-06-06
I noticed this too, I can't do group conversations on Empathy.


Instead, I use emesene, good MSN alternative, with group conversations and everything.

---

### Post by Akavashi on 2011-06-15
@linuxinstalledfromhdd
Cheers for that, installed Telepathy from the PPA to hopefully fix the issue... but it seems it must be an Empathy problem - that is, assuming Telepathy Butterfly actually allows group chat (which I'm pretty sure it does, since it worked for me in 10.10). Must just be an Empathy option that's not enabling properly... also tried the Empathy PPA, only to realise it was Empathy 3.0 :( - not exactly keen on working my Natty system over with Gnome 3 just yet :P

@Triblaze
Yeah, I've been using Emesene and Pidgin... But Emesene doesn't support concurrent accounts (GTalk and MSN); and Pidgin doesn't have the beloved Adium theme (which I love for Group Talk :P), although is still functional

---

