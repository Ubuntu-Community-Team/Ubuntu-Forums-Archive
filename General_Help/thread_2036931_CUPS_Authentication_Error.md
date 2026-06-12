---
title: "CUPS Authentication Error"
date: 2012-08-03
forum: General Help
---

### Post by Ubun2to on 2012-08-03
I have tried setting up a Sharp MX-3100N at a business, and the person in charge never thought of making sure the printer was supported for their Ubuntu server. Now, he is mad at ME for somehow messing with the settings so that he can't print from the server (even though he shouldn't be messing around with the server to begin with).
I have noticed one thing that pops up in the debugging every time-authentication errors. I have made sure to install the Sharp drivers as well, so it is a broken or incompatible PPD file.
So, I tried multiple revisions in the file. Here is the list of changes of each one:
1. No editing.
2. Changing the password line to the admin password.
3. Changing the password line to the user ID number.
4. Adding a username line and making sure the password matched up with the username.
5. Putting the user ID number in the username line I created and making sure the password was correct.
I tried these in over 25 ways-over SAMBA (as the printer is hooked into a Windows machine-I tried it with authentication to the machine and without it), LPD, CUPS web interface Find Printer feature, and I even tried things that I knew were not supported by the printer just to see if it would function properly (IPP, AppSocket).
The reason I am having authentication errors is because the printer requires you to sign in with a username and password before you print, as each user has their own permissions (color/B&W, pages you can print, access to stapler, paper sizes allowed, etc.). I think that the only thing I can do is to somehow delete the entire security system on the printer, but then I would be in hot water with the manager, who would say I am trying to put viruses on the computers, and would subsequently fire me.
Any suggestions as to how I can fix this error? It all starts at the user accounts settings on the printer.

---

