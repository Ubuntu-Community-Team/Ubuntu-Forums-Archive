---
title: "installed windows after linux"
date: 2010-10-23
forum: General Help
---

### Post by deviator on 2010-10-23
hi i just installed vista over my xp partition because xp was mucking up and gave me a blue screen on bootup.

now when my computer loads i get "disk error press enter to reboot"

after pressing enter i'm taking to the grub menu where ubuntu loads up fine but still shows xp at the bottom of the list.

i've found several help docs telling me how to do it step by step (installing windows after ubuntu) but i'm confused about editing the grub.

what should i do exactly to update grub and get vista in place of xp?

---

### Post by skyjacker on 2010-10-23
Try the info in this thread...[HTML]http://ubuntuforums.org/showthread.php?t=169234[/HTML]

---

### Post by garvinrick4 on 2010-10-24
I am very surprised Vista did not overwrite grub2 and put its window grub in its place.
If can boot into Ubuntu might as well give it one of these;
```
sudo grub-install /dev/sda
``````
sudo update-grub
```

---

