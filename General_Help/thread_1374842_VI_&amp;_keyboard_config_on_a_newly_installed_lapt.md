---
title: "VI &amp; keyboard config on a newly installed laptop"
date: 2010-01-07
forum: General Help
---

### Post by mansonthomas on 2010-01-07
Hi,

  I've just installed ubuntu 9.10 on my laptop, and when I'm on vim, I can use arrow key normally in command mode, but in editing mode, if I use them, it print a letter, capital case + new line and doesn't move the cursor.

  Any idea of what to do, so that my keyboard works ? 

  In putty I would try to play with the different type of keyboard settings (ESC[~, Linux, Xterm R6, VT400 etc...), but here, I don't know what to do.

  At the installation time, I choose French/French keyboard.


  Extra Question : 

   here: [http://www.ubuntu.com/getubuntu/releasenotes/910overview#GRUB%202%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/910overview#GRUB%202%20by%20default)

  It's said to have GRUB2 by default, but at boot time it says Grub 1.97 beta...

  Is it normal?

Thanks,
Thomas.

---

### Post by mansonthomas on 2010-01-11
up

---

### Post by llawwehttam on 2010-01-11
are you sure your using vim and not vi. vi had a different set of controls.  try

```
sudo apt-get install vim
```Sometimes of you type vim and don't have it it opens in vi.

And about grub 1.97 yes its normal. Grub 1.97 beta is normal as grub 2 has not been released yet except as beta but it is still better than grub-legacy as that needs a patch to boot ext4

---

### Post by mansonthomas on 2010-01-11
Thanks, you were right, it's vi that is installed not vim.

Thomas.

---

