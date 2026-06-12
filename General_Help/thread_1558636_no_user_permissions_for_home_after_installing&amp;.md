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

### Post by Old *ix Geek on 2010-08-23
> **dsikl said:**
> the end result: three warning messages at logon

- Could not update ICEauthority file /home/dsikl/.ICEauthorityCheck its permissions. At a command prompt:
```
ls -al ~
```
If the file .ICEauthority isn't rwxrwxrwx:
```
chmod 777 ~/ICEauthority
```

> - There is a problem with the configuration server. (/usr/lib/bgconf2-4/gconf-sanity-check-2 exited with status 256)Are you sure it's /usr/lib/**bgconf** and not /usr/lib/**libgconf**? If it's the latter, this may solve the problem--I read this in [**_another thread**_](http://ubuntuforums.org/showthread.php?t=1061084). Again, at a prompt:
```
chmod 1777 /tmp
```

> - Nautilus could not create the following required folders: /home/dsikl/Desktop, /home/dsikl/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.At a prompt:
```
ls -al ~
```
Do the two files exist? If so, what are their permissions? Change them to:
```
chmod 777 ~/Desktop ~/.nautilus
```

Log out and back in and see if the problem is solved.

> i would be happy to do a clean installThis isn't windoze. In the *nix world reinstalling the OS to fix problems like this should not be necessary.
> but there's one spreadsheet in the documents folder which i desperately need and i really need to get a hold of it before formating.Assuming the above ideas don't solve the problem, boot from a live CD and choose the option that doesn't change anything on your hard drive. Navigate to your document and save a copy of it on a USB drive or whatever (e-mail it to yourself if that's the only way you can save it).

And for future reference: If you partition your hard drive into separate sections for the OS and data, you wouldn't need to format the partition containing your data for a problem like this.  I always follow the same partitioning scheme when doing a new install:

/ -- for the OS; doesn't need to be huge; on a 300GB disk I might allocate 25GB

/home -- for user directories and data; on a 300GB disk I might give this 125GB

/data -- for whatever--I store images, videos, downloads, backups, etc. on this; on a 300GB disk I'd give it the remainder of space, 150GB

swap


Following this scheme you can safely and without worry do a clean install, formatting ONLY / and not losing any of your data.

---

### Post by dsikl on 2010-08-23
thank you so much Old *ix Geek for your help! i couldn't really do most of it at first, 'cause i had no access to the folders or rights whatsoever, but the thing with libgconf (chmod 777 /tmp) worked (and it was libgconf, not bgconf, sorry about that), and after a restart i had the normal desktop back, and could even execute the rest of your commands.......

however, either all the files got somehow lost, along with most of the system settings etc. (it still doesn't have my wlan data for instance), or i still don't really have access to the /home folders, at least not to the files? 'cause the folders are now there (desktop, documents, downloads etc.), but they're completely empty and i still have the two files ('access-your-private-data.desktop' and 'readme.txt' or similar) in the /home/dsikl folder, along with all the above mentioned empty folders........weird.............

i went to unwrap my passphrase and i have it now, but it doesn't seem to want to accept it for some reason.........i tried both with 'access-your-private-data.desktop' and with 'ecryptfs-mount-private' at command prompt........checked a thousand times, retyped, did everything, no success.

the thing with the livecd you suggested - that doesn't work, because i checked the "request password to access my /home folder" or similar at installation...........is there a way around it? i suppose not, but hey...........i'm a total noob

so i've definitely come a long way with your help, but i'm somehow still missing that little bit to get to the file.........any fresh ideas?

many thanks in advance!

dsikl

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

this brought me to a stage where i had my desktop the way it was, but  still couldn't see no files in my folders, local keyring was completely  left out etc.

2. oldfred's suggestion to try getting back the ownership over .dmrc and my /home folder ([complete article]("https://help.ubuntu.com/community/dmrcErrors")):

chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
chown username:username /home/username
chmod 755 /home/username

Thank you Old *ix Geek, thank you oldfred

A MILLION!!!

dsikl

---

