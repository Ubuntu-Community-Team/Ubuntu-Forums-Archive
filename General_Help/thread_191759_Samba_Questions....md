---
title: "Samba Questions..."
date: 2006-06-07
forum: General Help
---

### Post by podollb on 2006-06-07
Hi,

I use Ubuntu as a server running Samba. It seems to work great other than a few things that are minor bug very annoying...

1. The Windows machines will be prompted to login to their respective home directory, but if one user logs in as another, Windows doesn't ever forget the username/password. So the real user has full rights to the guy who just logged in before him (assuming they are using the same Windows account). Is there a way to have Samba close a connection or make the session go away when the window that connected to the share dies? Or is deadtime my only option which will disconnect the user after a specific amount of time...

2. The refresh problem is horrible. If I go into one of the Samba share and create a file or delete a file, my changes do not show up unless I hit F5 to refresh the screen. There HAS GOT TO BE A WAY for Samba to send refreshes or something to avoid this problem -- doesn't there?

Thanks!

---

