---
title: "Device access rights hell for sr0..."
date: 2006-06-02
forum: General Help
---

### Post by tribaal on 2006-06-02
Hi there!

Experimenting with the advice obtained [here]("http://ubuntuforums.org/showthread.php?p=1082976"), I tried to fix a recurrent problem I have with gnomebaker: When I launch the program as a regular user (member of the cdrom group), gnomebaker tells me I do not have access to /dev/sr0.

So I thought hey no problems, I'll just "chown root:cdrom sr0"! Well I guess it's supposed to work, but then "ls -l" tells me sr0 is still owned by root:root...

And mind you, I did use sudo...

/dev/sr0 seems to be a link to /dev/scd0, and scd0 *is* owned by root:cdrom ...

Is there a special procedure to change group/ownership for links? 

I tried a "chmod a+rwx sr0" (to add rwx rights for everyone), which worked, but then a "chmod o-rwx sr0" (to remove rwx from anyone but owner) and a "chmod u=rwx sr0" (to make ower's rwx the only access) didn't work...
I'm really confused. Can someone remove that spine from my foot? ;)

Cheers

- trib'

---

### Post by jakev383 on 2006-06-07
[QUOTE=tribaal]Hi there!

Experimenting with the advice obtained [here]("http://ubuntuforums.org/showthread.php?p=1082976"), I tried to fix a recurrent problem I have with gnomebaker: When I launch the program as a regular user (member of the cdrom group), gnomebaker tells me I do not have access to /dev/sr0.

So I thought hey no problems, I'll just "chown root:cdrom sr0"! Well I guess it's supposed to work, but then "ls -l" tells me sr0 is still owned by root:root...

And mind you, I did use sudo...

/dev/sr0 seems to be a link to /dev/scd0, and scd0 *is* owned by root:cdrom ...

Is there a special procedure to change group/ownership for links? 

I tried a "chmod a+rwx sr0" (to add rwx rights for everyone), which worked, but then a "chmod o-rwx sr0" (to remove rwx from anyone but owner) and a "chmod u=rwx sr0" (to make ower's rwx the only access) didn't work...
I'm really confused. Can someone remove that spine from my foot? ;)

Cheers

- trib'[/QUOTE]

I added this to my rc.local file (before exit 0):
chmod 777 /dev/scd0
change scd0 for whatever your burner is mounted to. This solved the writing problem for me.

---

