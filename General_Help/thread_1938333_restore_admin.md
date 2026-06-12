---
title: "restore admin"
date: 2012-03-09
forum: General Help
---

### Post by soulcat on 2012-03-09
hi 

how do i restore my admin account status on ubuntu 11.10 so that i can make updates im on standard account at the moment due to pi@@ing about


cheers

---

### Post by yetiman64 on 2012-03-09
> **soulcat said:**
> hi 

how do i restore my admin account status on ubuntu 11.10 so that i can make updates im on standard account at the moment due to pi@@ing about


cheers

1. Can't you use sudo at all ? And 2. Is there only the one account on the machine now set to user ? 

If the answer to 1 is no and 2 is yes, you will need to boot to a recovery console. If you only have one OS on the machine you will need to press and hold down the shift key after the POST screen to access the grub boot menu. 

When you get to the grub boot menu select the recovery mode for your current kernel, it will boot to a console menu, select "drop to root shell prompt". When you get a root prompt issue the command,
```
useradd -G admin <yourusername>
``` no need to use "sudo" here and no password will be needed. Also replace <yourusername> with your actual log in user name.

I would suggest to reboot with the command "reboot" (don't include the quotes) here to make sure the changes take, though I suspect just exiting (type the command "exit", once again don't include the quotes) back to the console menu and continue to boot as normal, may work.

Whichever you choose to try (ie. exit or reboot), run the terminal command ```
groups
```and check "admin" is one of them. If it is, run an update ```
sudo apt-get update
``` and if it works without a problem you now have admin rights back.

---

### Post by Zephilinox on 2012-03-09
> **soulcat said:**
> hi 

how do i restore my admin account status on ubuntu 11.10 so that i can make updates im on standard account at the moment due to pi@@ing about


cheers

you mean you made another account? just log out your standard and log in with your admin, or if you mean you changed your user group to standard, then you will have to reboot and select recovery mode, which boots you in as root. I'm not sure about the command you have to enter to change a users usergroup, but a quick search should hold the answer.

---

### Post by soulcat on 2012-03-09
hi

i'm the only user do not want to add another was on admin now standard due to pi@@ing about

---

### Post by oldos2er on 2012-03-09
What is "pi@@ing about"? What exactly did you change?

---

