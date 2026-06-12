---
title: "error: no such partition"
date: 2011-08-21
forum: General Help
---

### Post by broadw on 2011-08-21
Hello - I have been a regular user of Ubuntu and love it.  I'm using the  netbook remix now, and have it installed as a dual boot with Windows XP on my ASUS 1005 netbook.  I am still a newbie though.

I have a problem that has happened to me twice before.  When I turn the netbook on, I get the dreaded:
"error: no such partition."  message, and then the grub rescue> prompt

I will bet that a Windows update messed around with the partitions.  One odd thing this time - absolutely no commands work with that grub rescue prompt - not even 'help'.  Whichever command I type, I get "Unknown command'.

I have solved this problem before by completely reinstalling Ubuntu, but now, I don't want to do that because it means I lose all of the data I have under Ubuntu.  

Is there a way to just fix grub without reinstalling?

Thank you!

---

### Post by TeoBigusGeekus on 2011-08-21
You could just [reinstall grub2]("https://help.ubuntu.com/community/Grub2#ChRoot"), not the whole os.

---

### Post by dandnsmith on 2011-08-21
I suggest you have a look at [boot info script](http://sourceforge.net/projects/bootinfoscript/)

It needs to be run from a working Ubuntu or other linux.
If you don't get anything from the results which helps, post them (between code tags), and someone will probably be able to offer suggestions to resolve the situation.

I understand your suspicion of those updates, but Windows XP updates don't (normally) go anywhere near the boot bock or partition. It's more likely that Ubuntu updates are causing the problem, as that is where any grub interference would come from.

---

