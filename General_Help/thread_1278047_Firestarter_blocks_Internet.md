---
title: "Firestarter blocks Internet"
date: 2009-09-29
forum: General Help
---

### Post by satish_j on 2009-09-29
Need help with configuring Firestarter as the default settings blocks the Internet connection.If i stop the firestarter,internet strats working again.
Iam using DSL modem for connecting to Internet.I think there must be some exception that needs to be put for Internet in firestarter.
Pls help...

---

### Post by lisati on 2009-09-29
Suggestion: use (g)ufw instead of firestarter.

---

### Post by satish_j on 2009-09-29
> **lisati said:**
> Suggestion: use (g)ufw instead of firestarter.

Can you tell me how to install and configure the same???

---

### Post by credobyte on 2009-09-29
> **satish_j said:**
> Can you tell me how to install and configure the same???

It's have been already explained ( tutorial ): [http://ubuntuforums.org/showthread.php?t=823741](http://ubuntuforums.org/showthread.php?t=823741)

---

### Post by XCan on 2009-09-29
> **satish_j said:**
> Need help with configuring Firestarter as the default settings blocks the Internet connection.If i stop the firestarter,internet strats working again.
Iam using DSL modem for connecting to Internet.I think there must be some exception that needs to be put for Internet in firestarter.
Pls help...

If you go to the firestarter screen and click on the Policy tab, what does the "Inbound/Outbound traffic policy" say? My guess that your outbound policy is set to "Restrictive by default, whitelist traffic", effectively blocking your comp from reaching outwards.

---

