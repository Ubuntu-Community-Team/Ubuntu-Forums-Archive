---
title: "Evolution summary and folder mismatch (after all the usual fixes)"
date: 2010-08-22
forum: General Help
---

### Post by zak on 2010-08-22
The "summary and folder mismatch even after a sync" error is pretty common in Evolution. Usually just closing the program and re-opening it is enough to get rid of the error. Sometimes, it's necessary to delete the .index, .index.data and .cmeta files, then give it time to resync. I've done all that.

I also moved .evolution/mail/local/*, started with an empty inbox, then used the import function on the old one. After doing so, the problem occurs again, which suggests there's something about the *contents* of the inbox that Evolution doesn't like.

I have 35,000 email messages stored here, and I'd like to keep them in Evolution where I can sort them, search them and arrange things with search folders. I'd be happy to delete a couple corrupted messages if that's the issue. The difficulty is finding them. If there's something specific to look for, I can write a script to search the inbox for corrupted messages.

Should I be asking this question somewhere more Evolution-specific? I tried the IRC channel, but got no answers.

---

