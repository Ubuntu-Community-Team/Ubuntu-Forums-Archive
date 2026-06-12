---
title: "Automount partition deleted, Cannot boot up"
date: 2010-05-14
forum: General Help
---

### Post by IamPi on 2010-05-14
i recently deleted a NTFS partition while ubuntu was running and didnt disable the automount and when i tried to restart from what i can see it is trying to mount the partition which does not exist. When booting it says something to the effect of mounting dev/sda5 (which is now ubuntu) NTFS signature incorrect, what file must i change to allow ubuntu to boot because i kind of dont want to reinstall ubuntu and reconfigure it.

---

### Post by IamPi on 2010-05-14
Already solved it, was in live cd and edited FSTAB file. Thought there was more problems w/ ubuntu but looks like it was just the mounting that was the problem. =)

---

