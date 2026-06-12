---
title: "Access to windows shares suddenly stoped working"
date: 2011-05-16
forum: General Help
---

### Post by MockY on 2011-05-16
My XBMC box has been working just fine for a few months. I could easily browse to the Windows shares located on a machine running Windows 7 both within XBMC and Nautilus. However, now I can't browse to the shares using either XBMC or Nautilus (via Places - Network). Furthermore, when using smbclient in terminal I get the following error:
```
smbclient -L fileserver
protocol negotiation failed: ERRnomem

```
I have tried using the IP number as well (the host is entered in the hosts file.
I can ping the machine just fine, using either the IP number or the host name, but the ability to browse its shares is impossible. I can access the shares using another Windows 7 machine, so the shares are there.

What could have happened? And what should I try next?

---

### Post by garvinrick4 on 2011-05-16
I could not access Windows shares in 7 with samba in a Windows Workgroup as long as Windows live essentials is installed in 7. Not Windows live but windows live essentials. It would ask for password and not accept until I removed. Lots of other users had same issues. Something to investigate but works for me.

---

### Post by MockY on 2011-05-17
I will look in to that once I am near the machines in questions. However, nothing has changed from yesterday to today, and it worked then. If what you say is correct, then it shouldn't have worked at all. Either way, I will look into your suggestion.

---

### Post by buutteef on 2012-06-09
If you look windows logs, you can see error about lanman etc. shadow memory something.. Reboot your windows and then you can use windows shares again.

---

