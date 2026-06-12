---
title: "firefox error"
date: 2009-09-10
forum: General Help
---

### Post by monkeyslayer56 on 2009-09-10
i probably did something i should not have done(i like the manual way :D) but now i got a problem. i donwloaded firefox 3.5.3 from the mozilla website and made a new ```
/usr/lib/firefox-3.5.3
``` folder and copyed the files into it and made the lnks for plugins and extensions(and whatever else was linked in the old firefox) and i cna lounch if by ```
./firefox
``` from within the directory but when i just do ```
firefox
``` i get ```
firefox
Couldn't read application.ini
``` i have copyed the firefox mozzilla-run.sh and firefox-bin files into ```
/bin
``` and ```
/usr/bin
```directories. i know what i did was probably stupid so please only constructive criticism and/or help please
PS im on 64bit ubuntu 9.04

---

### Post by hwttdz on 2009-09-10
Ask 
"which firefox"
then take a look at the firefox it's actually running if you just say firefox. What's likely happening is that it's a link to the old version of firefox which isn't hanging about anymore.  You'll likely need to update the link in /usr/bin/ .  Or at least that would be my first guess.

---

### Post by grizzler on 2009-09-10
Not absolutely sure here, but I *think* either of those executable files expects to find the file application.ini in the same directory it has been started from. It's probably better to leave everything in the installation directory (/usr/lib/firefox-3.5.3 in your case) and create a softlink **/usr/bin/firefox** which links to **/usr/lib/firefox-3.5.3/firefox**.

---

### Post by monkeyslayer56 on 2009-09-10
i know how to make a link(and did) but idk how to make a SOFTlink. is that diferent then a symbolic link and if so how do i make one?

EDIT:i made a link of the application.ini into the folders(/bin and /usr/bin) with the links to firefox and mozilla-run.sh and now i get
```
josh@josh-desktop:~$ firefox
Error: Platform version '' is not compatible with
minVersion >= 1.9.1.3
maxVersion <= 1.9.1.3
```

---

### Post by hwttdz on 2009-09-10
soft and symbolic are the same thing, -s

---

### Post by grizzler on 2009-09-10
It looks like you're turning a bit of a mess into a bigger mess. Leave the files in /usr/lib/firefox-3.5.3 as they are. Don't create copies of them elsewhere or link to any of them, except for the one mentioned in my earlier post. You (or I for that matter) do not know what else the executables want to find in the same directory.
Besides, as hwttdz suggested, there may already be a link /usr/bin/firefox which points somewhere else. Until you change that, starting firefox with the command 'firefox' just isn't going to work right.

---

### Post by monkeyslayer56 on 2009-09-10
ok well i cleaned my mess up a little bit and am back at the first error i mentioned. i have removed theother links and now only have the "firefox" link in /usr/bin and a few .so files in the lib directory(from erroes i was getting about them before the one i originally post about(file not foudn errors...)) i am still getting that error :(

---

### Post by grizzler on 2009-09-10
Strange. 

In your first posting you mentioned you copied all the files to the /usr/lib/firefox-3.5.3 directory and created links to parts of the original firefox. Could be something is interfering there. I assume the old firefox is in /usr/lib/firefox? Just to make sure the links aren't causing the problem, could you (temporarily) rename the old firefox (to /usr/lib/firefox-old or something like that) and unpack the tar.bz2 file directly with```
sudo tar -jvxf firefox-3.5.3.tar.bz2 -C /usr/lib
```
That should result in a 'clean' version in /usr/lib/firefox. Does that start properly? Don't forget to change the link in /usr/bin again.

---

### Post by monkeyslayer56 on 2009-09-10
ok i did that and linked "firefox" to /usr/bin and IT WORKED so then i copyed the links that were in teh old firefox directory so that my plugins would return(they did) and it working good. my guess it that the folder name through it off(firefox-3.5.3 vs firefox) thanks for your help :D

---

### Post by grizzler on 2009-09-10
You're welcome. Glad it's working.

I'm not convinced the name of the directory was the cause, though. My manually installed copy of Firefox is in /opt/firefox and that doesn't seem to matter. But I suppose one of the plugins you linked could have been looking in the wrong place...

---

