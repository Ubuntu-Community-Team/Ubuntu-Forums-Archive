---
title: "Messed up $PATH in ~./pam_environment, can't login"
date: 2011-12-29
forum: General Help
---

### Post by Kevka on 2011-12-29
Hi,
so the situation is the following:
- I've been using Ubuntu for 2 years now and know how to do easy stuff using the shell, but I'm no expert
- On my computer (Ubuntu 11.10) there is one superuser account and the home folder is located on a separate partition and is encrypted (setup with the installer)
- I changed ~/.pam_environment but I must have messed something up because since then I haven't been able to log in
- when I try to log in a message box appears with the following message: "Could not connect to session bus: //bin/dbus_launch terminated abnormally without any error message" (from what I found on google this means that the $PATH variable is messed up and this would make sense with me changing the  ~/.pam_environment file)

Now I think I'll have to empty the  ~/.pam_environmentand everything should work. But unfortunatelly I do not know how to do this. If I had another super user account on my computer I'd log in and try to mount the home partition. But I only have the guest login and the root shell I get when I start in recovery mode.
Can someone please point me in the right direction to solve this problem.

Best regards,
Kevka

---

### Post by Kevka on 2011-12-29
Just wanted to push this thread up!!
I really need help.
Is there maybe a way to login without the shell loading the messed up $PATH from ~./pam_environment????
Kevka

---

### Post by sinha1612 on 2012-01-04
> **Kevka said:**
> Hi,
so the situation is the following:
- I've been using Ubuntu for 2 years now and know how to do easy stuff using the shell, but I'm no expert
- On my computer (Ubuntu 11.10) there is one superuser account and the home folder is located on a separate partition and is encrypted (setup with the installer)
- I changed ~/.pam_environment but I must have messed something up because since then I haven't been able to log in
- when I try to log in a message box appears with the following message: "Could not connect to session bus: //bin/dbus_launch terminated abnormally without any error message" (from what I found on google this means that the $PATH variable is messed up and this would make sense with me changing the  ~/.pam_environment file)

Now I think I'll have to empty the  ~/.pam_environmentand everything should work. But unfortunatelly I do not know how to do this. If I had another super user account on my computer I'd log in and try to mount the home partition. But I only have the guest login and the root shell I get when I start in recovery mode.
Can someone please point me in the right direction to solve this problem.

Best regards,
Kevka

Hi Kevka,

Did you solve your problem?

If not, you can try this. 
- When you are at the log-in screen press Ctrl+Alt+F1. This will give you a full-screen command line environment. 
- Log in at the prompt. You will see some errors. Ignore them.
- type ```
/bin/mv .pam_environment pam_environment_err
``` or any other name you would want to rename it to. You could also use /bin/rm to delete the file.
- Now type exit to quit the shell and then press Ctrl+Alt+F7 to go back to the graphical login screen.

Hope it helps! :)

---

### Post by efflandt on 2012-01-04
If all else fails, maybe you could fix it from a live system on install CD or install iso on bootable USB. You need to prefix root commands with "sudo " to do them as root.  Although, if what you are to get to is encrypted I don't know how easy or possible that is (never used that).

---

### Post by tigerswing2 on 2012-06-28
> **Kevka said:**
> Hi,
so the situation is the following:
- I've been using Ubuntu for 2 years now and know how to do easy stuff using the shell, but I'm no expert
- On my computer (Ubuntu 11.10) there is one superuser account and the home folder is located on a separate partition and is encrypted (setup with the installer)
- I changed ~/.pam_environment but I must have messed something up because since then I haven't been able to log in
- when I try to log in a message box appears with the following message: "Could not connect to session bus: //bin/dbus_launch terminated abnormally without any error message" (from what I found on google this means that the $PATH variable is messed up and this would make sense with me changing the  ~/.pam_environment file)

Now I think I'll have to empty the  ~/.pam_environmentand everything should work. But unfortunatelly I do not know how to do this. If I had another super user account on my computer I'd log in and try to mount the home partition. But I only have the guest login and the root shell I get when I start in recovery mode.
Can someone please point me in the right direction to solve this problem.

Best regards,
Kevka

Hi kevka, I have the same problem and tried what sinha1612 suggested, however it doesn't work. Did you resolve the problem already? Can you tell me how did you do it?

Thanks.

---

### Post by venky_194 on 2013-03-04
Thanks, this worked

---

