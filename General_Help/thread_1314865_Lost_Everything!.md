---
title: "Lost Everything!"
date: 2009-11-04
forum: General Help
---

### Post by Coach_Mark on 2009-11-04
Sorry if this is in the wrong place.  But, I'm at a loss about what to do here...

Currently I have a Dell Inspirion loaded with 9.04.  I've been trying to install Virtual Box for a couple days.  After solving the kernel issue, it would not read discs.  I un-installed and re-installed.  At that point I had a black border around everything (drop down windows, pop-up windows, mouse-over windows, etc.).  I tried a re-install of VB, after which it would not show on the desktop nor could I find a way to launch it.  When I rebooted the computer, it came up with the default desktop screen instead of my regular one, my evolution mail was asking me to set it up from scratch, it no longer had memory of my wireless network key, but it still had all my saved documents and FF favorites.

Anyone know what happened...what to do about it...and, how to recover my mail?

---

### Post by darco on 2009-11-04
Sounds like a corrupt profile. When you log in to your pc, are you entering your login name and pw or does it go straight to desktop? Have you tried the "log-out" option and see if you can see your profile?


darco

---

### Post by Coach_Mark on 2009-11-04
i'm the only user on this laptop.  if i log out, it prompts me to enter a user name.  at boot up, i get prompted for my pw. so that seems to be ok.

atm, aside fro trying to make sure this doesn't happen again, i can't find my old mail folders.  I was still in the set up process after wiping out Vista, and hadn't done a back up on the system.  i suspect that means it's gone...yes?  or is there some sort of system recovery i can do and get it back?

also, i keep finding more things that are not as they were.  the visual effect in appearances says desktop effects cannot be enabled when i try to change it from "none."

---

### Post by unamanic on 2009-11-04
Which mail client were you using?  The default, evolution?

---

### Post by Coach_Mark on 2009-11-05
yep.  i'm using evolution mail.

---

### Post by unamanic on 2009-11-05
1) During your troubleshooting did you ever remove or move any of these?
.evolution (where the mail is actually stored
.gconf (where some config settings are stored)
.gconfd (where some config settings are stored)

2) Did you reconfigure your mail?

If you removed the .gconf directories (sounds like you did because of the "fresh" desktop), but did **not** reconfigure your mail perform the following:
- from the command line, back up your mail directory: "mv .evolution bak.evolution"
- configure your mail by starting evolution
- close evolution after it's configured, but before it can fetch any mail from the server
- from the command line remove the new mail directory: "rm -rf .evolution"
- from the command line move your old mail directory back "mv bak.evolution .evolution"

If you have reconfigured your email, I do not know how it will play out, I'll have to test it to see.

---

### Post by Coach_Mark on 2009-11-05
oh.  sorry.  i forgot to include that a friend did recommend i reset the .gconf and .gconfd.  so that explains the screen and etc. reset.  thank you!!!!  however, i did NOT do anything with evolution files or settings.  currently away from my comp.  so, once i get back i'll try the mail reset as you described and post back the results.  thanks!

---

### Post by Coach_Mark on 2009-11-05
hmmm...that was strange.  when i finished reconfiguring the mail (step 2 in the list above)...all the old stuff appeared as soon it  launched...folders...messages...everything.  all seems well, now.  I did not have to go to any further steps.

oh...how do I get the appearance preferences-->visual effects thing to change?  It used to be set to "normal", now it says "none" and when I go to change it I get a warning that says "Desktop effects  could not be enabled."

CORRECTION:  when i changed screens...everything disappeared. and...when I moved the folder back (last two steps)  nothing was there.  apparently, it's all gone (unless someone has another suggestion).

---

### Post by unamanic on 2009-11-05
I know it doesn't help now, but I might suggest you try thunderbird int the future.  It's not effected by .gconf and backup/restoral is as easy as moving around a .thunderbird directory (or .mozilla-thunderbird depending on linux distro).  I hope you didn't lose too many emails.

---

### Post by Coach_Mark on 2009-11-06
unfortunately, it is a bunch of emails that are gone.  i'm hoping none were critical.   i just have to remember regardless of the losses learning from them is more important than the loss itself.  thanks for the tip on thunderbird.  overall i'm still very happy with Ubunut.  like all new things, it's a learning curve.  

thanks for all the help!  it's been greatly appreciated.:D

---

### Post by Macchi on 2009-11-09
Regarding risks for losing everything, I usually recommend: 
1) Forwarding your important e-mail addresses to another (hidden) address on another service provider (for instance, keep a copy on gmail).
2) Using IMAP accounts for anyone using more than one computer and/or with critical roles in the organization. Email on POP accounts may disappear.
3) Keeping backup copies of your /home and avoiding experiments on any machine that contains important data. 

Upon experiments you should be prepared to lose everything. Upon wild experiments there is even a risk of damaging hardware. Sorry to say, but this actually happens sometimes. 

I apologize if these comments are slightly off-topic.
Sincerely,
/Macchi

"... and most importantly, never take along anything on your journey so valuable or dear that its loss would devastate you."
Anne Tyler, The Accidental Tourist

---

### Post by Coach_Mark on 2009-11-09
Fortunately, this is a home computer, so the network issues don't apply in my case.  regardless, I appreciate the reminders on all points.  Good things to remember any time you are making changes.  This is my first go-round with changing over to Ubuntu.  Once I'm done getting it right here, I'll be changing over two other family computers.

---

