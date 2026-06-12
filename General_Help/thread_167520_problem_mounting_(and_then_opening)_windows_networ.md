---
title: "problem mounting (and then opening) windows network shares"
date: 2006-04-28
forum: General Help
---

### Post by kupajava on 2006-04-28
I am not new to linux (just new to Ubuntu) and have dealt with more than one Linux SysAdmin with this issue, all of them are scratching their heads on this...

I can browse my windows server 2003 network shares through nautilus, but they don’t appear in file operation dialogs. What this means is that although I can see the individual network files, I have to save to the desktop and then copy over to the network share (and vice versa) - I can’t navigate to the share through the save dialog.

So I tried to mount the share to a local directory.

When I manually mount in the terminal screen, everything goes fine and without errors in the terminal screen but when I navigate to the mount, the folder is displayed as a unknown file and I get an access denied error (even with a gksudo nautilus browser) trying to open it. I'm pretty certain this cannot be the windows side since I can browse this server in nautilus using "connect to server" and everything opens just fine.

any ideas? Im sure I am just missing something obvious but just cant to get it!](*,) 

also, I have also tried the whole Mount Windows Shares Permanently with fstab method (//servername/sharename /media/mountname smbfs defaults,uid=1000,gid=1000,credentials=~/.smbcredentials,umask=777 0 0) with the same result. no errors in the terminal with mount -a, but as soon as I navigate to the mount point the folder I created becomes an unknown file that wont open. I know the credential file is correct, since it wasnt the first time (wrong case pw) and it errored in the mount -a dialog. I even get the desktop icon for the mount but it gives me a system error beep and no response when I doubleclick it.

---

### Post by kupajava on 2006-04-28
also, before trying to mount again I changed the permissions on the folder for the mount with:
sudo chmod 777 -R /media/mount (I didnt the first time) with the same response
(where mount isnt actually the name of the mount folder, just using it as an example)

This is actually what I consider to be the last problem before having a full working Ubuntu setup and it has taken me 2 days of ](*,) and no luck whatsoever.  I feel like I havent  made any real progress with this one.  Im not new to Linux but this is my first time with Ubuntu and my first time to have to mount a Win2k3 Server share.  ANY IDEAS? "...Im losing IT!" :???:

---

### Post by djsroknrol on 2006-04-28
Just a suggestion...check System>Administration>Services...I found my samba unchecked there after a recent install...just a thought so you don't loose it..:)

---

### Post by kupajava on 2006-04-29
Thanks for the suggestion bro, but unfortunately, it is there and it is checked (I think it has to be for nautilus to see the server, but I am not sure) and every line of the samba conf checks out.  This is crazy since I was able to do exactly what I am trying to do with another machine running debian using KDE on my network, I can see the shares when browsing from "connect to server" in nautilus, and still, in Ububntu I get a folder that becomes a file I cannot open with nautilus in root mode.  This makes no sense and it really su**s since I have ubuntu running on this client now and everything else is running great (it rocks!).  I have spent so much time on this and done so much research (the upside being that I am much more proficient in command line now) and still, nothing.  Even other people I know who are linux competent are scratching their heads with this one. Without being able to access my W2k3 server with most of my apps this problem with Ubuntu is a deal breaker on this network.  I hope someone has something on this...  If anyone has anything at all on this please let me know because otherwise I cannot see any other option than using a different distro.  Maybe if no answer exists I can just try ubuntu with a later and more robust distro.  I hate this so much since everything else is so good!  Anyone?!?

---

### Post by kupajava on 2006-04-29
I think the solution might actually be to use "cifs" instead of "smbfs" in the line.  I simply replaced smbfs with cifs exec in my fstab file and the link sprang to life. I read about this in a really old forum about 20 pages into a google search.  This workaround was discussed in a forum for the build before hedgehog.  It seems to work but according to the person who posted it, it might be unstable for some reason. The post was from about a year and a half ago and was never updated with an alternative solution or what or how it was unstable.  Any ideas about this?

---

### Post by kupajava on 2006-04-30
Anyone know why cifs would work in this situation and not smbfs?

---

