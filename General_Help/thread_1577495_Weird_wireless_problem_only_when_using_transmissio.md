---
title: "Weird wireless problem only when using transmission."
date: 2010-09-18
forum: General Help
---

### Post by aklo on 2010-09-18
I am using ubuntu netbook edition 10.04 on acer aspire one.

My wireless is working perfectly when I am surfing the net or downloading youtube videos however when I use transmission (bit torrent) it will download for awhile then my wireless will not work and yet it shows that it is connected...then I have to reconnect again then the torrent starts downloading for awhile usually 1-2 mins then the wireless will fail again.

An interesting point to note: When I connect the ethernet cable to my netbook, bit torrent download perfectly it only happens when i'm using wireless.

It is annoying how I have to physically connect my netbook to the modem to download bit torrent files.

---

### Post by 3dgard on 2010-09-19
Try using Deluge instead of transmission to download torrents... if it behaves the same, then its a problem with your wireless card driver -> which means I can't help you :(

---

### Post by kerry_s on 2010-09-19
sounds like your overloading your router wifi, try throttling transmission.

for example: mine
i got 3mb dsl

if i use unlimited down & 50 up for 1 torrent it's fine
but if i add more than 1 torrent, it will crash the router/wifi & i have to wait a minute for it to come back up so i connect again.
if i use 150 down & 50 up, i can down load as many torrents as i want, no problem wifi never drops out

i also have no problems with a hard connection, the network doesn't drop when using the wire.

---

### Post by aklo on 2010-09-19
Thank you i will try the solution of downloading 1 file at a time and setting the limit.

It used to work fine in 9.10 though.

---

### Post by rlklee on 2011-06-06
Bump on this problem. Same elsewhere as in Transmission. Scaling back the number of connections doesn't seem to matter one bit. 

I get no bad behavior in Win 7 and I, like above poster, didn't used to have this problem in previous versions of Ubuntu. 

I get the same problem in latest versions of Debian and Fedora as well.

Very frustrating and confusing, considering how broad the problem seems to  be.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **rlklee said:**
> Bump on this problem. Same elsewhere as in Transmission. Scaling back the number of connections doesn't seem to matter one bit. 

I get no bad behavior in Win 7 and I, like above poster, didn't used to have this problem in previous versions of Ubuntu. 

I get the same problem in latest versions of Debian and Fedora as well.

Very frustrating and confusing, considering how broad the problem seems to  be.

Do you have port forwarding configured on your router?

---

### Post by rlklee on 2011-06-06
> **linuxinstalledfromhdd said:**
> Do you have port forwarding configured on your router?

Yes.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **rlklee said:**
> Yes.

Did you test to see if this happening in 10.10 live bootable USB flash drive of Ubuntu?  Is this something that is solely related to 11.04 testing?

---

### Post by rlklee on 2011-06-07
> **linuxinstalledfromhdd said:**
> Did you test to see if this happening in 10.10 live bootable USB flash drive of Ubuntu?  Is this something that is solely related to 11.04 testing?

See my above post.

---

### Post by rlklee on 2011-06-07
Solution here worked for me [http://ubuntuforums.org/showthread.php?t=1775726]("http://ubuntuforums.org/showthread.php?t=1775726").

Phew!

Edit: Never mind, I spoke to soon, too optimistic. Problem persists.

---

