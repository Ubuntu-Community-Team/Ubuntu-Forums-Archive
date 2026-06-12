---
title: "What exactly is SSH Agent?"
date: 2010-10-19
forum: General Help
---

### Post by gabriella on 2010-10-19
Could someone kindly tell me what exactly is SSH Agent as listed in Startup Applications? And can I safely disable it? I've read around a bit and get the impression is has to do with others connecting to my machine/network which is not an issue for me as I'm the only user, but I'm not clear.

Thanks

Gabbi

---

### Post by gabriella on 2010-10-19
Anyone????

---

### Post by marshmallow1304 on 2010-10-19
[QUOTE="man ssh-agent"]ssh-agent is a program to hold private keys used for public key authentication (RSA, DSA).  The idea is that ssh-agent is started in the beginning of an X-session or a login session, and all other windows or programs are started as clients to the ssh-agent program.  Through use of environment variables the agent can be located and automatically used for authentication when logging in to other machines using ssh(1).[/QUOTE]

You probably don't want to disable it as I think it handles passwords stored via the password manager for things like encrypted WiFi and Evolution mail accounts.

---

### Post by efflandt on 2010-10-19
See **man ssh-agent**.  In the old days I had to run **ssh-agent**, then run **startx** from the console (I think I created an alias for startx that would do that automatically).  But gnome runs ssh-agent automatically.

ssh-agent makes it easier to reconnect ssh client or use scp, etc. because once you run ssh client and enter your password or passphrase for your key, it remembers that until you log out.  So if you disconnect the ssh session or want to use scp to copy files, you do not have to re-enter your password or passphrase.  Once you shut down your computer or log out of your local PC, ssh-agent forgets everything.

If you want to ssh to a different computer and then ssh to a 3rd computer or scp something back to your computer you can put **ForwardAgent yes** in your ~/.ssh/config and you ssh-agent will not require you to re-enter credentials in your remote ssh session.  However, from **man ssh_config**:

> ForwardAgent
             Specifies whether the connection to the authentication agent (if any) will be forwarded to the remote machine.  The argument must be “yes” or “no”.  The default is “no”.

             Agent forwarding should be enabled with caution.  Users with the ability to bypass file permissions on the remote host (for the agent's Unix-domain socket) can access the local agent through the forwarded connection.  An attacker cannot obtain key material from the agent, however they can perform operations on the keys that enable them to authenticate using the identities loaded into the agent.

---

### Post by gabriella on 2010-10-20
> **efflandt said:**
> See **man ssh-agent**.  In the old days I had to run **ssh-agent**, then run **startx** from the console (I think I created an alias for startx that would do that automatically).  But gnome runs ssh-agent automatically.

ssh-agent makes it easier to reconnect ssh client or use scp, etc. because once you run ssh client and enter your password or passphrase for your key, it remembers that until you log out.  So if you disconnect the ssh session or want to use scp to copy files, you do not have to re-enter your password or passphrase.  Once you shut down your computer or log out of your local PC, ssh-agent forgets everything.

If you want to ssh to a different computer and then ssh to a 3rd computer or scp something back to your computer you can put **ForwardAgent yes** in your ~/.ssh/config and you ssh-agent will not require you to re-enter credentials in your remote ssh session.  However, from **man ssh_config**:

OK thanks guys! I guess I'll leave it on then. I was just disabling unwanted start-up applications.

---

