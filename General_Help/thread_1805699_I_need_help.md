---
title: "I need help"
date: 2011-07-16
forum: General Help
---

### Post by ub45 on 2011-07-16
I've just changed my password and somehow I've accidentally brushed some keys when creating the 
password now I can't change anything, is there a solution to this. I haven't logged out of the
computer yet.

---

### Post by mvmacd on 2011-07-16
There is a way to boot your computer into root.  I have not tried it on Ubuntu 11, but I am pretty sure it will work.

1. Turn off your computer
2. Turn it back on.
3. Wait for GRUB, when you see it press **ESC**.
4. Press **e** to edit the boot string.
5. Go to the very end of the line, and add this: **[color=blue]rw init=/bin/bash[/color]**. 
6. Press **Enter**.
7. Press **b** to boot Ubuntu.
8. Now, it should have dropped you to a **[color=red]root[/color]** shell.  Be aware root can screw your system if you do not know what you're doing.
9. Enter the command **[color=green]passwd USERNAME[/color]**, where USERNAME is *your* username.
10. It will ask you to enter a new 'UNIX' password.  Enter your new password.
11. Confirm it, and then type the command **[color=green]reboot[/color]**.  That's it!

---

### Post by heyitseric on 2011-07-16
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

i ran into the same problem and this helped me

---

### Post by ub45 on 2011-07-16
Thanks

---

