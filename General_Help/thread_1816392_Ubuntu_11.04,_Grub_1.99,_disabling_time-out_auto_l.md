---
title: "Ubuntu 11.04, Grub 1.99, disabling time-out auto load of OS?"
date: 2011-08-01
forum: General Help
---

### Post by Trilogin on 2011-08-01
I have an Ubuntu/Win7 dual boot system with GRUB as my default bootloader, and I am often distracted by other things when I boot up my PC. Is there any way I can stop GRUB from loading linux automatically after it times out? I would prefer if it never timed out, and I could eternally have the OS selection on the screen until I decide to select an OS. 

Have been reading the GNU Grub Manual, but I can't make heads or tails of some of the more technical stuff yet and I do not know enough about Terminal to know all of the commands they are throwing at me.

---

### Post by Trilogin on 2011-08-01
EDIT: NOT SOLVED, actually :) /EDIT SOLVED! I ran terminal then used cd to change directory, navigated to the /etc/default directory then used ls to list the files to make sure I had the correct directory. After this I used:

sudo chown adam /etc/default/grub 

This changed the ownership of the GRUB file to my user instead of it being root.

Then I used the file system navigator that came default with ubuntu and navigated to the grub file.

I changed GRUB_TIMEOUT to look like this:

GRUB_TIMEOUT=-1 

I got the GRUB_TIMEOUT=-1 value from this link:

[http://www.gnu.org/software/grub/manual/html_node/Simple-configuration.html#Simple-configuration](http://www.gnu.org/software/grub/manual/html_node/Simple-configuration.html#Simple-configuration)

I saved the file, used this command:

sudo chown root /etc/default/grub

to change the ownership back to root so that the file cannot be altered by me without doing a bunch of command line stuff again. 

Now to see if it works! :)

EDIT****

Ok. This did not work.  GRUB still automatically booted into Linux after just 10 seconds. I navigated back to the file and opened it, and my change remains. So why did my change not work?

---

