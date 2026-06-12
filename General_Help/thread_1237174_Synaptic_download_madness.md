---
title: "Synaptic download madness"
date: 2009-08-11
forum: General Help
---

### Post by Ekeluo on 2009-08-11
My ISP have been quite gracious recently and power a bit stable, so I afforded my self the pleasure of downloading nexuiz to play. I managed to get the outdated one in the repos (when will it be updated?). A massive 400mb+ download considering I had to sit in front of the pc for the whole download to finish at ~20kbps. OK. Significant part of my life gone, can't get it back, but I do have nexiuz installed. But then... I got new repos for the updated version (at playdeb.net) and managed to sit for four hours while the download progressed to 34 percent. Then something happened to the connection temporarily (Was using firefox to surf so I knew it was down) and when it returned [SIZE="4"]SYNAPTIC RESTARTED THE DOWNLOAD!!!!!!!![/SIZE] Without any reason, info or warning? why? What have I sat here for 4 hrs for? Huh?

This is really not good at all for people like me with 20 kbps internet connections.

---

### Post by zkriesse on 2009-08-11
Usually in the Synaptic Manage when a download is interrupted it will automatically restart if there has been a connection error. Most likely that's what happened to you.

---

### Post by Ekeluo on 2009-08-23
After the error in the following info box it says the reason why the download was cancelled - Connection error. I don't see why it has to restart. [Sigh].

P.S. I use a sort of hotspot-like ISP where your connect, dhcp address, the login page for the ISP where you have to sign in. You will be redirected to this page upon logout or requesting for login. Such that if I get logged out mid download, the file gets corrupted (in kget, at least). Anybody know any 'intelligent dl managers that suspend the download when the file size changes?

---

### Post by SuperSonic4 on 2009-08-23
wget should work, especially if pass the -c flag (-c = continue)

---

### Post by MelDJ on 2009-08-23
or aria eventhough it looks old:P

---

