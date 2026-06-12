---
title: "Samba - Often not detected by hostname, but always by IP."
date: 2010-03-29
forum: General Help
---

### Post by Roasted on 2010-03-29
Just curious, why do I get mixed feedback with connecting to my Ubuntu/Samba file server? If I use the computer name, about 50% of the time it will work when connecting from my Ubuntu laptop. The other 50% I just resort to IP address, which is just as easy anyway.

However, I have 3 Windows boxes on the network, and they all connect each time and every time. What is it about the Windows boxes that allows them to connect via hostname EACH time while my Ubuntu laptop gives me a mixed story?

---

### Post by readycarpenter on 2010-03-29
hmm it should be one way or the other.

did you edit your /etc/hosts file and add

192.168.0.123 servername

and restart to make changes

---

### Post by Roasted on 2010-03-29
No, I did not. Why would I have to do that if my laptop picks it up half of the time? What is it that is even allowing my laptop to pick it up 50% of the time if editing the entry in /etc/hosts is necessary?

---

### Post by Iowan on 2010-03-30
I'm still confused by Windows' "Master Browser" concept. Theoretically, one machine is elected to keep tabs on what machines are available. This only updates periodically - but I'm not sure how often, or exactly how Samba imitates this process...

---

### Post by Roasted on 2010-03-30
Are you suggesting that if my laptop was on my network more often, it would be able to detect (or refresh) my desktop (samba server)'s existence? Therefore making it detect the server via hostname more easily and more frequently?

---

