---
title: "can't uninstall damaged picasa installation"
date: 2011-01-15
forum: General Help
---

### Post by halfbeing on 2011-01-15
I accidentally deleted Picasa from /opt so I decided to remove it using apt so I could reinstall it. However it refuses to go because it depends on various files being there so it can delete them. I tried creating files with the right names, but it all got too complicated. How can I either uninstall Picasa or force it to reinstall its missing files?

This is the error message I got:

root@ermintrude:/# dpkg -r --force-all picasa
(Reading database ... 402182 files and directories currently installed.)
Removing picasa ...
/var/lib/dpkg/info/picasa.prerm: line 323: /opt/picasa/bin/killpicasa: No such file or directory
picasa.prerm:error: could not find xdg-desktop-menu in PATH or '/opt/picasa'
dpkg: error processing picasa (--remove):
 subprocess installed pre-removal script returned error exit status 1
cat: /opt/picasa/desktop/google-picasa.desktop.template: No such file or directory
cat: /opt/picasa/desktop/google-picasa-fontcfg.desktop.template: No such file or directory
cat: /opt/picasa/desktop/google-picasa-mediadetector.desktop.template: No such file or directory
cat: /opt/picasa/desktop/google-picasa.directory.template: No such file or directory
picasa.postinst:error: could not find xdg-desktop-menu in PATH or '/opt/picasa'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 picasa

---

### Post by jonbonjovi on 2011-01-15
Have you tried to simply re-install it? Where did you install it from? Google repo?

---

### Post by halfbeing on 2011-01-15
> **jonbonjovi said:**
> Have you tried to simply re-install it? Where did you install it from? Google repo?


Hi. I've tried telling it to reinstall but it tells me i have the latest version. I did get it from the Google repo. Maybe I should just wait for the next version to come out and let it update automatically.

---

### Post by jonbonjovi on 2011-01-16
Weird...the "re-install" command shoul reinstall the package even if you have the latest version installed. did you check the "damaged" packages in synaptic? maybe it appears in there.

Otherwise try to wait for the next version, maybe it'll just fix itself.

---

### Post by halfbeing on 2011-01-18
Thanks for helping me think this through :)

Google seems to have closed down dl.google.com so the repository has gone. I found a deb at [http://picasa.google.com](http://picasa.google.com), so I downloaded it, unpacked it and copied the files across to /opt. Then I uninstalled picasa via Synaptic and reinstalled it from the deb. A bit complicated, but there you go.

---

### Post by jonbonjovi on 2011-01-20
So you did solve the problem?

---

### Post by halfbeing on 2011-01-21
> **jonbonjovi said:**
> So you did solve the problem?

Yep! Thx once again for your help!

---

### Post by jonbonjovi on 2011-01-22
Write the [Solved] tag before the title of your first post ;)

---

### Post by halfbeing on 2011-01-22
> **jonbonjovi said:**
> Write the [Solved] tag before the title of your first post ;)

I can't work out how to edit the title.

---

### Post by andymorton on 2011-01-22
> **halfbeing said:**
> I can't work out how to edit the title.

I think you can mark it as solved using 'Thread Tools' at the top. :)

---

