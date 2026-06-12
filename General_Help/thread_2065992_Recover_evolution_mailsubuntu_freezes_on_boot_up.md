---
title: "Recover evolution mails/ubuntu freezes on boot up"
date: 2012-10-03
forum: General Help
---

### Post by achu91 on 2012-10-03
Please  guide me on how to recover mails from evolution 3.2..Due to my experiment with Ubuntu i am unable to boot and Ubuntu freezes when booting up.But i am able to login to terminal mode using ctrl f1 .So please guide me on how to accomplish the same using a live cd or any other method.

The reason to reach such a stage while boot up is that i played with grub menu tutorial from google.I also tried to repair the boot by usng boot-repair program.But still ubuntu freezes while booting.

---

### Post by alarme on 2012-10-03
Hi:

From a live CD/USB, copy the folder  /home/yourusernamehere/.local/share/evolution to a safe place.

Then, on a working install, import messages from the copy of .local/share/evolution/mail/local/

Good luck

---

### Post by achu91 on 2012-10-05
Thanks for the information .the mission was successful.





> **alarme said:**
> Hi:

From a live CD/USB, copy the folder  /home/yourusernamehere/.local/share/evolution to a safe place.

Then, on a working install, import messages from the copy of .local/share/evolution/mail/local/

Good luck

---

### Post by piddewest on 2012-10-05
> **achu91 said:**
> Please  guide me on how to recover mails from evolution 3.2..Due to my experiment with Ubuntu i am unable to boot and Ubuntu freezes when booting up.But i am able to login to terminal mode using ctrl f1 .So please guide me on how to accomplish the same using a live cd or any other method.

The reason to reach such a stage while boot up is that i played with grub menu tutorial from google.I also tried to repair the boot by usng boot-repair program.But still ubuntu freezes while booting.

Even if its solved i would like to give you an advice how i solved a similar problem when the boot process halts.

I used boot-repair tool but in advanced mode. Choosed "Purge Grub before reinstall" and "Purge Kernels and reinstall last kernel"

That solved my problem. I tried the easy mode first, but that did not help.

---

### Post by achu91 on 2012-11-05
Thank you very much  for the information.i will certainly use this next time.

---

