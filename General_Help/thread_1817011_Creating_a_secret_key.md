---
title: "Creating a secret key"
date: 2011-08-02
forum: General Help
---

### Post by skynet2060 on 2011-08-02
Hello everyone,

I was in the process of registering with the ubuntu bug squad. As i was finishing the UbuntuCodeofConduct agreement form, I ran this command to create a signature key to sign the form.

#sudo gpg --clear UbuntuCodeofConduct-1.1.txt

After the program ran I got this message.


gpg: no default secret key: secret key not available
gpg: UbuntuCodeofConduct-1.1.txt: clearsign failed: secret key not available

Apparently, I don't have a default secret key. How do I create one?

---

### Post by psusi on 2011-08-02
You skipped a step; that is the command to sign the CoC, not create the key.

---

### Post by skynet2060 on 2011-08-03
What step did I miss?

---

### Post by psusi on 2011-08-03
> **skynet2060 said:**
> What step did I miss?

The one where you create the key.

---

