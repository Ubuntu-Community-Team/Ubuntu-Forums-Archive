---
title: "Tweaks regarding Teamviewer 6"
date: 2012-01-04
forum: General Help
---

### Post by PyroFX on 2012-01-04
I have a couple of small issues that have arisen during my use of Teamviewer in 11.10. These are nothing major, but still annoying none-the-less.

If I open Teamviewer6 from the terminal, it opens Teamviewer and Wine in the side bar (if that is the term for it). On the other hand, if I open Teamviewer by clicking on the app icon (either by searching in Dash Home or browsing to the folder the icon is in) it only opens a Teamviewer icon on the sidebar. I'd like to be able to set Teamviewer as a startup application, but prevent the wine icon from popping up in the sidebar as well.

Also, I have been trying to see if there is a way to prevent Teamviewer from opening a webpage (asking me to sign up for the teamviewer newsletter) whenever I close it.

As I've said, these aren't incredibly important, but I would like to find a way to fix them if possible.

Thank you very much in advance!

---

### Post by imachavel on 2012-01-04
I believe the fact responsible for this would have something to do with the fact that ubuntu no longer uses a gnome interface. did I say this right? very sorry if I didn't. It uses another type of interface now, and uses grub 2 as the master boot record, or maybe not the master boot record but the partition loader select menu.

Sorry I'm rusty. Anyway the interface has nothing to do with the back end kernel loading files. But I have heard up and down that Ubuntu does something very wrong with take bars, menu bars, etc. with newer distros. I personally also use linux mint, and enjoy the interface, and believe the kernel root files are exactly the same.

as for your problem, I wouldn't know how to fix it, but look at this:

[http://www.liberiangeek.net/2010/04/how-to-install-teamviewer-on-linux-mint-and-connect-to-windows/](http://www.liberiangeek.net/2010/04/how-to-install-teamviewer-on-linux-mint-and-connect-to-windows/)

also if it works better from the terminal, open it from the terminal instead of the gui

---

### Post by PyroFX on 2012-01-04
> **imachavel said:**
> as for your problem, I wouldn't know how to fix it, but look at this:

[http://www.liberiangeek.net/2010/04/how-to-install-teamviewer-on-linux-mint-and-connect-to-windows/](http://www.liberiangeek.net/2010/04/how-to-install-teamviewer-on-linux-mint-and-connect-to-windows/)

also if it works better from the terminal, open it from the terminal instead of the gui

I have gotten Teamviewer to be a startup application, so that's not the issue. My problem is that the command that opens Teamviewer (and is used to make Teamviewer open at startup) also creates a Wine icon on the sidebar. If I instead start Teamviewer by clicking it's icon, it only opens a Teamviewer icon on the sidebar (no wine icon). I'd like to be able to open teamviewer from the terminal without also opening a wine icon on the sidebar.

---

### Post by howefield on 2012-01-04
What command are you using to start Teamviewer ?

---

### Post by PyroFX on 2012-01-04
> **howefield said:**
> What command are you using to start Teamviewer ?
 
"teamviewer6" (It is what the install suggested I use to open Teamviewer)

---

### Post by imachavel on 2012-01-04
> **PyroFX said:**
> I have gotten Teamviewer to be a startup application, so that's not the issue. My problem is that the command that opens Teamviewer (and is used to make Teamviewer open at startup) also creates a Wine icon on the sidebar. If I instead start Teamviewer by clicking it's icon, it only opens a Teamviewer icon on the sidebar (no wine icon). I'd like to be able to open teamviewer from the terminal without also opening a wine icon on the sidebar.

team viewer was originally an application designed for use with windows. which version of team viewer did you download? the version for windows? or the version for wine? if you downloaded the version for windows, the only way team viewer could open is with wine which funny enough stands for wine is not a windows emulator

if you downloaded the linux version then it shouldn't open with wine at all. That is a problem I'm sure of, but if team viewer connects just fine, then this thread is more of a wine problem then a team viewer problem. Have you tried modifying the properties in the wine config manager? set wine to not start with any programs, then try opening team viewer. if that fixes it, then try reconfiguring wine to only open certain programs.

---

### Post by imachavel on 2012-01-04
btw you had more luck then me:

teamviewer6
tee: /home/danel/.teamviewer/6/winelog: Permission denied
TeamViewer: 6.0.9258
Profile: /home/danel (danel)
Desktop: ubuntu
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric

that's what I got. also I installed the linux version. when I try with sudo it gives me the same problem. what can I say

---

### Post by howefield on 2012-01-04
Hmm, can't replicate the issue.

Neither using terminal or launcher to open Teamviewer opens a Wine icon.

---

### Post by PyroFX on 2012-01-04
> **imachavel said:**
> if you downloaded the linux version then it shouldn't open with wine at all. That is a problem I'm sure of, but if team viewer connects just fine, then this thread is more of a wine problem then a team viewer problem. Have you tried modifying the properties in the wine config manager? set wine to not start with any programs, then try opening team viewer. if that fixes it, then try reconfiguring wine to only open certain programs.

I downloaded the current .deb release from the Teamviewer website. I had the issue with a previously installed version of Teamviewer, so I uninstalled that versin (5, I believe) and installed the newer version.

I don't see any options in the wine configuration to not start with any programs.

---

### Post by PyroFX on 2012-01-04
I feel a bit dumb, but I just noticed that running the command to open Teamviewer doesn't open both a teamviewer and wine icon on the sidebar, it only opens a wine icon. The Teamviewer icon is already available as a quick launch option.

If I open Teamviewer via that quicklaunch icon, or by looking up the icon in my Dash, it simply uses that quick launch Teamviewer icon that is already on the sidebar.

My problem still remains, however, in that Teamviewer is opening with Wine for some reason when I use the "teamviewer6" command, this does not happen when I use the Teamviewer icon.

Also, I was able to make the web page from popping up by giving it my e-mail (I think I've already unsubscribed in the past, so I'll just have to do that again).

---

### Post by PyroFX on 2012-01-06
Not sure what to try, especially since howefield couldn't replicate this. I think I'll try uninstalling Wine to see if that does anything.

---

### Post by PyroFX on 2012-01-08
Uninstalled Wine and now Teamviewer opens a somewhat blurry Teamviewer icon on the launcher entitled "Teamviewer". 

When I upgraded to 11.10, it already had a Teamviewer icon available in the launcher entitled "TeamViewer 6" and if I open TV from the Dash by searching and clicking the icon there, it uses the same icon that already exists in the launcher. I even decided to open the folder to see what command is listed under its properties. If I run "/opt/teamviewer/teamviewer/6/bin/teamviewer" it still opens a new icon... 

I have no idea why an icon and an icon's command would open differently.

I know that I can just remove the existing launcher icon and that would prevent having two such icons from opening TV at start-up, but overall, I am asking these question out of curiosity. I hope I'm not annoying anybody by asking what might seem like meaningless questions.

---

