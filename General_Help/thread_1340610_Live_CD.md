---
title: "Live CD"
date: 2009-11-28
forum: General Help
---

### Post by jstnreed on 2009-11-28
Just a rather dumb question about the Live CD - when you select the mode - use Ubuntu w/o any change to your computer and need to re-install Grub. How do I do this? I know I need to re-install Grub but I can't seem to get it to work b/c of the mode I am in possibly. I know I am installing Grub right through the terminal b/c it seems to work fine but than cannot get it to work. If someone could just clear this up or explain what I am doing wrong that would be great.

---

### Post by SuaSwe on 2009-11-28
Maybe try reinstalling it via the recovery prompt instead? Boot without the disk and select 'Recovery Mode' then 'Drop into root shell', then try the necessary commands to reinstall GRUB? 

Also, could you walk us through what happened when you tried it from the LiveCD?

---

### Post by jstnreed on 2009-11-28
Ok, well, I went to the terminal in ubuntu and then ran the command to install grub. What happened was, I had a ubuntu partition and I was unhappy with that so I re-installed ubuntu on another partition. I deleted the orginal unbuntu partion (after installation of the new one) and then when I shut down my computer and restarted. Since it was a dual-boot-grub would start up and then I would select my OS. But since I deleted that orginal ubuntu partition - grub would not recognize my filesystem. It would say: filesystem unknown and then grub rescue. So this is why I was wanted to re-install Grub. The problem was, however, not being able to get on a already installed OS I had to use the Live CD to try to reinstall Grub. The problem I think with the live CD is that with the mode I was using which is the only mode that boots up unbuntu on the Live CD i belive. Nothing went wrong trying to install Grub except when I restarted the computer grub would still not work right so I thought the Live CD was only installing temporally for that session on the CD It would not really install Grub b/c the mode won't leave any permanent changes. That is why I was asking about the Live CD. As far as the recovery prompt - I never tried it - but will give it a go. Just how exactly does it work or what exactly is it telling the computer to do? out of curiosity.

---

