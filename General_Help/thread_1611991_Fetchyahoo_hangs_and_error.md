---
title: "Fetchyahoo hangs and error"
date: 2010-11-02
forum: General Help
---

### Post by NikitaUtiu on 2010-11-02
When I run fetchyahoo 2.13.9 it hangs at 'Fetching mail from folder: Inbox' for a good couple of minutes then I get an error saying something about multi-hop cycle.
This is my configure file:
```
###### SHOULD configure these  ######
username = n.utiu@yahoo.com
# this can be a password or an md5_hex hashed password
password = ######## no password for you

# set this to 0 to turn off HTTPS and login insecurely via plaintext instead
use-https = 1

use-forward = 1
mail-host = smtp.gmail.com
smtp-username = nikita.utiu
smtp-password = ########
send-to = nikita.utiu@gmail.com
folders = Inbox , Spam
no-download = 1

```
Any idea ?:confused:

Thanks, NikitaUtiu.

---

