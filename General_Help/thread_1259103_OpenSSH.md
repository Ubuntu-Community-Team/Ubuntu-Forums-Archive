---
title: "OpenSSH"
date: 2009-09-05
forum: General Help
---

### Post by Cardale on 2009-09-05
I have been trying to get OpenSSH working and everything is fine, but I wanted to use keys to increase security one problem is when I follow most tutorials I find that there is no .ssh/authorize_keys file or folder for that matter.  If there isn't one do I just create it or what?  Using Ubuntu server to connect to an Ubuntu desktop

---

### Post by fluffman86 on 2009-09-05
yeah, just open gedit, paste in the key you want to authorize on your desktop, and save it as ~/.ssh/authorized_keys

---

### Post by Cardale on 2009-09-05
ok it seemed to work fine if I use ssh -i but it still asks me for the passphrase and the user account password.  Whats wrong here?

---

### Post by falconindy on 2009-09-05
It's my understanding that just because you're allowing that particular key, it doesn't let you bypass authentication. You're merely adding a second layer of protection, preventing other people without your key from connecting.

In case I'm mistaken about the above, have you restarted the openSSH server? Should be something along the lines of: `sudo /etc/init.d/sshd restart`

---

### Post by Cardale on 2009-09-06
Thanks for posting.  I believe your incorrect.  I believe you have the option either way.  You can have both or one or the other.  Many tutorials mention this that users would setup a key just so they wouldn't have to enter a password and also not even use a pass phrase which is insecure.  Unless something has changed from when these tutorials were written? [http://www.ibm.com/developerworks/library/l-keyc.html](http://www.ibm.com/developerworks/library/l-keyc.html)

I did a restart of the individual ssh client and the server.  I'll keep trying hopefully I can figure out the problem.

---

### Post by Cardale on 2009-09-06
Alright I got it working! Woohoo!  Anyway.  I guess I was reading a old article.  I create a authorized_keys2 file instead of a authorized_keys file and it work.

Thanks fluff and falcon.

---

