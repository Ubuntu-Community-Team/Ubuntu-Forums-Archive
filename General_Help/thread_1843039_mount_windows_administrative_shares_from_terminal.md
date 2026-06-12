---
title: "mount windows administrative shares from terminal"
date: 2011-09-12
forum: General Help
---

### Post by Artanis.ro on 2011-09-12
Is it possible to mount a windows administrative share from an ubuntu terminal, without installing additional software like smbmount?

Thank you

---

### Post by haqking on 2011-09-12
> **Artanis.ro said:**
> Is it possible to mount a windows administrative share from an ubuntu terminal, without installing additional software like smbmount?

Thank you


do you not have facility to install additional software ?

also what type of windows shares ? server or desktop.

in certain version of windows it is better to use CIFS than SMBFS

---

### Post by Artanis.ro on 2011-09-12
> **haqking said:**
> do you not have facility to install additional software ?

also what type of windows shares ? server or desktop.

in certain version of windows it is better to use CIFS than SMBFS

I have access to the root user of a server. It is not my server, so I don't want to install aditional software, because I don't want to upset the server admin. Sometimes I need to copy things from the server to a computer that is inside the LAN. He is ok with the copy/paste thing, but like I said I don't want to install extra stuff.

Administrative shares is something like \\computer_ip\c$.

---

### Post by uRock on 2011-09-12
If you do not own, nor administer, the server, then there is nothing we can do to help you gain access to it.

If services are needed in order to properly share the files, then you will need to contact the admin and have him/her install the services.

Thread Closed.

---

