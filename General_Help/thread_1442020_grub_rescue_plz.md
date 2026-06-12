---
title: "grub rescue plz"
date: 2010-03-29
forum: General Help
---

### Post by spiky001 on 2010-03-29
Hi I have had a few problems with a desktop, now I think I need to repair Grub2 I had a problem where it wont boot because of a dvd drive causing probs will sort that later then got Grub rescue error, I have got it to boot into system after many attempts do I need to do a repair on grub?

---

### Post by Brandon Williams on 2010-03-29
It sounds like running a repair on grub would be a good idea, yes. All the information you might need to figure this out can be found [here](https://help.ubuntu.com/community/Grub2). If you need more help figuring out the exact commands to run, please post your specific questions. Typically, you would run 'sudo grub-install /dev/sda' (or some other disc if sda isn't the disc you boot from) followed by 'sudo update-grub'.

---

