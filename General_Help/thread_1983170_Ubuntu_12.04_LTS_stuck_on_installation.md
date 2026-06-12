---
title: "Ubuntu 12.04 LTS stuck on installation"
date: 2012-05-19
forum: General Help
---

### Post by DaveDeviant on 2012-05-19
Everything is working fine till the end on installation where Ubuntu stuck on ```
ubuntu ubiquity: Processing triggers for update-notifier-common
```

Waited for more than 10 minutes and nothing, stucked there.

---

### Post by mc4man on 2012-05-19
If you were connected to the Internet for the install then you may be showing issues due to current bad state of some Canonical servers

If it doesn't finish after a while longer then I'd do the install over & make sure your machine has No Internet connection during the install
If wired then disconnect the cable, if wireless then don't enable before/during the install.

Otherwise this should clear up in a day or so

---

### Post by DaveDeviant on 2012-05-19
> **mc4man said:**
> If you were connected to the Internet for the install then you may be showing issues due to current bad state of some Canonical servers

If it doesn't finish after a while longer then I'd do the install over & make sure your machine has No Internet connection during the install
If wired then disconnect the cable, if wireless then don't enable before/during the install.

Otherwise this should clear up in a day or so

Yes, this is what I've done after tried that installation with updates and got stucked. I disconnected my wifi and run the installation without updates. I think is something related to flash because when I try to install ubuntu restricted extras the installation in terminal stuck there on wget flash plugin. If I click on the link there is no problem in downloading but on terminal it's not working. Y'day I had the same problem on installation but with "retrieving files". As you said, may be something related to canonical servers.

Thanks for reply,
Dave

---

### Post by mc4man on 2012-05-19
> **DaveDeviant said:**
> Yes, this is what I've done after tried that installation with updates and got stucked. I disconnected my wifi and run the installation without updates. I think is something related to flash because when I try to install ubuntu restricted extras the installation in terminal stuck there on wget flash plugin. If I click on the link there is no problem in downloading but on terminal it's not working. Y'day I had the same problem on installation but with "retrieving files". As you said, may be something related to canonical servers.

Thanks for reply,
Dave

It's definitely some of their servers (Main & US for packages)
I've switched to the one shown in screen for the moment but the flash installer comes from Main not matter what mirror you're using, I had this install get hung up on that update (didn't notice it was included until too late

So even if switching servers I'd be careful what you're installing/updating till this is fixed

---

### Post by DaveDeviant on 2012-05-19
Indeed. As you said, we just need to have some patience and let them fix those issues. I just hope they fix it in a day or two maximum.

Regards,
Dave

---

