---
title: "Not password problem-Locked out of 9.04!"
date: 2010-04-15
forum: General Help
---

### Post by Cookie-Tux on 2010-04-15
Ok, I'm a n00b.

Problem: When I login my password is correct. It doesn't say "Authentification Failure",
It goes on showing the "ubuntu" loading screen and then, It flickers. Real bad.Then the loading screen comes back and then...The loading screen comes back.I've tried wrong passwords,But they just go "Authentification Failure" as they normally do. Its only when I actually login.
Circumstances: Yesterday I changed screen resolution, Did some EMCA programming, Went on on the internet, used gimp, closed internet, Finished and closed programming then I shutdown, NOT CLOSING GIMP.I am currently on another account so Only my account is locked. Its really annoying, Please help!

-OMnOmNOmNoM

---

### Post by aysiu on 2010-04-15
Just to clarify, when you log in, there is no authentication failure?

But when you log in with a wrong password, you get an authentication failure?

I'm not sure what the problem is, then.

If another account is working fine, have you considered copying your old files and settings to this new account and then deleting the old account?

---

### Post by Cookie-Tux on 2010-04-15
Yes, That is correct, I don't know how that would work since this account (the one I'm on) has administrator rights but still doesn't have permission to access the other user's(The locked one's)home folder.

To avoid confusion, Locked account = "a" other account = "b".

---

### Post by Cookie-Tux on 2010-04-15
Bump

---

### Post by aysiu on 2010-04-15
Log into account b

Press **Alt-F2**

This should launch a little run dialogue.

In the dialogue, paste in the command ```
gksudo nautilus
``` This will launch a root-privileged file browser window.

Press **Control-H** to see hidden files. Then go to /home/a and copy all the relevant files to /home/b

When you're done, open a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste in the command ```
sudo chown -R *b:b* /home/*b*
``` where *b* is the username of the other account (not the locked one). This will make sure that all the files and folders you copied over will be owned by the new user and not the old one.

---

