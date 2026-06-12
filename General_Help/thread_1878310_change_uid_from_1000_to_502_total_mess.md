---
title: "change uid from 1000 to 502: total mess"
date: 2011-11-09
forum: General Help
---

### Post by ibokg4 on 2011-11-09
Hello

I have an ubuntu 11.10 install. everything works, expect that i didn't have acces to my documents on the hfs+ partition named "Macintosh HD" . the hd is mounted ok but i don't have access to my files.  the problem is that my osx user has a different uid. on osx my user has 502 on linux 1000. 
my goal was to have the same id and i changed uid in linux to 502:

my steps:
- logged in as a different user
- activated root
- logged in as root

usermod -u 502 myuser

- deactivated root 

PROBLEM: myuser is not available on login screen. i choose "other..." login choosing myuser, gnome-session  and password .

login suceed but unitiy is started (not gnome). all my settings are ignored. in the user-menu on top there is not my username but "[INVALID UTF-8]" displayed. The only thing that works now is that i have access to my files on "Macintosh HD" yeah thats nice... but my nice gnome ubuntu system is messed up!

it really looks like a big mess. how do i fix this. (change uid back to 1000 maybe ?, but how to fix the uid mismatch when accessing hfs+ volume ?)
are there any other files i have to change permissions ? the man page for usermod tells that it changes the ownership in home directory. is there a tool on linux that checks if the permissions are ok and repairs them (like disk utility on osx) ?

thanks for help

stefan

---

### Post by dcstar on 2011-11-10
> **ibokg4 said:**
> Hello

I have an ubuntu 11.10 install. everything works, expect that i didn't have acces to my documents on the hfs+ partition named "Macintosh HD" . the hd is mounted ok but i don't have access to my files.  the problem is that my osx user has a different uid. on osx my user has 502 on linux 1000. 
my goal was to have the same id and i changed uid in linux to 502:
.........

Never, **ever**, muck around with the default account.

Boot off a live CD and try and edit the /etc/passwd entry for that user back to 1000:1000, then:

[http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write](http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write)

---

### Post by ibokg4 on 2011-11-10
Hi David

Thank you for your answer.
I notice, never change uid of user 1000.
Anyone knows a good reference about those ubuntu / linux guidelines (e.g. default user, groups permissions, what to change what not) ?

Is there a tool on linux to repair permissions (like "Disk Utility" in OSX") ? It would be useful for me to get sure that everything is ok after the uid rollback. If there's no tool, a checklist might be useful.

---

### Post by dcstar on 2011-11-10
> **ibokg4 said:**
> Hi David

Thank you for your answer.
**I notice, never change uid of user 1000**.
Anyone knows a good reference about those ubuntu / linux guidelines (e.g. default user, groups permissions, what to change what not) ?

Is there a tool on linux to repair permissions (like "Disk Utility" in OSX") ? It would be useful for me to get sure that everything is ok after the uid rollback. If there's no tool, a checklist might be useful.

Sorry, I misread your issue (look at the **title** of this thread), but you did say that you changed the UID of "myuser", so what is the reality of the situation?

As far as any "reference", there are various things that state what should not be touched in Unix/Linux going back many years, but you really need to look at each specific area.

Users with UIDs below 1000 will not appear on the login screen, that is by design.

Basically Linux gives people the capability to stuff up working systems, there is no real tool that I am aware of that will take snapshots and let you "roll back" apart from making backups and restoring them after things go wrong.

---

### Post by ibokg4 on 2011-11-10
i misspelled sorry the first question is correct. and i
only nee **read-only** access, no write access. Disable
journaling don't fix the uid mismatch between my osx user and the linux user.

therefore changed uid for user "myuser" from 1000 to 502 (to match the uid of the osx users).

the 2. answer from superuser.com (your [link]("http://superuser.com/questions/84446/how-to-mount-a-hfs-partition-in-ubuntu-as-read-write")) has the solution i have chosen. Maybe I just have to do the last part:

> 
sudo chown -R 501:yourusername /home/yourusername

You may also want to fix your login screen, since by default Ubuntu won't list users with a UID of less than 1000. To do this, just open a Terminal and run gksudo gedit /etc/login.defs and search for UID_MIN in the text file. Change that value from 1000 to 501, and when you reboot your user will be listed in the login screen.

I try it this evening and write the result here.

Thanks for your help
Stefan

---

### Post by ibokg4 on 2011-11-10
Tried the solution from superuser.com (leave uid at 502 and edit /etc/login.defs)

Works perfectly.

Thanks.

---

