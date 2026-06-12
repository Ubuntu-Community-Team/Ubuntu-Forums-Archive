---
title: "Home folder permissions"
date: 2009-07-06
forum: General Help
---

### Post by Jugney on 2009-07-06
Hi all,

I'm running Ubuntu 8.10. Yesterday I was backing up my home folder. Not having found a backup solution that I liked yet, I simply started copying and pasting my entire user folder under "home" to a USB drive. This user is the administrator.

Quickly I got an error about permissions. So without really thinking, I opened up the properties on my user folder, set the "Group" permissions to "Create and delete files," clicked the button to apply these changes to enclosed files, and then tried again. The copying seemed to work, but my computer started behaving very strangely - namely it went very slow. Programs started hanging and going gray. 

I rebooted X a few times and each time the bootup and application speeds were very slow, and when X loaded I got a message about the file .dmrc not having the right permissions. As the box suggested, I used chmod to change permissions to 644, but still get the error on each load.

On shutdown, I saw error messages which unfortunately I didn't write down. But after 10-15 minutes, it was still shutting down, so I simply turned the computer off (also may not have been the smartest thing).

Today on fresh bootup, fsck said it needed to recover the journal on /dev/sda3, which is the separate partition for my /home folder. It completed and things seem to run at normal speed now, but I still get the message about .dmrc and imagine there are other problems remaining. 

Am I OK? Are there select files/folders that need to have their permissions restored to the default? Do I need to re-install?

Thank you,
Jugney

---

### Post by sisco311 on 2009-07-06
[thread=976610]Solving .dmrc and $HOME Permission Errors[/thread]

---

### Post by Jugney on 2009-07-06
Thank you!

---

### Post by Yleeyas on 2009-07-06
Thanx sisco, pointed me in the right direction also :)

---

