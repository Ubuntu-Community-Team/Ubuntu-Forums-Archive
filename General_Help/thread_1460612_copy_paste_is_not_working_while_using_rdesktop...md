---
title: "copy paste is not working while using rdesktop.."
date: 2010-04-23
forum: General Help
---

### Post by python.noob on 2010-04-23
Hello all,

          I've tried rdesktop and grdesktop.. But i can't do copy and paste operation **within windows XP** machine.:( Hope u've understood my problem.. 

Looking for your replies..

---

### Post by python.noob on 2010-04-26
May i know why i'm not getting any replies?? :confused::confused: . Confused..

---

### Post by Lazy123 on 2010-05-07
Same problem here. Using rdesktop from 64bit Lucid to Win 2003.

---

### Post by cviorel on 2010-05-07
Try using these options for the **rdesktop** command:
```
-5 -K -r clipboard:CLIPBOARD
```

---

### Post by zajc on 2010-06-14
I had exactly the same problem on Windows Server 2008.
I've read this blog [http://www.gfi.com/blog/copy-paste-working-remote-desktop-connection-whats-wrong/](http://www.gfi.com/blog/copy-paste-working-remote-desktop-connection-whats-wrong/) and did exactly what is says.

>    1. Load up task manager (right click taskbar and select Task Manager)
   2. Go to the Processes Tab
   3. Select rdpclip.exe
   4. Click End Process
   5. Go to the Application Tab
   6. Click New Process
   7. Type rdpclip
   8. Click Ok


Probably restarting server would help too. Now I'm happy copy-pasting.

---

### Post by thirdy on 2012-01-26
Thanks, this worked for me, using 11.04 unity

> **cviorel said:**
> Try using these options for the **rdesktop** command:
```
-5 -K -r clipboard:CLIPBOARD
```

---

### Post by dcstar on 2012-01-28
The **remmina** package works fine with Copy & Paste.

---

### Post by Habitual on 2012-01-28
rdesktop xxx.xxx.xxx.xxx -u Administrator -p password **[COLOR=Red]-r clipboard:PRIMARYCLIPBOARD[/COLOR]**

---

