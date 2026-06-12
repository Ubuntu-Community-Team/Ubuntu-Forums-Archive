---
title: "Alternative to DBAN"
date: 2010-05-17
forum: General Help
---

### Post by Matuku on 2010-05-17
I'm looking for an alternative to DBAN that can be used on specific drives rather than just wiping all the ones it can find. I've got a lot of external HDDs that I'm looking to wipe before selling and DBAN doesn't seem to let you pick and choose which disks it wipes. Anyone know of one that does?

---

### Post by cryptotheslow on 2010-05-17
Single overwrite with random or zero should be fine unless you have state secrets on those drives...  and the person buying them knows you did and is prepared to go to extreme lengths to try to get some of the information back.

DBAN is overkill imho - just use dd.

For random overwrite:
```
dd if=/dev/urandom of=/dev/sda
```

For a straight zero overwrite:
```
dd if=/dev/zero of=/dev/sda
```

Change the device after of= to be the device you want to overwrite of course!

Zero overwrite will be faster.

I'm always paranoid about accidentally overwriting my live disks so I disconnect them and then boot from a liveCD to use dd on drives I want to wipe.

---

