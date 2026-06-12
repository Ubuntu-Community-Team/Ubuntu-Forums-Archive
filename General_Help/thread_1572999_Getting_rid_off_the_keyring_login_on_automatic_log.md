---
title: "Getting rid off the keyring login on automatic login..."
date: 2010-09-12
forum: General Help
---

### Post by gwu777 on 2010-09-12
Hi there,

I have setup ubuntu to log me in automatically, unfortunatly since, I have to login into the keyring. I am not sure why, as no program running seems to need it anyway...

I really would like to get rid off it, however, I would like to keep a password on the keyring.

P.S. When I use normal login with password, I don't need to login into the keyring...

Any ideas?

---

### Post by mikewhatever on 2010-09-12
The way to get rid of the keyring login prompt is to set its password to nothing. As for the programs that access keyring, the Network Manager is probably the most common one.

---

### Post by gwu777 on 2010-09-16
> **mikewhatever said:**
> The way to get rid of the keyring login prompt is to set its password to nothing. As for the programs that access keyring, the Network Manager is probably the most common one.

It is not the network manager, I have already checked... Anyway, I have now re-enabled login. Thank you very much for your help.

---

### Post by stinkeye on 2010-09-16
Go to network manager applet ,edit your connection and tick the box **make avaiable to all users**.

---

### Post by gwu777 on 2010-09-16
> **stinkeye said:**
> Go to network manager applet ,edit your connection and tick the box **make avaiable to all users**.

Thank you for the above, but as I said it is NOT the network manager as I have already done what you mention a while back, and the wireless connect fine to my wpa network before I enter the password. Not to worry though as I have re-enabled the login for various reason...

---

