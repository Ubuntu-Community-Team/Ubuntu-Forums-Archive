---
title: "Facebook Plugin for Photo Uploads"
date: 2010-02-28
forum: General Help
---

### Post by jereece on 2010-02-28
I am trying to install the Facebook plugin to Firefox for photo uploads. I searched the forum and found [this solution]("http://blog.freus.net/2010/02/17/problems-with-facebook-plug-in-installation/") but it does not seem to work.  I manually copied the .so file to the .plugins folder but that does not seem to work either.

Any help is appreciated.

Jim

---

### Post by n0dix on 2010-02-28
Not is .plugins folder is /home/user/.mozilla/plugins/, it's different. 
uhhmm. The steps are very simple, do you get any error?

---

### Post by jereece on 2010-02-28
Okay..I got the dot wrong. My typo.  I put the .so file in the /home/user/.mozilla/plugins folder.      

Anyway, the plugin is in the correct folder.  I do not get any error messages.  Although I do not see it listed when I go into Firefox and choose Tools/Add-ons/Plugins.  I rebooted just in case it needed that to see the plugin.

Any other suggestions?

Thanks,
Jim

---

### Post by asai on 2010-03-01
I have the exact same problem. Any suggestions would be appreceiated.
;)

---

### Post by alexpotato on 2010-03-03
I had a similar issue:

-When using 8.04 and Firefox 3.0, firefox would freeze every time I tried to download the plugin
-Downloaded the plugin from another pc and just manually copied over the 1.0.1 plugin and it worked fine
-Apparently, there is a NEW plugin 1.0.3
-I upgrade to Firefox 3.5 and 9.10 so never tried the old plugin but now even with the new plugin in the correct location it keeps saying I need to install the plugin

No luck so far.

As a workaround, F-Spot has a Facebook Export plugin that works pretty well although it doesn't look like you can tag photos from F-Spot and you have to approve photos once they hit facebook. Better than using the old FB upload page though.

---

### Post by partofthething on 2010-03-07
Same story. 9.10 and FF 3.5.8. I emailed the address listed in the README file but it bounced back. (BTW, they're using MS exchange for email). Will be watching/posting here if I get it working. The old version worked for a week or something and it was actually pretty slick. Maybe a kernel update broke it.

---

### Post by ericmitz on 2010-03-07
Same issue here. I see this when I run firefox from the command line:

```

(firefox:2971): GLib-WARNING **: g_set_prgname() called multiple times
LoadPlugin: failed to initialize shared library /home/eric/.mozilla/plugins/libnpfbook_1_0_3.so [/home/eric/.mozilla/plugins/libnpfbook_1_0_3.so: undefined symbol: idna_strerror]

```

---

### Post by doml25 on 2010-03-11
Same here, anyone find a solution. 

I installed chrome and i have the same symptoms. 

I installed the latest java and javaplugin.

Updated FireFox.

Uninstalled and reinstalled Firefox.

Still no joy.

Currently using Ubuntu 9.10 and FF 3.5.8 and also Chrome 5.0.307.11

---

### Post by jereece on 2010-03-14
Bump...

---

### Post by DawieS on 2010-03-14
I have seen my daughter uploading photo's, 5 at a time, to Facebook. AFAIK there is no **plugin** installed for that. She does reduce the resolution of HD photo's to about 800 pixels with **Fspot**, and save them to a folder before uploading.

I will ask her tomorrow to make sure. (She's asleep now).:grin:

---

### Post by jereece on 2010-03-14
That's what I am having to do now.  However if the FB plugin worked, you can upload a bunch more and it's easier.

Still looking for a solution.

Thanks,
Jim

---

### Post by jereece on 2010-03-17
Bump.

---

### Post by jereece on 2010-03-23
Bump up.

---

### Post by jonnylinuxnerd on 2010-04-24
Bump from me as well! I have the same problem!

---

### Post by jereece on 2010-05-12
This problem is resolved in 4.10.

---

### Post by asai on 2010-05-18
> **jereece said:**
> This problem is resolved in 4.10.
What do you meen by 4.10?

---

### Post by jereece on 2010-05-18
Sorry..meant version 10.4 instead of 4.10.

---

