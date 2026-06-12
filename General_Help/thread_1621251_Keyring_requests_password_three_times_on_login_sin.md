---
title: "Keyring requests password three times on login since upgrading to Maverick"
date: 2010-11-14
forum: General Help
---

### Post by chargrims on 2010-11-14
Hello,

Simply as the title says, when I boot up my password is requested three separate times by the keyring. Sometimes if I have left my computer to boot up it will actually be requested four times.

I get the impression it relates to start up programs, for example if I leave it so that it requests the password a fourth time, at the same time the wifi connection settings pop up requesting the wifi password.

I remember having a similar problem before and I think I was able to set a program as always having access to the keyring once logged in, but I can't remember or find how to do this.

The programs that are maximized on startup are; transmission, liferea. Docky and gnome-do are also arranged to load on startup.

---

### Post by mister_playboy on 2010-11-14
System > Perferences > Passwords and Encryption Keys

How many keys are listed?  Deleting any ones other than the "login" one should solve this issue by re-associating the keyring with your login.

This issue also can occur anytime you change your password.

---

### Post by chargrims on 2010-11-15
There are two folders listed under 'passwords';

Passwords: default
Passwords: login

When I unlock the latter, there is one entry which says 'unlock password for default keyring'

Under 'Passwords: default' there are many different entries.

To add to the plot my system now no longer boots to the desktop and instead goes to the login screen, but instead of requesting a user and password it simply says 'Automatically login' and pressing enter goes to the desktop.

---

### Post by fragos on 2010-11-15
> **chargrims said:**
> There are two folders listed under 'passwords';

Passwords: default
Passwords: login

When I unlock the latter, there is one entry which says 'unlock password for default keyring'

Under 'Passwords: default' there are many different entries.

To add to the plot my system now no longer boots to the desktop and instead goes to the login screen, but instead of requesting a user and password it simply says 'Automatically login' and pressing enter goes to the desktop.

Same here but I noticed two "Desktop Couch user authentication", one has details tab basic and the other oauth. I wonder if that has anything to do with it. This system was an upgrade to 10.10 from 10.04. My laptop was a 10.10 clean install which doesn't have this issue.

---

### Post by chargrims on 2010-11-16
This system was a clean install, although the home partition was left as is - this has caused some permissions problems during previous upgrades.

I tried changing the login keyring to be set as default, but now even though I've changed it back, I get a message on login saying 'The default keyring did not unlock' which requests the password again.

---

### Post by chargrims on 2010-11-22
Have now resolved the latter complication re: the login screen. Went in to System/Administration/Login Screen and "Allow 10 seconds for anyone else to log in first" had become checked. Unchecking this causes a boot straight to desktop and the message re: the default keyring not unlocking has now gone.

However I'm back to the problem as originally presented. Can anyone help?

---

### Post by joelzehring on 2010-11-26
I have the same issue. With Automatic Login activated, I get three separate password requests once my desktop loads up.

---

### Post by godparn on 2010-11-28
Same issue here, upgrade to 10.10 from 10.04, anyone can help?

---

### Post by jfred99 on 2010-12-02
Identical issue moving from 10.04 to 10.10 via Update Manager on SonyVIAO COREduo.  I only have a login keyring and I've tried changing the password and rebooting to no avail.  

Just annoying really.

---

### Post by mister_playboy on 2010-12-03
My other idea is to delete the files located in your ~/.gnome2/keyrings folder.  If you logout and back in, you should have to enter your password to rebuild the keyring... hopefully that will stop the password prompts.

---

### Post by fragos on 2010-12-03
> **mister_playboy said:**
> My other idea is to delete the files located in your ~/.gnome2/keyrings folder.  If you logout and back in, you should have to enter your password to rebuild the keyring... hopefully that will stop the password prompts.

Thank you very much -- back to a single a single keyring login.

---

### Post by ekennes on 2010-12-19
deleting keyrings worked but then the problem came back

---

### Post by cknoettg on 2010-12-19
This is not a solution, so much as a workaround/note. I had the problems that everyone in this thread has described when upgrading from 10.04 to 10.10 - asking for password logins multiple times, having to close out of the authentication screen when installing some programs, etc. I then wiped my 10.04 and 10.10 completely, and then reinstalled a clean version of 10.10, and the bugs have not come up once. I know it's not a fix per se, but that's what happened.

---

### Post by fragos on 2010-12-19
FYI: I uninstalled gwibber and one of my keyring logins disappeared.

---

### Post by meluxx on 2010-12-24
I have 10.10 clean install
and have to enter 4 times keyrings password, it's really annoying.

---

### Post by meluxx on 2011-01-12
Still no solution?
I dont know what to do, dont really want to disable it, too big security risk.
i really dont want to install ubuntu again because of this

---

### Post by ibbuntu on 2011-01-15
Does anyone know if there's a bug report for this? I haven't been able to find one. Even with a clean install of 10.10 I am still getting this issue.

---

### Post by rdingram on 2011-01-17
I am having the same issue here. My home partition has been unchanged for several different installations so there are always a couple of glitches here and there, but this one is perplexing. Should a bug report be submitted somewhere?

---

### Post by fragos on 2011-01-17
I finally did a new clean install but my happiness that I no longer had multiple keyring logins was short lived. After enabling empathy my first keyring log in appeared -- no surprise. A day later I enabled Ubuntu One and now have two keyring logins. No doubt enabling gwibber would add a 3rd. The cause seems clear to me -- every function that depends on keyring adds another login. It should be noted that with my last install when I uninstalled gwibber, one of my keyring log ins went away.

---

### Post by jook on 2011-02-16
I did ```
rm ~/.gnome2/keyrings/*
``` and it took care of the problem. Thanks!

---

### Post by puca mor on 2011-03-01
Thanks Jook! Can't believe that worked - i've been typing my pw three times for so long, it's a real treat just to enter it once! :P Now if i could just get the wireless working properly...

---

