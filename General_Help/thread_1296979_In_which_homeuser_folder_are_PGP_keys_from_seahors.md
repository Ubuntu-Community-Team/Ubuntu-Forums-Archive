---
title: "In which /home/user folder are PGP keys from seahorse located?"
date: 2009-10-21
forum: General Help
---

### Post by j_arquimbau on 2009-10-21
Hello!
I made a full reinstalallation of ubuntu and before doing it I copied the /home folder to an external USB device. I forgot to export some PGP keys and I've been able to see that they are somewhere in the /home/user folder, but I don't know where exactly. Any help so far at this point?

Thank you.

---

### Post by Soul-Sing on 2009-10-21
./gnupg in your home.

---

### Post by j_arquimbau on 2009-10-21
I found it! Sorry for this unnecesary post. 
Here it is what I did:

I went to /home/user/.gnupg folder and I dragged the secring.gpg file to the seahorse aplication. 

I hope this can help someone.

I EDIT HERE:

Thank you leoquant. When I wrote this reply I hadn't seen your post. I just googled a bit and saw it, but I had searched for the answer some days ago and I found nothing... I must have used the wrong terms.

---

### Post by Soul-Sing on 2009-10-21
seahorse in ./gnome

---

