---
title: "nm-applet missing after users table modification"
date: 2010-06-11
forum: General Help
---

### Post by manco1911 on 2010-06-11
I just installed Ubuntu 10.04 on a Dell Notebook.. actually a Dell Inspiron e1405.

So, after installing some usual stuff, i headed to the users configuration. Since this is a laptop that will be used by different people.. i just created some users with limited priviledges.

Before giving back this box, i'm told that they only need 1 "master user". So I erased all users exept for the original one.. the Administrator. But just in case i modified the root user pwd for an incident recovery.. sort of.. 

The thing is that after the final reboot, i encounter that the nm-applet --sm-disable is missing from the main panel. Thow it is "running" on the background.. for some reason its not showing.

After several google searches, and some command lines.. still nothing.

So i login on to root account, in wich i realize the network applet its showing as it should on the main panel. Looking around i found out that for some reason, after playing with the users table, in the Administrator User account, the option to conect to Eth and Wifi networks was not ticked. :confused:

I just enabled that option, login as Administrator and there it was.. 

Anyone know why this could happen ?

---

