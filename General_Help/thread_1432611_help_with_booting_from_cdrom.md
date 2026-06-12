---
title: "help with booting from cdrom"
date: 2010-03-18
forum: General Help
---

### Post by Adrenochrom3 on 2010-03-18
ok heres the run down. my friend wants me to install another os onto his computer, next to windows and ubuntu. now grub is being gay and wont let his computer boot from cd. ive been in the system settings and changed the cdrom to the first slot under the boot options. but for some reason grub pops up before it can boot from cd. ive looked around to find the answer to my problem, but in times of need i always come running here for the more difficult questions. 

so i guess some how i have to deactivate grub so it boots to disc. man i get some insight on this situation im in?

---

### Post by Ozymandias_117 on 2010-03-18
It's doesn't have anything to do with GRUB, GRUB doesn't take over until BIOS looks on the hard drive for a boot device, for whatever reason, BIOS either isn't looking at the CD first, or it thinks the CD isn't bootable.

One thing you can try, if his computer has a one-time boot menu, you can select CD from that and see what it does. If that doesn't work, you can try removing Hard Drive from the boot order completely.

---

### Post by d3v1150m471c on 2010-03-18
When you start your computer you have to switch bios to boot from cd. Like ozy said it has nothing to do with grub.

---

### Post by Adrenochrom3 on 2010-03-18
yea like i said i changed the boot settings to have cd as the first choice. and no his computer does not have the one-time boot menu.

i mean i even tried to put the linux cd in the drive to see if would boot from that cd, and it would not. it was the same cd i used to install linux onto his computer, so theres no way the computer cant see that its bootable. so the problem still seems to be grub

any other suggestions?

---

### Post by Ozymandias_117 on 2010-03-18
Did you try completely disabling hard drive boot in BIOS options?

---

### Post by Adrenochrom3 on 2010-03-18
no i have not, he ended up leaving, so i came on here to see if anyone could give me a solution to this problem. next time hes here i will. but hypothetically speaking, if i wasnt able to do that, (because im not sure that it will let me remove boot options, i think it will only let me move them up and down the list.) but lets say this didnt work, what else can i do about this situation?

---

### Post by DeMus on 2010-03-18
> **Adrenochrom3 said:**
> yea like i said i changed the boot settings to have cd as the first choice. and no his computer does not have the one-time boot menu.

i mean i even tried to put the linux cd in the drive to see if would boot from that cd, and it would not. it was the same cd i used to install linux onto his computer, so theres no way the computer cant see that its bootable. so the problem still seems to be grub

any other suggestions?

As has been explained before in this thread: this has nothing to do with Grub.
Grub is situated on your hard disk and it will only be started because in BIOS it says: start from hard disk. Then BIOS will look in the MBR of the mentioned hard disk and will boot up the OS mentioned in there, in your case GRUB will boot and you have the choice to either choose Ubuntu or Windows.
In BIOS you have to say you want to boot from the cd-rom drive. If, for whatever reason, this does not work then we have to find the reason.

[LIST=1]
[*]Are you sure the cd is bootable? Try it on an other computer
[*]Are you sure the cd drive is okay? Can you read the contents of the Ubuntu cd when booted in Ubuntu? Can you read the contents of the cd when booted in Windows?
[*]Check again in BIOS to make sure you placed the cd drive on the first place. Do you have more than 1 cd-drive? If so, make sure the _correct_ one is in first place.

[/LIST]

---

