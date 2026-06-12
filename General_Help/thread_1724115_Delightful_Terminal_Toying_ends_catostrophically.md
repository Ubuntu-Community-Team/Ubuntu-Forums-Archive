---
title: "Delightful Terminal Toying ends catostrophically?"
date: 2011-04-07
forum: General Help
---

### Post by Captain Potter Fujichan on 2011-04-07
I was searching for a way to disable the xubuntu GUI (as i have it installed over the ubuntu server) to revert back to the server command line temporarily, and I came across this post: [http://ubuntuforums.org/showthread.php?t=43516](http://ubuntuforums.org/showthread.php?t=43516)
I followed the instructions in the second post, and got this from terminal:
```
minecraft@minecraft:~$ sudo update-rc.d -f xfce remove
 Removing any system startup links for /etc/init.d/xfce ...
Then I ran this to repair it:
minecraft@minecraft:~$ sudo update-rc.d xfce defaults
update-rc.d: /etc/init.d/xfce: file does not exist

```But i simply don't know what happened.
The machine's name is minecraft in all instances.
Absolutely nothing whatsoever happened after rebooting.
What did I do? and is there a way to revert to command line from XFCE, maybe by terminating processes? How can I fix whatever i did?

---

