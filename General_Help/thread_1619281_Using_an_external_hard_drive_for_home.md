---
title: "Using an external hard drive for /home"
date: 2010-11-11
forum: General Help
---

### Post by kh1116 on 2010-11-11
Any opinions on this? I think it would be very convenient for me, but I don't want to cripple the speed of my computer if it is going to slow it down substantially.

---

### Post by kh1116 on 2010-11-14
bump

---

### Post by dcstar on 2010-11-15
> **kh1116 said:**
> Any opinions on this? I think it would be very convenient for me, but I don't want to cripple the speed of my computer if it is going to slow it down substantially.

/home is a system folder that** must** be on a Linux filesystem.

If you put it on a USB connection it will be about 4 times slower than a eSATA connection.

---

### Post by kesman on 2010-11-15
> **dcstar said:**
> /home is a system folder that** must** be on a Linux filesystem.

True, but it can be an external drive, no problem with that. Could even be a remote server on a network and the operating speed would still be tolerable.

For AP: You have to mount the external drive as /home during the installation of Ubuntu. At least that's how I would go about doing it.

---

### Post by kh1116 on 2010-11-15
> **dcstar said:**
> /home is a system folder that** must** be on a Linux filesystem.

If you put it on a USB connection it will be about 4 times slower than a eSATA connection.

That's what I needed to hear, thank you

---

