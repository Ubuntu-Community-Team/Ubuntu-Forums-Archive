---
title: "Ubuntu-Tweak...can't Unlock"
date: 2010-10-05
forum: General Help
---

### Post by tophousetim on 2010-10-05
Hi all. Little prob with Ubuntu-Tweak. I can't Unlock for some reason, as simple as that :(
It used to Unlock...no more. Completely uninstalled through Synaptic, then reinstalled and hasn't helped. I'm at a bit of a loss. And I'm not over technical either. Has anyone else experienced this?

Aspire 7736G. Intel Core 2 Duo T6600  Ubuntu 10.04LTS 2.6.32-25

---

### Post by spcwingo on 2010-10-05
You could try renaming the config folder.  It should be located in your home folder under ~/.config/ubuntu-tweak.  Just note that the folders with dots in front of the name are hidden.  If that doesn't work you could just delete the new config that it creates the next time you run the program and restore the previous name...no harm, no foul.  :)

---

### Post by tophousetim on 2010-10-08
Sorry to take so long spcwingo and thanks for the pointer, but that didn't work, renamed the ubuntu-tweak file in config, ran the program again, still no access, closed it and it created new ubuntu-tweak config file. Ran up again and still no access, or rather no "unlock". It did work the first few times I used it. Now it don't!

---

### Post by spcwingo on 2010-10-08
The only other thing I can think of is to uninstall ubuntu-tweak, delete the config file again, and then reinstalling ubuntu-tweak.  All that can be accomplished with this command:

```
sudo apt-get remove --purge ubuntu-tweak && rm -R ~/.config/ubuntu-tweak/* && rmdir ~/.config/ubuntu-tweak && sudo apt-get install ubuntu-tweak
```

The last part:

```
sudo apt-get install ubuntu-tweak
```

will only work if you have the ubuntu-tweak repository enabled on your system.  If you don't just leave that part off including the && in front of it and download from the ubuntu-tweak website then install.

If for some reason that doesn't work you can look under system>administration>users and groups and check to see if you're account type is set to Administrator.

---

### Post by tophousetim on 2010-10-23
thanks for the pointers spcwingo....but.....as usual my abilities are limited. I have found i can do all I wish if I open ubuntu-tweak as sudo in a terminal. But I cannot check my permissions in users, it won't let me "change". I know there are minimal commands through the terminal, but can't get a grip of these.

---

### Post by spcwingo on 2010-10-23
Do you have sudo privileges on the machine in question...if so, did you try to press the "change" button beside "Account Type"?  If you did and that didn't work I believe the terminal command is (although you still need sudo access):

```
useradd -G {group-name} username
```

[COLOR="Red"]WARNING:  I the only thing I ask is that you don't try that command before someone confirms it (I'm a bit rusty on the terminal).[/COLOR]

---

### Post by tophousetim on 2010-10-24
yes, tried the change button beside account type, it clicks but nothing happens, change name and password work and so does manage accounts, but change account type and advanced settings.....no. I have not knowingly played with any of the priviledge settings myself....thats what flusters me. Oh, and just for the record it is my machine, I'm the sole user and always have been, so it's my fault I hold my hands up. I'll have to have a closer look at Ubuntu for non-Geeks.......when I can sit down quietly and concentrate or else I can see I'll make things worse. It's only tweak I am having the problem with. Anyway, again, thanks and much appreciated. This from many miles away!

---

### Post by spcwingo on 2010-10-24
The only other thing I can think of to check is maybe it's something with policykit.  Open up Synaptic and search for policykit.  In the results post all the ones that are marked as installed (you might be missing one or more).

---

### Post by tophousetim on 2010-10-24
Hello my friend. Another very recent entry on this exact problem NimbusIIhas had 2days ago was solved by sisco311, suspecting policy kit. Followed his track and have so far been successful, it's put tweak right.

---

### Post by tophousetim on 2010-10-24
Now then, I'm sure you know best. Do I put a solved by this thread.....how. Again thank you for your guiding light. kind regards, Tim

---

### Post by spcwingo on 2010-10-25
It looks like you have figured out how to mark solved.  :)  The only thing I would recommend is to post the link that helped you to resolve your problem so that others who have the same issue that come across this thread can also solve their problem.

---

### Post by tophousetim on 2010-10-25
Solved this problem through the link [http://ubuntuforums.org/showthread.php?t=1603042&highlight=ubuntu-tweak+unlock](http://ubuntuforums.org/showthread.php?t=1603042&highlight=ubuntu-tweak+unlock). Thank you community.

---

