---
title: "no user permissions for /home after installing&amp;removing xubuntu-desktop"
date: 2010-08-22
forum: General Help
---

### Post by dsikl on 2010-08-22
hi all, i'm having trouble with my fresh ubuntu installation (netbook edition).

what i did was install xubuntu-desktop on top of that (wanted to check it out)..........didn't really work for me, so i removed it, hoping this would also remove the xubuntu desktop logon screen, which i didn't like.

since this wasn't the case, i went to synaptics and removed all and everything with xubuntu in the title.

NOTE: in the same session i turned off password requests for login - it could also matter, but i'm not sure, so i thought i'd mention it.

the end result: three warning messages at logon

- Could not update ICEauthority file /home/dsikl/.ICEauthority

- There is a problem with the configuration server. (/usr/lib/bgconf2-4/gconf-sanity-check-2 exited with status 256)

- Nautilus could not create the following required folders: /home/dsikl/Desktop, /home/dsikl/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

i don't have access to my programs, administrator tools, /home folder, nothing.........the only thing that appears is the right part of the top bar (network, clock etc.), but also completely different.......it doesn't have my WLAN data anymore (can't access it), and all i have managed to get started was (accidentally) terminal with Ctrl-Alt-T, and from there I can use sudo, or even start nautilus, but can't access my own user, no matter what.........in the end i somehow managed to get to the point where it requested my passphrase, which i wanted to print out a day before it happened, but didn't and the screenshot is unfortunately within my /home folder.

i tried reinstalling xubuntu-desktop, even ubuntu-desktop, i repaired broken packages from the recovery mode, tried everything i could to get the bugger going again, no success yet.

i would be happy to do a clean install, but there's one spreadsheet in the documents folder which i desperately need and i really need to get a hold of it before formating.

any ideas, suggestions? could some sort of a rescue livecd help? i just need that one file..............the easiest would be if i could somehow repair whatever packages may be broken, or manually (with apt-get or similar) reinstall the additional xubuntu packages i manually removed via synaptics, but i wouldn't have a clue what those were... and would that help?

many thanks in advance!

dsikl

---

### Post by dsikl on 2010-08-22
sorry, double post, unintended...

---

### Post by earthpigg on 2010-08-22
> **dsikl said:**
> 
i would be happy to do a clean install, but there's one spreadsheet in the documents folder which i desperately need and i really need to get a hold of it before formating.

use whatever LiveUSB or LiveCD you installed ubuntu with, and boot from that.

find the data in the documents folder, drag and drop it to a thumb drive.

remove that thumb drive, and hit the install icon on the desktop.

for future reference, [this ought to help you]("http://www.psychocats.net/ubuntu/puregnome") out when experimenting with different DEs.

---

### Post by dsikl on 2010-08-23
thank you for your suggestion, earthpigg! unfortunately, that doesn't work, because i checked the option "request password to access my private folders" or similar, at installation........

i've managed to get a couple things done (have my desktop and private folders again), following the instructions by Old *ix Geek in the [original post]("http://ubuntuforums.org/showthread.php?t=1558636"), but the folders are still empty, i.e. i still can't access my files..........

greets! dsikl

---

### Post by oldfred on 2010-08-23
If related to moving /home or permissions on /home

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by dsikl on 2010-08-24
WHOOOOOOOOOOOOOOOHOOOOOOOOOOOOOOAAAAAAAAAAAAAAAAAA!!!!!!!!!!!!!!!!!!!

THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU!!!!!!!!!!!!!!!!!!!!!

that was it!!!!!!!!!!!!!!! ;DDDDDDDDDD

i know i'm ridiculous now, but hell i got all my data back and everything's the way it was!!!!!!!!!!!!

two things did it for me:

1. Old *ix Geek's suggestion (in [original thread]("http://ubuntuforums.org/showthread.php?t=1558636")) to try and chmod for /tmp to 1777 (from [another thread]("http://ubuntuforums.org/showthread.php?t=1061084")):

chmod 1777 /tmp

log out and back in and then

chmod 777 ~/ICEauthority
chmod 777 ~/Desktop ~/.nautilus

this brought me to a stage where i had my desktop the way it was, but still couldn't see no files in my folders, local keyring was completely left out etc.

2. oldfred's suggestion to try getting back the ownership over .dmrc and my /home folder ([complete article]("https://help.ubuntu.com/community/dmrcErrors")):

chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
chown username:username /home/username
chmod 755 /home/username

Thank you Old *ix Geek, thank you oldfred

A MILLION!!!

dsikl

---

