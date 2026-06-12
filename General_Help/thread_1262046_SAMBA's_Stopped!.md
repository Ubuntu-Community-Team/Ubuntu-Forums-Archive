---
title: "SAMBA's Stopped!"
date: 2009-09-09
forum: General Help
---

### Post by LeeS_AIA on 2009-09-09
Last Friday I did an update. Later I discovered that SAMBA stopped working. I thought it would be a simple restart issue.....NOT!

I have a ubuntu desktop setup Jaunty 9.04. We are using it as a file server. (3 PC's and a MacBookPro) Previously (before the update) everything was very stable for a few months since setting it up. I am an architect, not a techy (I know enough to get myself in trouble). We have a small office, so I wear many hats, including IT Manager. 

I've used the SWAT (Samba Web Admin Tool) in the past to get SAMBA started. In the status page it offers a selection to start or restart SAMBA. This did not work. I tried /etc/init.d/samba that also did not work.

I tried removing SAMBA and reloading it. get-apt samba. No results though the response appears that it was successful. 

I've looked for the daemon smbd and I don't believe it is there. I used the find command and the search for files under places in the desktop menu. 

using dpkg -L lists samba, samba-common, samba-doc, smbclient, smbfs....

So, I'm at a standstill. I don't know what to do. I need to get back to real work. PLEASE HELP!!

Thank you!!

---

