---
title: "help 9.10 down"
date: 2009-11-27
forum: General Help
---

### Post by bigtone86 on 2009-11-27
I think this may be my own fault but here goes. Yesterday I decided to install a prog called anymeal from the accesories menu (add/remove prog) all went well untill I opened up anymeal and tried to see how the database worked, I clicked on an icon and K wallet appeared. I decided to do a search online about it and, firefox would not open. I decided then to remove the offending prog but, the add/remove would not open either. At this point I did a system reboot. The reboot went as usual untill it reached the desktop screen, all I got was a black screen and the curser(busy)
the following message apppeared

"failed to contact configuration server, some possible causes are you need to enable tcp/ip networking for orbit or you have stale nfs locks due to a system crash. see [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for info , (details-1:could not send message gconf daemon/process/usr/lib/libacon f2-4/a confd-2 recieved signal 11)"

I have looked up the web page above but  it did not help me much as I cant access the terminal

Any help on this matter would be much appreciated...........I am on a duel boot so I am writing this from the other side.

---

### Post by ikacer on 2009-11-27
> I have looked up the web page above but it did not help me much as I cant access the terminal
First off, I bet you can still access the console using ctrl-alt-F1 (note:the console Ubuntu usually boots up in is F7).

My guess is that the problem is with some config files in your home directory. If so, this should be easy to fix.
Here are a few things to try, the results could tell us a lot about your problem.
Can you boot up if you choose "failsafe GNOME" as your session at the login screen? If so skip the next part.
If not, try booting up recovery mode (you can use "startx" command to bring up a gui interface).  create a new user, restart normally, and try and log in on the new account (you can delete this account once you are done).

If either of these work, then the problem is almost certainly in you /home/USERNAME directory. Then, you can delete some config files there that you think might be the problem, and see if that fixes it. Just remember to backup anything before you delete it. From the error message, it might have something to do with gconf, so I'd try that file first.

---

### Post by bigtone86 on 2009-11-30
Thanks for the info. You were right about the console, I managed to access that ok. Tried "startx"but it still didn't bring up the gui and still had the same problem. I don't appear to have"failsafe GNOME"option at start up screen. I can access the system using the Ubuntu disk in virtual mode but, I cannot delete gconf files because permission is denied.
I think the easiest option would be to format the partition and reinstall. Thanks for taking the time to help any how.> bigtone.

---

