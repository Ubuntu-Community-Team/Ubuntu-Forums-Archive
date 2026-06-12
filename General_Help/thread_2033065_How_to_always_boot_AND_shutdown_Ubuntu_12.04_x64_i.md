---
title: "How to always boot AND shutdown Ubuntu 12.04 x64 in verbose mode?"
date: 2012-07-25
forum: General Help
---

### Post by javagreen on 2012-07-25
I want to be able to boot AND shutdown Ubuntu 12.04 x64 always in verose mode. The pink/purple spash screen doesn't scale to my monitor's resolution and thus looks bad. 

Also, I'd love to be able to see what goes on 'under the hood' so to speak during thr boot-up process. :P

Help please?

---

### Post by dino99 on 2012-07-25
remove "quiet splash" from /etc/default/grub, then update-grub

---

### Post by javagreen on 2012-07-25
> **dino99 said:**
> remove "quiet splash" from /etc/default/grub, then update-grub

Thanks, I did the above but for some reason it's STILL showing the splash screen on boot-up. 

Any idea why it's doing that?

I did a 'sudo nautilus' in terminal to get to the grub config file, edited & saved it and closed the terminal. I forgot I also had to do 'sudo update-grub' ... so I opened up terminal again and did it. Double checked whether the quiet + splash option is gone from the config file, and it's gone.

---

### Post by dino99 on 2012-07-25
> **javagreen said:**
> Thanks, I did the above but for some reason it's STILL showing the splash screen on boot-up. 

Any idea why it's doing that?

I did a 'sudo nautilus' in terminal to get to the grub config file, edited & saved it and closed the terminal. I forgot I also had to do 'sudo update-grub' ... so I opened up terminal again and did it. Double checked whether the quiet + splash option is gone from the config file, and it's gone.

while you see the splash screen, hit the UP key, that should switch to text (verbose)

an other option is to use GRUB_TERMINAL=console
[http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode](http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode)

---

### Post by javagreen on 2012-07-25
> **dino99 said:**
> while you see the splash screen, hit the UP key, that should switch to text (verbose)

an other option is to use GRUB_TERMINAL=console
[http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode](http://askubuntu.com/questions/92276/how-do-i-boot-into-true-text-mode)


Thanks a heap, uncommenting the 'GRUB_TERMINAL=console' line did the trick :D

---

