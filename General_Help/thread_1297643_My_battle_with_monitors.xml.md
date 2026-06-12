---
title: "My battle with monitors.xml"
date: 2009-10-22
forum: General Help
---

### Post by jrrader on 2009-10-22
Hello all,

I don't normally post my questions because usually I can find the answers with a search but I've been struggling with this for a few weeks now.  I run Ubuntu (9.4 until 9.1 officially comes out) on all my computers and everything works just fine, but on my wife's laptop, which is a Toshiba Satellite L305-S5911, the resolution keeps changing on her user account.  The resolution (1280x800_60) starts fine for root and my own account, but on hers it starts at 1024x768.  She doesn't touch anything other than OpenOffice and FireFox so I know it's not something she's doing.   So I delete monitors.xml from /home/hername/.config and she can log in and out and the resolution is fine.  But when she turns the computer off and then on again, monitors.xml comes back and the resolution goes back to 1024x768. 

This is what I've tried:
1. I changed monitors.xml to specify 1280x800 - did not work.
2. I changed permissions to 000 - worked for two restarts.
3. I created an empty monitors.xml with 000 permissions - worked for maybe 5 restarts and then went back to 1024x768...
4. I created an empty monitors.xml with 000 permissions and gave ownership to root. - just did this so I don't know if it will work or for how long.

Any suggestions for a fix that will stop whatever is causing monitors.xml to do this?  Am I pointing my finger at the wrong file?

---

