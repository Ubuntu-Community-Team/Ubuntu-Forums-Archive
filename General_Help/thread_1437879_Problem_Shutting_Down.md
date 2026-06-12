---
title: "Problem Shutting Down"
date: 2010-03-24
forum: General Help
---

### Post by The Fridge on 2010-03-24
Hi all,

Last night I went to shut down only to be greeted by a message which told me that it was against system policy to shutdown when other users were logged in and that if I wished to do so enter my password. 

I tried cancelling and clicking shut down again only to be greeted by this message. I even tried logging out and logging in again but still got this message. I then hit the restart button on my machine, logged in again and when I clicked shutdown was displayed the normal message.

Unforunately I did not have the sense to take a screenshot or write down exactly what it said so I am only working from memory.

I have never encoutered this message before and had no idea what could have caused it. I hadn't installed anything or (knowingly updated the machine) in fact I didn't even use the sudo command or enter my password for anything other than logging on or opening the Firestarter GUI. The only account that I have created is my own account, I don't have any other accounts beside this.

I spoke to a friend in work who also uses Ubuntu and he said he'd heard about this happening to people running 9.10/Karmic but I am running 9.04/Jaunty. I am beginning to worry that I may have been hacked even though I've noticed nothing else suspicious I cannot account for the message. I am posting this from my work PC, so when I get home I will run a scan for rootkits.

Any help would be greatly appreciated.

EDIT: Ran chkrootkit an rkhunter, first came back with nothing at all, but rkhunter showed warnings in file properties check for /usr/sbin/unhide and /usr/sbin/unhide-linux26; a warning for checking dev for supsicious file types; and warnings for checking version of ofGnuPG and OpenSSL.

---

