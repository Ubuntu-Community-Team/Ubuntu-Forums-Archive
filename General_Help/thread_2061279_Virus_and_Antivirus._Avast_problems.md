---
title: "Virus and Antivirus. Avast problems"
date: 2012-09-22
forum: General Help
---

### Post by Windoze Refugee on 2012-09-22
Hi
I recently started to suspect virus activity, so I installed Avast! for linux.
Job one, as per most antivirus apps, i downloaded the latest virus database, and applied it. The moment i ddi tho, Avast crashed and now will neither run nor allow me to uninstall. Ubuntu doesnt even see it in the file list

heres the error log:
"08:53:00: Deleted stale lock file '/home/jonathan/.avast/lockfile-jonathan'.
08:53:07: An error occured in avast! engine: Invalid argument"

Any ideas?

Cheers
WR

---

### Post by OrangeCrate on 2012-09-22
Though someone might come along with an answer for you here, you might be better served, if you post this on the avast! forums. There is a specific forum for avast! on Linux/Unix:

[http://forum.avast.com/](http://forum.avast.com/)

---

### Post by spaceshipguy on 2012-09-22
> **Windoze Refugee said:**
> Hi
I recently started to suspect virus activity..

What virus activity? I thought Ubuntu didn't get viruses :-(

---

### Post by krishna.988 on 2012-09-22
> **spaceshipguy said:**
> What virus activity? I thought Ubuntu didn't get viruses :-(

See these links ubuntu is virus free..

[https://help.ubuntu.com/11.04/ubuntu-help/net-antivirus.html](https://help.ubuntu.com/11.04/ubuntu-help/net-antivirus.html)

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by daslinkard on 2012-09-22
I definitely agree that you need to hop on over to the Avast forum to get support there.  As for me one of the reasons that I made the switch to Linux was so I didn't have to stay married to the AV companies such as Norton, Trend, Kaspersky, etc.  That and the fact I haven't had a BSOD in well over 18 months thanks to Linux!

I do not miss the days of Windows Update issues and malware seeping through the crack of the OS.

---

### Post by Buntu Bunny on 2012-09-23
> **daslinkard said:**
> As for me one of the reasons that I made the switch to Linux was so I didn't have to stay married to the AV companies such as Norton, Trend, Kaspersky, etc.....I do not miss the days of Windows Update issues and malware seeping through the crack of the OS.

Amen to that!

---

### Post by jimmac49 on 2012-09-23
Try this, it works for me.

Luck

---

### Post by jimmac49 on 2012-09-23
[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG] **(all varients) FIX the AVAST error engine failure after update.**  
   	Hello 	guys for those who dont have avast Linux here is the link to get it:
 	 	[HTML 	Code:]("http://www.avast.com/linux-home-edition#tab4")
 	[ http://www.avast.com/linux-home-edition#tab4]("http://www.avast.com/linux-home-edition#tab4") 	
get the .deb file for Ubuntu/kubuntu/xubuntu

ANyhow 	lately Avast has been crashing with engine errors. what i found out 	was that the problem was due to the fact that the size of the virus 	definitions database reached a system limit. it was a messup from 	avast linux team. that they overlooked this. Anyhow here is a quick 	way to fix it that will take you 30 seconds  	:smile:

[B]NOTE: 	KUBUNTU USERS USE KATE (instead of gedit) 
XUBUNTU USERS USE 	MOUSEPAD (instead of gedit)[/B]

1) open the terminal
2) 	a)type this command to open the file you need to edit:  	
 	 	Code:
 	sudo gedit /etc/init.d/rcS 	b) type your password and hit enter

3) when the text file 	opens add the line:
 	 	Code:
 	sysctl -w kernel.shmmax=128000000 	4) make sure the line you added is before:  	
 	 	Code:
 	exec /etc/init.d/rc S 	5.- This is how it should look like:
 	 	Code:
 	 #! /bin/sh     #     # rcS     #     # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order     #      sysctl -w kernel.shmmax=128000000      exec /etc/init.d/rc S 	6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST 	WILL WORK 100%
 
 Sorry Forgot the Attachment

---

