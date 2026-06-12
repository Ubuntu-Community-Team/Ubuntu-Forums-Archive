---
title: "Backup utility"
date: 2009-08-15
forum: General Help
---

### Post by Mikael P. on 2009-08-15
Hello forum,
I was wondering if anyone could suggest a good backup tool?

Back on windows I was using Cobian backup and liked it a lot. So ideally I'd like something similar. I haven't tried running it through wine yet as I'd prefer something native to linux.

I am not going to use it to backup whole partitions, just to specify certain directories to be backed up.

Lastly, non GUI solutions aren't interesting really. I am not so accustomed to ubuntu yet...

Thanks for your help!

---

### Post by Sidewinder1 on 2009-08-15
I'm not familiar with Cobian,... I use GRSYNC, it's a GUI front-end to the rsync command in terminal. You will find it in the Synaptic repositories.
HTH, Side

---

### Post by Mikael P. on 2009-08-15
Do you have to create several sessions to backup different directories? Or can you nest them all in one session?

Are there more options hidden in the shell version? If I were to use the text based grsync can I create a settings file somewhere to control it?

---

### Post by Sidewinder1 on 2009-08-15
I'm not certain that I understand your questions. Try installing grsync from Synaptic and check out all of the various options. It even has a "Simulate" button to check out what will happen. If you don't like it you can always remove it with Synaptic. IMHO, you only really need to back up your home/"username" directory as all of the other kernel/configuration files in root could be reinstalled from the ubuntu disk...
Side

---

### Post by Mikael P. on 2009-08-15
Yes, but I spread out somewhat. Putting my work files on a different partition and other files on other partitions.
I found another tool called pyBackPack where it was easy to specify several different folders in one go and where they should end up.

Thanks for you help anyway!

---

### Post by Sidewinder1 on 2009-08-15
No problem. :-)

---

### Post by longtom on 2009-08-15
This is a good question, which coincidently was asked by me as well some time ago:

[http://ubuntuforums.org/showthread.php?t=1165866](http://ubuntuforums.org/showthread.php?t=1165866)

However, I didn't really find what I was looking for, also some people tried to help out.  You'll find suggestions in the thread.

The closest I got was fwbackups - see also here:

[http://ubuntuforums.org/showthread.php?t=1223364](http://ubuntuforums.org/showthread.php?t=1223364)

I keep an eye on this one.

---

### Post by Mikael P. on 2009-08-15
Thanks for that suggestion but all the issues makes it somewhat daunting. I'll keep it in mind and will check it out in the future. The one I found, pyBackPack seems to be doing exactly what I want without all the installation hassle.

---

### Post by Revolutionary101 on 2009-08-15
> **Sidewinder1 said:**
> I'm not familiar with Cobian,... I use GRSYNC, it's a GUI front-end to the rsync command in terminal. You will find it in the Synaptic repositories.
HTH, Side

Thanks I was also looking for a backup utility. I have installed grsync and it works perfectly.

---

### Post by Sidewinder1 on 2009-08-15
Glad to have been of assistance.
Side

---

### Post by scouser73 on 2009-08-15
You can also look at [[COLOR="Red"]**Pybackpack**[/COLOR]]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html").

---

