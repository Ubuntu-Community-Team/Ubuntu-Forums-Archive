---
title: "Problem with Google Chrome"
date: 2010-05-11
forum: General Help
---

### Post by The_Aegidius on 2010-05-11
I get this error when I lunch Google Chrome.

[IMG]http://img688.imageshack.us/img688/7076/tempm.png[/IMG]

How can I solve that?

---

### Post by Peter09 on 2010-05-11
How did you install Chrome, did you use sudo or install as another user?

---

### Post by The_Aegidius on 2010-05-11
I download a deb package frome [here]("http://img688.imageshack.us/img688/7076/tempm.png").

---

### Post by zaphod777 on 2010-05-11
open system manager and kill chrome then open it again. This happens when a process is frozen.

---

### Post by The_Aegidius on 2010-05-11
There is no Google Chrome process active.

---

### Post by zaphod777 on 2010-05-11
it would show up as chrome.
If rebooting doesn't help then you need to make note of all of your extensions and username / passwords and go to 

~/.config/ 

and either rename or delete the google-chrome folder. This will reset your google chrome profile and you will be basically starting over from scratch. Somehow your profile got corrupted.

---

### Post by zaphod777 on 2010-05-11
oh and make sure you have bookmark sync setup so you don't lose the bookmarks.

---

### Post by zaphod777 on 2010-05-11
> **88escort said:**
> no i think google chrome is good.
<snip>

I have run into this exact problem myself and this is how I fixed it. 

But I agree I also like chrome it is very fast.

---

### Post by The_Aegidius on 2010-05-11
zaphod777 really thanks for helping me, but I don't understand where i can find the ~/.config/ file. It's not in opt/google/chrome directory.

---

### Post by zaphod777 on 2010-05-11
~/ is just another way to say your home directory sorry. 

and then click view hidden folders and you should see it.

---

### Post by The_Aegidius on 2010-05-11
Thank you! I solved the problem!

---

### Post by zaphod777 on 2010-05-11
no problem :guitar:

---

### Post by The_Aegidius on 2010-05-11
I'm sorry, but I closed Chrome and when I open it again i still got the problem.

Have you got any ideas?

---

### Post by The_Aegidius on 2010-05-11
If I lunch Chrome with sudo google-chrome the browser start normally and with my preferences.

---

### Post by Nathan_M on 2010-05-11
> **The_Aegidius said:**
> If I lunch Chrome with sudo google-chrome the browser start normally and with my preferences.

That means there's some kind of permissions problem in your home folder.

Type in the terminal ```
ls -l | grep chrome
```. It should say ```
drwx------ 5 nathan nathan 4096 2010-05-11 17:12 google-chrome
``` (but your username instead of nathan, and a different time). It's the drwx bit and the username but that's important.

Oh, and now that you've diagnosed the problem by running Chrome in sudo, don't do it again... it's a security risk allowing your web browser the ability to modify any file on your computer.

---

### Post by The_Aegidius on 2010-05-11
Giving that command I get no response.

[[IMG]http://img33.imageshack.us/img33/1362/tempn.th.png[/IMG]](http://img33.imageshack.us/i/tempn.png/)

---

### Post by The_Aegidius on 2010-05-11
Is it possible that I got a virus? Cause now I got problem with Apache permissions.

---

### Post by The_Aegidius on 2010-05-11
I solved setting 755 permissions.

---

### Post by Nathan_M on 2010-05-12
> **The_Aegidius said:**
> Giving that command I get no response.

[[IMG]http://img33.imageshack.us/img33/1362/tempn.th.png[/IMG]](http://img33.imageshack.us/i/tempn.png/)

Not sure if you mean you've solved the chrome problem or not...

Sorry, I should have said, first type ```
cd .config/
```, then the command above. cd .config/ moves you to the .config folder, ls means "list all the files and folders in the current folder", and the -s flag makes ls show some additional information, including the all-important permissions bit.

---

