---
title: "&quot;Failed to download repository...&quot;"
date: 2012-01-01
forum: General Help
---

### Post by thulefoth on 2012-01-01
Update Manager fails with the message:  &quot;Failed to download repository information.  Check your Internet connection. Details E:Problem executing scripts APT:Update::Pre-Invoke 'if[-x/usr/bin/daptup];then usr/bin/daptup -pre;fi', E:Sub-process returned error code&quot;  I searched with portions of the error-text, and found the following suggestion;  sudo apt-get update -o Acquire::http::No-Cache=True  This executed in the Terminal.  I started Update Manager, and it quickly announced 3 security updates.  It has been 12 days since the last successful update.  These 3 downloaded & installed ok.  I then closed UM, started it again, had it check for updates ... and the original error repeats.  Synaptic and Software Center work normally.  I see no other issues at all.  This is a Wubi 11.04.  I survived massive Wubi meltdown, in 9.6.  I looked in Mega-Wubi, but do not see anything Wubi-based.  Thank you! (Hm.  The laugh-faces in the text were both the 2-letter set; "colon, capital-P".)

---

