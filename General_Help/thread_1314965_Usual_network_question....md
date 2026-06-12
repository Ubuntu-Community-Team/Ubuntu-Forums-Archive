---
title: "Usual network question..."
date: 2009-11-04
forum: General Help
---

### Post by Himself2007 on 2009-11-04
Hello again

Everything is fine up to now.
But I have a little problem...not dramatic.
But a bit annoying.
About my network.
Samba has been installed and running well.
I remember this morning my network was going fine.
From Ubuntu I could go in share folders on a Windows machine.
And same thing from Windows. Perfectly bi-directional.
But now none of them can communicate.
As an example, if I open my Network file browser and click on "Windows Network" I have this message:
"Unable to mount location...Failed to retrieve share list from server".
OK I know this means that Samba is "out to lunch"...I guess.
But how can I repair this situation.
You know? I like when my network is working.
If I remember well, I installed and uninstalled two different FireWalls.
Gufw and Firestarter. 
Could be the reason...but they are uninstalled!
I will confirm that Windows can access other Windows computers on the network.
The problem is in the Ubuntu computer.
[SIZE="4"]**[COLOR="DarkRed"]Mystery![/COLOR]**[/SIZE][-o<

Luc

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Good luck, my network was finally dialed in before Karmic, now it's off somewhere munching eucalyptus I suppose.

---

### Post by kixome on 2009-11-05
look for an iptables reset script, also check 
sudo ufw status, if on then, sudo ufw disable
i think iptables needs to be reset to accept all connections

---

### Post by ST3ALTHPSYCH0 on 2009-11-05
Installing Samba 4 has allowed my windows 7 full access to my Ubuntu shares, but Ubuntu can't see either the Vista or the Win7 machine on my network.

---

