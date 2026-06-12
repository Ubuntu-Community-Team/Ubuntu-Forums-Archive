---
title: "Integrating Kubuntu Workstation into RM Network"
date: 2006-04-06
forum: General Help
---

### Post by chrisdcmoore on 2006-04-06
Hi all,

I am a student attending a grammar school in England, and with the authority of my Sys. Admin will be installing Kubuntu on an old machine (previously running Windows 98 ) which no longer works due to the school upgrading from the RM Community Connect 2.4 to the CC3 framework (which uses Active Directory).

My intentions for the box are currently in a bit of a muddle, as I wish to have it authenticate over the network with the servers and work pretty much like the WinXP boxes do at the moment, but whether this is actually feasable or not is another matter. The sysadmin isn't overly keen on installing any new software on the server in order to add easier functionality for the box to connect, so it's up to me to get it working. Once users were able to auth and do the above, I would also need KDE to apply a Kiosk profile to all users (excepting root and an acc called "admin") in order to enforce proxy and restrict them from using Konsole, admin tools, adjusting Panel, etc.)

The only other alternative I could think of, was this not possible was having a permanent user on the box, with Kiosk limiting what he could do. The box would use dhcp to join the network at boot (tested) and kdm would be set to automatically log in the user "art" (we are putting the box in the art room) on startup.

Current layout of the network is a follows:
dbh-sr-001 ^|
dbh-sr-002    |- Fileservers
dbh-sr-003  _|
dbh-sr-ex1 -----Exchange server
dbh-sr-adm ---- admin server... not entirely sure what it does.. maybe domain controller?

I have done quite a bit of googleing on the subject, but not a lot of it makes that much sense to me (as I have yet had the chance to try any of it).

All help is welcome, and thank you in advance!

Chris

---

### Post by mcanada on 2006-04-07
Chris,

I think there a couple of resources on how to set up your computer with Active Directory. Here are a couple of links that I found on these forums...

[http://www.ubuntuforums.org/showthread.php?t=91510]("http://www.ubuntuforums.org/showthread.php?t=91510")
[http://www.ubuntuforums.org/showthread.php?t=5409]("http://www.ubuntuforums.org/showthread.php?t=5409")

I personally have only used the second link and I found that it works just fine with NT 4 authentication. There are people in that post saying that it works with Active Directory as well. Good luck.

---

### Post by chrisdcmoore on 2006-04-16
Thanks for your reply, I am sure these will be of great help.

We have had to wait until the new term starts next week due to exams taking place in the venue that the computer is situated in.

Will keep this posted on our progress.

Chris

---

### Post by chrisdcmoore on 2006-05-22
Ok, it didn't go too well...

I will try and get some logs to post because I have never studied AD in depth and don't know what some of it means.

What makes matters worse is that a load of students' stuff is on one server, and a load of others' on another (dbh-sr-00[123]).

Has anyone had any experience with RM networks that could lend me a hand?

Chris

---

