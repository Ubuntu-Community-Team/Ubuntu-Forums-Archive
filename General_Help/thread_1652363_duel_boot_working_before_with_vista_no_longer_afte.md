---
title: "duel boot working before with vista no longer after 7"
date: 2010-12-24
forum: General Help
---

### Post by hifonics10 on 2010-12-24
ok so last night i had my computer set up and working with both vista and ubuntu dual boot so when i started my computer i had a choice between ubuntu or vista went back and forth a few times to make sure everythign worked fine and it did. so this morning i update my vista basic to 7 home premium well now when i start my computer i no longer have a choice and it boots directly into 7. can someone help me fix this i really liked being able to have both on on hdd

i know that ubuntu is still there becouse my hdd reads 220 free of 250 the hdd is 320 i set the other half for ubuntu

---

### Post by spiky001 on 2010-12-24
Have a read of this it explains what you have to do [http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)

---

### Post by wilee-nilee on 2010-12-24
Post this script so we can see what is where. So while your on the live cd you can also just take a screen shot of gparted, menu-system-admin-gparted, 

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by hifonics10 on 2010-12-25
what is a live cd? is that just the normal os on the cd? also i upgrading to 10.10 and the cd is for 10.04 would that matter or do i need to download 10.10 then burn it?

---

### Post by wilee-nilee on 2010-12-25
> **hifonics10 said:**
> what is a live cd? is that just the normal os on the cd? also i upgrading to 10.10 and the cd is for 10.04 would that matter or do i need to download 10.10 then burn it?

You seem to have a wubi install.

Did you install Ubuntu from a live running windows?

Not knowing what a live cd makes it seem like this sort of install.

---

### Post by hifonics10 on 2010-12-26
well i downloaded ubuntu 10.04 iso from rarbg. burned it then installed it on a differnt hdd to see if it works then i installed it on this one that had vista at the time selected the duel boot option everything worked fine now after 7 it does this so would that be a live cd? should i just go download 10.10 and re burn it

---

### Post by wilee-nilee on 2010-12-26
> **hifonics10 said:**
> well i downloaded ubuntu 10.04 iso from rarbg. burned it then installed it on a differnt hdd to see if it works then i installed it on this one that had vista at the time selected the duel boot option everything worked fine now after 7 it does this so would that be a live cd? should i just go download 10.10 and re burn it

I personally can't really help you until I know more information and the bootscript in my signature will provide that. If you run the script read the instructions carefully and post it in code tags as described in my earlier post and in my signature.

Your not knowing what a live cd is alone, makes me hesitant as we want to be on the same page.:)

---

### Post by WorMzy on 2010-12-26
When you installed Win 7, you overwrote the MBR with Win 7's bootloader. I'd expect that to give you the option of Vista or Win 7 at least.. but oh well.

Follow this tutorial to recover grub: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Or, alternatively, run the boot info script for more specific advice regarding your system.

---

