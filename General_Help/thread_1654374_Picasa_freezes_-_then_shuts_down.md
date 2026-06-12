---
title: "Picasa freezes - then shuts down"
date: 2010-12-28
forum: General Help
---

### Post by Ronson76 on 2010-12-28
For some time I've encountered that Picasa freezes shortly after HD scanning is complete. Then 15-30 seconds later it shuts down. Today I re-installed Picasa 3 on my Maverick distro. And the problem still persists.

I know the topic has been raised elsewhere but that was concerning Windows machines. I can't find any solution to this annoying problem for Linux distros. Would appreciate some assistance here - thanks.

---

### Post by CheetoBandito on 2010-12-28
Have you started picasa from a terminal window and checked for debug output?

---

### Post by Ronson76 on 2010-12-29
Yes, I did and the symptoms are the same. No debug output.

---

### Post by fooman on 2010-12-29
hi,  have you tried deleting the picasa config files?  when i encounter a problem with a particular app in linux/ubuntu...thats usually one of the things i try.  the config files will re-create themselves when you restart the application.

the config files for picasa3 are stored in a "hidden" file @ /home/<user name>/.google/picasa

a file is "hidden" when it has a "." in front of it.  in order to see it,  open your home folder (places > home folder),  in the toolbar, look under "view" and put a check mark next to "show hidden files"

find/open the .google folder and delete the "picasa" folder that is in there.

then try to start picasa again....see if that helps.

---

### Post by Ronson76 on 2010-12-29
fooman,

Thanks for your input. I tried what you explained but unfortunately it didn't solve it.

However, I now have a strong suspicion that Picasa has a problem with files containing special national letters. It's like when it detects a file named something containing the Danish letters æ, ø or å, it freezes there for 10-15 seconds and then shuts down.

It never did that when I used to run Picasa on Windows. For your info the language is entirely English (UK) on my Linux machine.

How the heck do I solve that one?

---

