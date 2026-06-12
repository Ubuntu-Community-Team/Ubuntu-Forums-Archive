---
title: "Youtube videos won't play in Fireox 15.0.1"
date: 2012-09-25
forum: General Help
---

### Post by Neill_R on 2012-09-25
Ubuntu -server 12.04
Ubuntu-desktop
FireFox 15.0.1
Java jre1.7.0_07
java script enabled 

But no video vision or sound appears

Any one able to help debug my problem?

Neill

---

### Post by Statia on 2012-09-25
Did you install Flash? Or enable HTML5 in Youtube's settings.

---

### Post by Neill_R on 2012-09-25
How does one enable html5 on [www.youttube.com/user/username/](www.youttube.com/user/username/)
What flash and where do you mean a plugin if so which one?

---

### Post by Statia on 2012-09-25
To enable HTML-5 go here: 

[http://www.youtube.com/html5](http://www.youtube.com/html5)

(While logged in to your Youtube or Gmail account)

Yes, I meant the Flash plugin. 

```
sudo apt-get install flashplugin-installer
```

---

### Post by Neill_R on 2012-09-25
**This is an opt-in trial of HTML5 video  so [COLOR=Red]NO I did not get it. [/COLOR]**

sudo apt-get install flashplugin-installer
[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@newpc-server:~$ 

[/B]

---

### Post by Statia on 2012-09-25
They won't let you opt in?

As for Flash: if you type about:plugins in Firefox' location bar, is the Flash plugin there?

---

### Post by Statia on 2012-09-25
```
about:plugins
```

---

### Post by vasa1 on 2012-09-25
> **Statia said:**
> ```
about:plugins
```
Yes, we need to put certain stuff in code tags or disable smilies in text from the Additional Options located below the "submit reply" button.

---

### Post by Neill_R on 2012-09-25
**Shockwave Flash**

 File:  libflashplayer.soVersion:   Shockwave Flash 11.2 r202**Java(TM) Plug-in 1.7.0_07**

 File:  libnpjp2.soVersion:   [Java]("http://java.sun.com") plug-in for NPAPI-based browsers.**iTunes Application Detector**

 File:  librhythmbox-itms-detection-plugin.soVersion:   This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

---

