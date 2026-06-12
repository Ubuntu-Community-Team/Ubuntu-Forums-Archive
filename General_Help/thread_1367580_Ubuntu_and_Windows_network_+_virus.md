---
title: "Ubuntu and Windows network + virus"
date: 2009-12-29
forum: General Help
---

### Post by Coder68 on 2009-12-29
At a wifi hotspot I was redirected to a page that gave me a scareware pop up and then showed me a "Windows xp my computer" page and said I had over 100 trojans. Obviously fake and unable to hurt Linux...

My question is this:  Could something from this site have gotten on my Ubuntu laptop and then when I hook up to my home network, be transfered over to my Windows boxes? I can't see how, but someone told me that it could.  I would think it would have to infect Ubuntu for it to be able to make Ubuntu send over a file via the network.        I did not click on anything other then to close the Firefox tab, and I got no prompt for my password to allow anything to install. 

I say I am correct and this other guy is wrong.  What do you say?

Coder68

---

### Post by HPD2 on 2009-12-29
I think that is a bit of a loaded question because it has to answers the simple one, no, and the complex, yes. Some one correct me if I'm wrong.

It is technically possible, but using Linux the likely hood of some thing like that, drive by malware infection, is slim at best, and then for it to transmit its self to a new platform, ex. Windows, is highly unlikely.

---

### Post by adam814 on 2009-12-29
Sounds very unlikely indeed.  It might be theoretically possible if you're running Wine and/or a samba server on your ubuntu machine, but I highly doubt it.  If you have more than one Windows machine on the network I'd be more worried they'd spread the malware amongst themselves than Windows to Ubuntu or vice versa.

---

### Post by Coder68 on 2009-12-30
For that to happen, wouldn't there have been a prompt for me so malware could install or execute?

C68

---

### Post by pfranks on 2009-12-30
OK, *if* there's a true self-installing malware (not scareware or trojan which would need human help) it would have to be a Linux executable (not Windows) AND it would have to wrap a Windows exe which is to be distributed into your network, AND it would have to be executable (flag) under Linux so it can run. So, unless you granted exe rights to a mystery file, it ain't going to happen even if all the other highly improbables come together at the same time.

---

