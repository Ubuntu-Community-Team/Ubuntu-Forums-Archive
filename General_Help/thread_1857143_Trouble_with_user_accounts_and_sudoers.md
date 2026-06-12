---
title: "Trouble with user accounts and sudoers"
date: 2011-10-09
forum: General Help
---

### Post by warmnscsi on 2011-10-09
Ok so I've been searching google for the past hour trying to get this to work right. I'm currently using bt5r1 - gnome variant (exactly like ubuntu 10.10) and I made a new password protected user called "User" since it only comes with one user which is the root user. So after creating this user I log in and I am now in a terminal. I typed sudo startx to start the gui and it told me I wasnt in the sudoers. So after some research I open sudo visudo and put in the line under #user priveledge specification I put: User     ALL=(ALL) ALL

So now I can log into the user account and sudo startx to get in but when I go to the terminal it says "sh-4.1#" I know the hash sign means I am logged in as root (I think) so I think I did something wrong somewhere.

I just want to be able to log in as the user and be able to sudo when I need to. If you can help that would be much appreciated. Thanks :)

---

### Post by mikejonesey on 2011-10-09
to be born or rebourne?

...your user is not setup with bash you can change the users default shell using usermod... (man usermod)

ps in sudoers to confirm...
username ALL=(ALL) ALL

will allow a user with with the username username to do whatever they want with a password...

---

### Post by sisco311 on 2011-10-10
> **mikejonesey said:**
> to be born or rebourne?

...your user is not setup with bash you can change the users default shell using usermod... (man usermod)

ps in sudoers to confirm...
username ALL=(ALL) ALL

will allow a user with with the username username to do whatever they want with a password...

No need to run usermod as root in order to change the user's shell. Users are allowed to change their login shell:
```
chsh
```

---

