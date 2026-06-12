---
title: "Keyring issue - no option to automatically log in default keyring"
date: 2011-05-02
forum: General Help
---

### Post by mjpatey on 2011-05-02
Hi, all-

I searched for an answer to this here, but so far have found nothing.  Did a fresh install of 64-bit Natty on day 1, and have an irksome issue when logging in.  Once I'm logged in, Keyring prompts me to type the default keyring password.  This happens every time I log in.

The problem is, the option to unlock the keyring automatically at login is dimmed, and only the other 3 options are selectable.

I opened the "Passwords and Encryption Keys" applet and saw 2 entries under "passwords", both named "Network secret for Auto [my network name]/802-11-wireless-security/psk".  I see no option here to allow either of these to automatically unlock at login.

Any idea how I can get Ubuntu to log into my wireless network automatically instead of asking for the default keyring password each time after log in?  Thanks in advance for any light you can shed!

---

### Post by gandaran on 2011-05-02
> Any idea how I can get Ubuntu to log into my wireless network automatically instead of asking for the default keyring password each time after log in? Thanks in advance for any light you can shed!
from the user administrator account set the wireless connection in network manager for all users, this way it wont ask for the keyring password anymore.
another way is to remove every existing keyring in Passwords and Encryption Keys, (remove/clear up everything there including the default keyring) then next time you login enter the wireless password but for setting the keyring use a blank password instead, just click the ok button.

---

### Post by mjpatey on 2011-05-02
Beautiful!  Thanks, that did it.  :-)

---

