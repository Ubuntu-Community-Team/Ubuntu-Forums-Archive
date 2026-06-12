---
title: "&quot;Network Connections&quot; disappeared"
date: 2011-05-11
forum: General Help
---

### Post by CTBuckweed on 2011-05-11
I am running "Lucid Lynx" (10.04) 64 bit. My "Network Connections" has disappeared from the 'System -> Preferences' menu. I also had a network connections status/configure thing on the panel. With it, I could disable/enable and configure my network connections. It appears on a fresh install of 10.04, but it is no longer available. I've been running 10.04 for a number of months but it recently has disappeared.

Help me... What happened?

---

### Post by CTBuckweed on 2011-05-16
Well, I fixed it myself... I did a full restore of an earlier backup of my root partition (I keep /home on a different partition).

That did the trick. Then I once again applied all the ubuntu patches and re-applied my new VirtualBox version.

Now, I am up and running with the 'network connections' available again...

Good backups saved the day.

Thanks for all your help (he says facetiously).

---

### Post by jim_deadlock on 2011-05-16
If it happens again just add nm-connection-editor to your panel (install it if necessary).

---

### Post by CTBuckweed on 2011-05-20
> **jim_deadlock said:**
> If it happens again just add nm-connection-editor to your panel (install it if necessary).

Thanks for the tip. I'll try this if it ever happens again.

---

