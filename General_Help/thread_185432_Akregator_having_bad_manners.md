---
title: "Akregator having bad manners"
date: 2006-05-31
forum: General Help
---

### Post by tijs on 2006-05-31
Ever since I installed Dapper Drake (from Flight 3), I've been having problems with Akregator, the RSS reader for KDE.

Sometimes, when starting my laptop, this message comes up:

> Akregator already seems to be running on another display on this machine. Running Akregator more than once is not supported by the Metakit backend and can cause the loss of archived articles and crashes at startup. You should disable the archive for now unless you are sure that Akregator is not already running.

Then it gives me the options "Force Access" or "Disable Archive". The latter option just downloads all the feeds again, which is quite annoying. If you force access, sometimes it works, other times Akregator crashes badly. After the first crash there is no way to make Akregator work again apart from manually removing all the Akregator files in my home directory. Just reinstalling the program doesn't work. My Kubuntu installation is up to date by the way.

So, what can I do? This happens every once in a while and it is starting to drive me nuts and makes me want to ditch Kubuntu altogether (yes, RSS feeds are crucial for me and Akgregator is a nice program, when it works properly...). ](*,) 

Any help appreciated, I can't find anything in Google.

---

### Post by asimon on 2006-05-31
Yes, it's very annoying. I am lucky in that it doesn't happen often for me and forcing so far did always work too.

It's a known problem, see [bug 127076](http://bugs.kde.org/show_bug.cgi?id=127076). Note that this is not a Kubuntu specific problem, but an upstream bug. KDE 3.5.3 will have the fix.

EDIT: I just saw that KDE 3.5.3 is already out, and there are even [packages for Kubuntu 6.06](http://kubuntu.org/announcements/kde-353.php).

---

