---
title: "Ssh"
date: 2009-08-07
forum: General Help
---

### Post by cromble1 on 2009-08-07
Hi,
 
I'm trying to setup a system where people can connect via ssh but cannot issue any commands. Any command will cause the user to be disconnected...the connection is purely to allow the use of a tunnel. Would anyone have some suggestions please?
 
Thanks.

---

### Post by pmlxuser on 2009-08-07
did you clearly ready and understand what ssh is for?? or you are mistaken, the whole purpose of ssh is to have a secure shell for connecting to a machine. so if no command then why use ssh.

---

### Post by bboston7 on 2009-08-07
If you're looking for a proxy, try squid.  SSH isn't what you're looking for.

---

### Post by slakkie on 2009-08-07
In your authorized_key file put the following:
```

from="ip",command="/home/user/bin/validate-command" ssh-rsa $key

```

then you validate-command scipt contains something like this:

```

#!/bin/sh

#echo $SSH_ORIGINAL_COMMAND > /tmp/sshorig

case "$SSH_ORIGINAL_COMMAND" in
        commands_that_we_can_execute\ *)
                $SSH_ORIGINAL_COMMAND
                ;;
        *)
                echo "Command rejected $SSH_ORIGINAL_COMMAND"
                logout
                ;;
esac

```

Tweak it were needed.

---

### Post by cromble1 on 2009-08-07
Thanks slakkie.  Pmlxuser,  ssh tunnel is an easy way to proxy and disable nagles at the same time.

---

