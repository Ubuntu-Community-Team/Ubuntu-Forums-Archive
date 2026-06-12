---
title: "Problem with update manager (?) in 8.04"
date: 2010-12-06
forum: General Help
---

### Post by grey1beard on 2010-12-06
I have 8.04/EMC2 installed in my offline workshop system, and it has not been updated for some months.
(I'm running 8.04 because of latency issues when I tried 10.04/emc, so I'm not upgrading for the moment.)

I brought it into the house to connect to a wired lan to do the update, and while several were fetched and installed, the following window appeared at the end of the procedure.

[B]W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8g-4ubuntu3.10_i386.deb)
  404 Not Found[/B]

I restarted, and tried repeating the update several times, but this always occurs, so the system is now back in the workshop, offline.

Any help/advice would be gratefully received.
John

---

### Post by yetiman64 on 2010-12-06
In Software Sources try changing the server you dowload from. If you currently have it set for your countries location try the main server and vice versa. If neither work try other servers (there should be a button for it to test which will be best for you). Hopefully this will allow you to find a dowload location with that file available. Good luck.

---

### Post by grey1beard on 2010-12-06
> **yetiman64 said:**
> In Software Sources....

Sorry, I may be being very dim, but I don't recognise this location.
Could you expand it a little, and is it only in 8.04 rather than 10.10 which I'm normally online with.
John

---

### Post by yetiman64 on 2010-12-06
On your top panel, System > Administration > Sofware Sources. If my memory of 8.04 serves me correctly it is pretty much the same as in 10.10, though it has been quite a while since I've used Hardy (8.04). 

Sorry for not being more specific, probably had a fit of laziness hit earlier ;).

---

### Post by grey1beard on 2010-12-06
Thanks yetiman.
I've just checked in the workshop, and sure enough it's where you indicate.
Job for tomorrow though.
Many thanks,
John

---

### Post by sikander3786 on 2010-12-06
> **grey1beard said:**
> Thanks yetiman.
I've just checked in the workshop, and sure enough it's where you indicate.
Job for tomorrow though.
Many thanks,
John
If that doesn't help, we'll need to see the entire output of this one from terminal.

```
cat /etc/apt/sources.list
```

Job for tomorrow :P

---

### Post by grey1beard on 2010-12-14
Well, tomorrow finally came, and all proceeded.
Having switched the download to main, all went smoothly.
Many thanks
John

---

