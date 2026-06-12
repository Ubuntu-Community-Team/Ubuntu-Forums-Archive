---
title: "rdesktop response issues"
date: 2010-01-07
forum: General Help
---

### Post by troodz on 2010-01-07
Hi,

I am experiencing some rdesktop lag time/response issues that I am looking for insight on... perhaps it is a common issue that someone has dealt with before?

I have several servers that serve virtual machines via RDP sessions. They all work fine from a Windows client using RDP. Rdesktop sessions to virtual machines on two of the servers also work absolutely fine. However, rdesktop sessions to virtual machines located on server 3 have huge response time issues... the experience is worse than a slow VNC session, and is not a sufficient solution for me. I have updated NIC drivers on server 3, and can't think of anything obviously different (aside from the different hardware, etc).

Has anyone seen poor response times via rdesktop before, when Windows RDP works fine? Could it be some sort of incompatibility with the server NIC? I have tried several Linux flavors, all with the same results... rdesktop work fine to other RDP sessions on my network, but not to ones on this particular server, even though Windows RDP sessions to that server pose no problems.

Thanks for the help.

Tony

---

