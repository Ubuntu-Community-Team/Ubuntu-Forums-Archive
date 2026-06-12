---
title: "hard disk errors"
date: 2006-05-27
forum: General Help
---

### Post by topquarck on 2006-05-27
hi all;

last week i upgraded my laptop to KDE 3.5.2 . every thing is fine but i noticed something strange: when i shut down my laptop normally by Logout in the KMenu. when i boot it again it tells me that the laptop was **unmounted uncleanly** and needs to force check <every time>. and now he detected errors <non-contingous block> . what can i do to fix this?

thnax alot

---

### Post by jazzmuzik on 2006-05-27
A file may have become irretrievably corrupted. Are you using ext3?

Just let it run through the check no matter how long it takes. It will fix errors automatically. If this doesn't fix it, see my first comment.

---

### Post by skyshark88 on 2006-05-27
Sounds like your disk is dying.....

---

### Post by treris on 2006-05-29
sounds like a good time to make a back-up of all of your important files,

anyway, it sounds like it could have something to do with the mounting permissions on your computer's harddrive(s)

not an expert here, but maybe somebody has an idea??/

---

### Post by MJN on 2006-05-29
It might be worth running smartctl on the drive (from the smartmontools package) to check the SMART status of the drive and perform some self tests.

However, if the drive is not unmounting cleanly then I'd be inclined to also check the logs as it's not necessarilly impending doom - and either way the logs should hold at least some idea as to what's happening (or not) on shutdown.

Mathew

---

