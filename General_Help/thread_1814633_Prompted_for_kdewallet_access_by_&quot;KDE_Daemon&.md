---
title: "Prompted for kdewallet access by &quot;KDE Daemon&quot; on every boot"
date: 2011-07-29
forum: General Help
---

### Post by mfeltman on 2011-07-29
Hi guys.

I've recently returned to [K]ubuntu after a bit of an absence.  I wasn't a fan of Unity and Ubuntu Classic didn't quite do it for me so now I'm a newly minted KDE user.  :)

I'm not sure what I did, but every time I boot up my notebook, once my desktop appears I'm prompted for my password so that KDE Daemon can access my wallet.  There is no checkbox for "Always Allow" or similar, so I keep having to do this.

Any idea what's causing this and how to fix it?  Thanks in advance for any help.

---

### Post by ankspo71 on 2011-07-30
Hi,
This is usually caused by our wireless connections wanting to connect to the internet automatically. There are 3 different things that can be done to avoid being prompted for a password to connect to wireless internet.

1. Disable automatic login for your desktop.
OR
2. Don't use a password for your wallet (leave password blank). 
OR
3. Or go into your network management settings and tell the network manager to store its 'connection secrets' in a non encrypted file. Right click on the network manager icon in your panel by the clock, choose "network management settings", then choose "other", then choose to store the connection secrets "in file (unencrypted)". (these instructions are based on KDE 4.7, but 4.6 should be the same) 

Hope this helps.

---

### Post by mfeltman on 2011-07-30
Thanks, this fixed it!!

---

### Post by Level II on 2011-09-30
I just read the post on how to stop KDE Wallet from driving me nuts - Thanks.  I hope it stays this way.  I got rid of the Keyring thing a while ago, then the Wallet began popping up and won't stop.  I don't need any passwords since I'm the only one who uses the computer and it and several other computers are all in a locked room and I live alone.  Kubuntu is a nice version of Ubuntu - so far.  The Keyring and Wallet almost had me ready to move on to something else.  
Nick  (on Level II)

---

