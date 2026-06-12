---
title: "Extremely awkward situation"
date: 2009-10-12
forum: General Help
---

### Post by noxary on 2009-10-12
Sorry I can't explain it in the title any better, but at work, we have a firewall blocking almost every port imaginable except for port 80 obviously so we can search through the web, the problem is that I have my own webserver that I usually SSH to. But, when I tried it here, it blocked me. So, I though I'd just work at the site locally and upload via FTP, but FTP can't connect either. I went home and thought I could set up a Remote Desktop, and I did set it up and was able to access my desktop from everywhere except from work. It turns out they blocked that port as well. So, can anyone here help me?

I'm not trying to set up a Remote Connection on port 80, but Ubuntu doesn't give me that option. I actually don't even have advanced settings on Ubuntu. I'm running the latest beta of Karmic by the way. Can anyone help me slack off at work and help me access my computer or web server?

---

### Post by khelben1979 on 2009-10-12
Talk to the boss? Or.. go for a stable release of Ubuntu?

---

### Post by pilorama on 2009-10-12
_...deleted..._[COLOR=#ffffff][[COLOR=#ffffff].[/COLOR]]("http://doctorluiza.wordpress.com/")[/COLOR]

---

### Post by Giblet5 on 2009-10-12
> **khelben1979 said:**
> Talk to the boss? Or.. go for a stable release of Ubuntu?

Why would a stable version of Ubuntu open ports in the corporate firewall?  ;)

---

### Post by Giblet5 on 2009-10-12
Noxary, it sounds like you're working inside a digital dead zone.

Talk to your boss or IT people.

You may need to use "socksified" clients to get through your firewall (google is your friend), but check with IT to see if they'll even permit that.

---

### Post by khelben1979 on 2009-10-12
> **Giblet5 said:**
> Why would a stable version of Ubuntu open ports in the corporate firewall?  ;)

Good question. :) I just thought that the problem could be bug related.

---

### Post by DeMus on 2009-10-12
> **noxary said:**
> Sorry I can't explain it in the title any better, but at work, we have a firewall blocking almost every port imaginable except for port 80 obviously so we can search through the web, the problem is that I have my own webserver that I usually SSH to. But, when I tried it here, it blocked me. So, I though I'd just work at the site locally and upload via FTP, but FTP can't connect either. I went home and thought I could set up a Remote Desktop, and I did set it up and was able to access my desktop from everywhere except from work. It turns out they blocked that port as well. So, can anyone here help me?

I'm not trying to set up a Remote Connection on port 80, but Ubuntu doesn't give me that option. I actually don't even have advanced settings on Ubuntu. I'm running the latest beta of Karmic by the way. Can anyone help me slack off at work and help me access my computer or web server?

I don't know where you work but I can imagine many companies do this to keep there own network safe. I once worked at a company where we didn't even have internet at our own computers. Here and there were what they call greennet computers with which you could surf. These computers were not connected to the normal network.
Another question is: why do you want/need to contact your own webserver during office hours? Do you get paid to do that?

---

### Post by P4man on 2009-10-12
> **noxary said:**
> Sorry I can't explain it in the title any better, but at work, we have a firewall blocking almost every port imaginable except for port 80 obviously so we can search through the web, the problem is that I have my own webserver that I usually SSH to. But, when I tried it here, it blocked me. So, I though I'd just work at the site locally and upload via FTP, but FTP can't connect either. I went home and thought I could set up a Remote Desktop, and I did set it up and was able to access my desktop from everywhere except from work. It turns out they blocked that port as well. So, can anyone here help me?

I'm not trying to set up a Remote Connection on port 80, but Ubuntu doesn't give me that option. I actually don't even have advanced settings on Ubuntu. I'm running the latest beta of Karmic by the way. Can anyone help me slack off at work and help me access my computer or web server?

You can change the port for remote desktop using gconf-editor (browse to /desktop/gnome/remote_access. Set alternate port, and enable use_alternate_port).

 You should try a port over 1024 (but below 16000). Firewalls often keep those high ports open as they are used to establish sessions. Anything over 1024 is not supposed to be a server. If your company has a stateful inspection firewall, a high port won't help (it inspects and identifies the TCP packages, and sees what sort of traffic it is, and who is server and who is client, and can therefore block protocols, not just ports). Most companies dont do stateful inspection though, so its worth a shot.

---

### Post by blueridgedog on 2009-10-12
Putting the technical issues aside, you should advise your team leader or supervisor as well as the IT staff where you work of your plans and needs.  The limits they have in place are either designed to help keep you working on their tasks or for their security.  If your remote work is legitimate, then the IT staff at your company may even assist you in making a connection.  If they aren't and you press on with alternate ports, the traffic will be found eventually.

---

### Post by P4man on 2009-10-12
> **blueridgedog said:**
> Putting the technical issues aside, you should advise your team leader or supervisor as well as the IT staff where you work of your plans and needs.  The limits they have in place are either designed to help keep you working on their tasks or for their security.  If your remote work is legitimate, then the IT staff at your company may even assist you in making a connection.  If they aren't and you press on with alternate ports, the traffic will be found eventually.

If its for his work, then yes, I obviously agree. 

If its for private, non work related stuff, assuming his contract allows him to do that, there is no point in talking to IT, they are not gonna open a firewall for you. 

FWIW, I used to do the exact same thing (remote desktop over ssh on  high port) to surf at work but from my computer at home - allowing me to visit job sites looking for another job. My contract didn't forbid private internet use (within reasonable bounds), but I obviously didn't want my employer to see I was surfing to monster.com :) Using remote desktop (over encrypted ssh to a dynamic IP at my home), all they can see is... traffic ;)

---

### Post by Johnny B on 2009-10-12
your ssh server at home can listen on multiple Ports if you want it to. why can't you have sshd listen on port 80 or 443 (https)?


i'm not going to ask why you want to do this, or If your remote work is legitimate, its none of my buisness or anyone else's. I'm here to help.

---

