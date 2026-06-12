---
title: "How to open Windows XP event logs?"
date: 2006-04-13
forum: General Help
---

### Post by SimpleNL on 2006-04-13
My Windows system has crashed all of the sudden (thank god for my Ubuntu partition!), but I would like to read the event logs that are stored in Windows (c:/windows/system32/config/system.log), but I was wondering with what program I could do this? I've searched google, but I couldn't find a thing, so I was hoping somebody here knew.

---

### Post by stuporglue on 2006-04-13
Is it not just a text file? Can you do it with Vim or gedit?

---

### Post by Ramses de Norre on 2006-04-13
I tried with gedit, less, vi but they all display weird caracters, so I guess windows has some kind of a codec to read it..

---

### Post by SimpleNL on 2006-04-13
Yeah, I guess it is in some sort of codec, I tried with gedit, and with OpenOffice Writer (trying different encodings), but i would only get pages of #, and at the top it would say in scattered letters Windows xp config

---

### Post by stuporglue on 2006-04-13
Navigate to it in a terminal and run "file" on it "file syslog.log". It'll try to tell you a bit more about it. Maybe it's zipped or something?

---

### Post by xenmax on 2006-04-13
It seems it is a darn windows registry file. I guess one can use wine and regedit.exe to view. Another idea might be to take file to another windows machine and viewing it. I searched for a linux app that could read win registry files, but to no avail.

---

### Post by SimpleNL on 2006-04-13
[QUOTE=xenmax]It seems it is a darn windows registry file. I guess one can use wine and regedit.exe to view. Another idea might be to take file to another windows machine and viewing it. I searched for a linux app that could read win registry files, but to no avail.[/QUOTE]

Well, I tried to copy it to my roommates computer, and tried to open it with regedit.exe, but didn't wuite understand... And then I tried to open it with an event viewer, on his computer, but it said it was corrupted... I'll Install Wine and see how that works...

---

### Post by xenmax on 2006-04-13
My bad. The output of "file" command said it was a NT registry file. But it looks like its better viewed using event viewer like you tried. if eventvwr on your friend;s comp said its corrupted...
i tried to view my system.LOG in regedit under wine - like you said, its hard to see whats going on in registry display
i tried bringing up eventvwr.exe in wine - wine could not do it - threw a bunch of errors. And it can't bring up compmgmt.msc either.
Hope you have better luck.

---

### Post by stuporglue on 2006-04-13
You could try using the comand "strings filename" . Strings will print to the console any strings it finds in the file. Do "strings filename > outputstrings", then view outputstrings if you'd like to look at them with a bit more leasure. 

Good luck

---

