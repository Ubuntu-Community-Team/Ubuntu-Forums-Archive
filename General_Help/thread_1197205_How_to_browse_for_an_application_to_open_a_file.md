---
title: "How to browse for an application to open a file?"
date: 2009-06-25
forum: General Help
---

### Post by mahela007 on 2009-06-25
Sometimes when firefox downloads a file it doesn't know how to open it and I have to manually browse though the folders to find the correct application.. In windows this is straightforward ,as all I have to do is go to program files and select the .exe file. Which folder should I go to to see the "program files" of kubuntu, in order to select an application?

---

### Post by Tyke91 on 2009-06-25
/usr/bin holds all the binaries for your installed apps. 
/bin holds all the binaries for your system commands.
/sbin holds all the binaries for your administration commands.
/usr/sbin holds all admin commands that you separately install (i think)

hope that helps :)


for example, firefox is actually /usr/bin/firefox, vlc is /usr/bin/vlc , ifconfig is /sbin/ifconfig

it takes some getting used to, but having the central folder for all binaries is pretty handy.

---

### Post by mahela007 on 2009-06-26
thanks.. 
are binaries the equivalent of .exe files in windows?

---

### Post by lisati on 2009-06-26
Try right-clicking on the file you wish to open within the "download" window then click on "open containing folder".

---

### Post by decoherence on 2009-06-26
> are binaries the equivalent of .exe files in windows?

Sometimes. In UNIX world, there are only two types of file: Binary and ASCII text. Either one can be executable... an executable binary is like a .exe whereas an executable text file is like a .bat.

---

### Post by Cheesemill on 2009-06-26
If you know the name of the application you can find out where the binary is using the which command. For example:
```
which firefox
```
will return
```
/usr/bin/firefox
```

---

### Post by mahela007 on 2009-06-27
wow... Thanks..
oh by the way , the same message pops up even when I click "open containing folder"

---

### Post by joshedmonds on 2009-06-27
[URL="http://support.mozilla.com/en-US/kb/Managing+file+types?style_mode=inproduct"]http://support.mozilla.com/en-US/kb/Managing+file+types?style_mode=inproduct
[/URL]
> When you tell Firefox to open or save the file and also check the option to "Do this automatically for files like this from now on", an entry appears for that type of file in the Firefox Applications panel

If you find a particular file type comes up regularly, make sure you check this option. You can always change the default behaviour in Edit>Preferences>Applications

---

### Post by SuperSonic4 on 2009-06-27
> **mahela007 said:**
> wow... Thanks..
oh by the way , the same message pops up even when I click "open containing folder"

Yeah it would, you;d need /usr/bin/dolphin for that :p

---

