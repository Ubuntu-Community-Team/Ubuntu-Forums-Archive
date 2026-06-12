---
title: "host refusing vnc over ssh"
date: 2010-08-25
forum: General Help
---

### Post by Mia_tech on 2010-08-25
I have a host (ubuntu) that accepts vnc over ssh connections, as long as they are originated from the same network, but when I do this as vpn (from outside) the ssh works, but not the vnc part.... I'm using putty, and dynamic port forwarding

thanks

---

### Post by CharlesA on 2010-08-25
You would need to use local port forwarding. Forward 5900 to 127.0.0.1:5900.

See if that works. :)

---

### Post by Mia_tech on 2010-08-25
> **CharlesA said:**
> You would need to use local port forwarding. Forward 5900 to 127.0.0.1:5900.

See if that works. :)

no, the problem was I was using the external ip/hostname to forward the dynamic port.... dahh

---

