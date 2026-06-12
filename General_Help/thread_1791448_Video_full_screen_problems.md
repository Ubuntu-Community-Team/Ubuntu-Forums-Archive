---
title: "Video full screen problems?"
date: 2011-06-26
forum: General Help
---

### Post by trizrK on 2011-06-26
Hi,
When i go to view a video in full screen mode(with any video player youtube,metacafe etc.) the screen goes black and i cant get out of it but there is a tiny bar at the top that still shows the screen.
Any ideas??:confused:
Thank you

---

### Post by noah++ on 2011-06-27
I had a similar problem awhile ago. There are a few Flash plugins to choose from in Synaptic: an open-source one, a binary 32-bit one, a binary 64-bit one. I don't remember which I originally had or which I switched to, but I know that switching fixed it for me.

---

### Post by trizrK on 2011-06-27
> **noah++ said:**
> I had a similar problem awhile ago. There are a few Flash plugins to choose from in Synaptic: an open-source one, a binary 32-bit one, a binary 64-bit one. I don't remember which I originally had or which I switched to, but I know that switching fixed it for me.
Thanks, i'll look online.

---

### Post by nomko on 2011-06-27
Search for flashplugin-nonfree. It can be found in synaptic unless you added the medibuntu repository: [http://medibuntu.org/](http://medibuntu.org/)

---

### Post by lovinglinux on 2011-06-27
Install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and run the extension wizard. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance and fix common issues. If you still get that issue after running Flash-Aid, then click the extension "Help" menu, then "Generate Report". Attach the contents of the *firefox-report.txt* file saved in your Desktop, so I can analyse your situation.

---

### Post by trizrK on 2011-06-27
Thanks for the suggestions but there still seems to be no change.
But, it's only when i try and view it in fullscreen mode.
I'm lost here...

---

### Post by nomko on 2011-06-28
Did you also installed ubuntu-restricted-extras? It can be found in synaptic. Check if that is installed and if not, install it.

---

### Post by trizrK on 2011-06-28
> **nomko said:**
> Did you also installed ubuntu-restricted-extras? It can be found in synaptic. Check if that is installed and if not, install it.
That wasn't installed. Doing it now...

---

### Post by nomko on 2011-06-28
> **trizrK said:**
> That wasn't installed. Doing it now...
 
Keep us updated!

---

### Post by lovinglinux on 2011-06-28
Try to disable hardware acceleration in flash settings.

---

### Post by trizrK on 2011-06-28
Okay so the ubuntu-restricted-extras repostitory didn't seem to affect it. I disabled hardware acceleration and that worked great. Thank you very much. Now it seems kind of laggy in fullscreen mode but that is a different problem. Again thank all of you for the replies.

---

