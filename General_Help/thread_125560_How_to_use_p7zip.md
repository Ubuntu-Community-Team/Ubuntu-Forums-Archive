---
title: "How to use p7zip?"
date: 2006-02-04
forum: General Help
---

### Post by Gundamdriver on 2006-02-04
Hi. I found that p7zip (in MS Windows, 7-Zip) supports more file extensions than that of Archive Manager, which is pre-installed in ubuntu.

Now I installed p7zip, but how can I start the program? Does it have a GUI interface?

Thanks.

---

### Post by Gundamdriver on 2006-02-04
Oh... I found that I should type in 7za in terminal, then the program will be loaded.
But, does ithave a GUI interface? I'm still not good at using commands...

---

### Post by fakie_flip on 2006-08-12
Yes, you are supposed to be able to use p7zip with file roller and xarchiver, but using it from the command line could give you better compression because you can change the amount of compression you want to get better speed from the command line. I have been trying to figure out what is the difference between 7z and 7za. running `man 7z` and `man 7za` shows that they appear to be exactly the same, so why is there two. There must be some difference that I do not know about. Which one should be used?

---

### Post by fakie_flip on 2006-08-12
Using the CLI (Command Line Interface) is much better. Really, you should learn it as much as possible. It's much faster, and you will be more likely to get a job using Linux if you are good at it. What if your system crashes or x won't start? I hope you are good with vi to edit configuration files and understand them because you may not have a gui app to do the job and every Linux distro I've seen came with vi. An example of doing something faster with commands would be to use a for loop or wildcard (asterisk) to go through each file and compress it, or to only compress all the text files in a directory instead of JPG pictures also because they are already compressed.

---

