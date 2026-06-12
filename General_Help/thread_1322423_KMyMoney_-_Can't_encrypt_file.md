---
title: "KMyMoney - Can't encrypt file"
date: 2009-11-10
forum: General Help
---

### Post by rfkrocktk on 2009-11-10
When I go to the Settings -> Configure KMyMoney -> Encryption page, all of the encryption options are grayed out. Is there another package I need to install to enable encryption?

---

### Post by Hei Ku on 2009-11-11
Have you setup your own GPG key? You need at least. Being all gray means that KMM has not found any suitable keys it can use to encrypt your file.

---

### Post by rfkrocktk on 2009-11-11
How do I generate my own GPG files? And what exactly does that mean? Are GPG keys stored somewhere specifically on my machine? Sorry I'm kind of new at this. I'm no stranger to encryption, but I haven't encountered having to do this.

---

### Post by Hei Ku on 2009-11-11
First, you need to generate a GPG private/public key using OpenGPG and add it to your ring.
I'm sure you will find a tutorial for this on wiki.ubuntu.com

---

