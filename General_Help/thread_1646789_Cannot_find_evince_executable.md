---
title: "Cannot find evince executable"
date: 2010-12-16
forum: General Help
---

### Post by carbon512 on 2010-12-16
Searched everywhere, and I can find all kinds of evince files but no executable or "link to executable." I can find all the other ubuntu installs, like gedit, gimp, etc. in my /usr/bin folder. But not evince. Even though Document Viewer runs fine.

I need this because I installed Adobe reader (ugh) and it took over as the default .pdf reader. The simple ways of trying to return default application to evince did not work, so I searched here and found a solution (y'all rule) -- edited the mimeapps.list file. Worked great. .pdf files now open in Document Viewer by default again.

Except, Thunderbird is still using Adobe reader as default for pdf files, and to change that I have to browse to the program I want to use instead. (Evince does not show up in the "open with" options I get by right clicking.) Can't browse to evince or enter path because I don't know where it is and can't find it anywhere..

I tried re-installing the evince pkg but no change.

Any suggestions?

---

### Post by 3Miro on 2010-12-16
If you can start evince form the terminal (Apps -> Access -> Terminal), then you can type:

```
 which evince 
```

and it will tell you where the executable is. For me, it is:

```
 miro@xxxx:~$ which evince
/usr/bin/evince
miro@xxxxx:~$  
```

---

### Post by carbon512 on 2010-12-16
As expected, it tells me it is in

/usr/bin/evince

but when I looked in that folder (using File Browser) evince didn't look like an executable. Showed as:
evince  - shared library

Looking at its properties, it shows as "shared library (application/x-sharedlib)"

But -- I told thunderbird to use it anyway, and it works. So all is good, thank you!

Before I mark this as "solved" I have a newbie question -- an "application/x-sharedlib" is an executable also, I guess? All my other binaries show up as executables, not shared libraries... and I am used to Mac "library" terminology meaning something else, thus the confusion...

And question #2 - Although I can force thunderbird to use evince or ask me now, Adobe Reader still shows in bold as "default." Rrrgh Adobe. Where is this still coming from? I have removed Adobe Reader entirely from my mimeapps.list file and there is nothing in my mimeinfo.cache file at all. Adobe Reader itself has nothing in its preferences about "set as deafult."

thanks!

---

### Post by 3Miro on 2010-12-16
You are right, it does say shared library. The concept of what gets labeled as "executable" or "shared library" exists at the level of the graphical environment. Linux cares more about permissions than file type, any file can be executed (or at least attempted) if it has its permissions set. The global shared libraries are registered via ldconfig, which is a different thing. I am suspecting a bug here, but I have to do some more reading.

To change default "open with" application, you right click on the file -> properties and use the "open with" tab. This will be activated for all files that associate with this file's type (however, the graphical environment registers those file). If document viewer doesn't show, you can add it from "other" (select /usr/bin/evince).

If you have done that for the system, then I don't know why Thunderbird would have a mind of its own. It is possible that you have to change a setting in Thunderbird itself to fix this (look at .thinderbird and/or .mozilla, but I don't know how much about Thunderbird).

Maybe someone else can give you a better answer on those questions.

---

