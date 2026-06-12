---
title: "SSH query"
date: 2012-08-11
forum: General Help
---

### Post by ryanyeah on 2012-08-11
In theory what would happen if you disabled password authentication to a server, put my SSH key in, and then my computer died and I had to generate another SSH key? 

Although I guess that would only lock me out of SSH though? And with VNC access to the server, it still may be possible to log in with an account password and reconfigure the SSH?

---

### Post by Habitual on 2012-08-11
You should NOT have to (re)generate anything if the server crashed.
The server admin would need to restore from backup /root/.ssh/authorized_keys*, or *the contents of your_key.pub* would need to be restored to /root/.ssh/authorized_keys* on the server.

When you connect to the "new" server using an old identity/fingerprint/*, you would get a warning on/from the client-side saying "fingerprint has changed" or similar, but if the change IS expected it is safe to delete that same host entry in your ~/.ssh/known_hosts and re-connect and accept the new key-host identity.

Hope that helps.

Edit: Sorry, if "my computer" ... you would restore your keys from backup to their original location.
If that is an issue, then you would have to regenerate another key and insert the contents of that key.pub into /root/.ssh/authorized_keys* on the server.

---

