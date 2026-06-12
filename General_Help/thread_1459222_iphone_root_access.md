---
title: "iphone root access"
date: 2010-04-21
forum: General Help
---

### Post by bladerunner6 on 2010-04-21
how would a enable the whole root access to my iphone 3gs (jailbroken)
i can access the mobile portion with afc through nautilus

---

### Post by Aenima99x on 2010-04-21
SSH into the iphone

---

### Post by RatSAT on 2010-04-21
mount it using ifuse with the --root option. Not tried it myself, but should work.

So 'ifuse --root /media/iPhone' or something

---

### Post by bladerunner6 on 2010-04-21
im using lucid lynx, which is support without ifuse

---

### Post by ubunterooster on 2010-04-21
sudo nautilus
then ctrl+h to show hidden files?

---

### Post by RatSAT on 2010-04-21
> **bladerunner6 said:**
> im using lucid lynx, which is support without ifuse

ifuse doesn't come with it by default no, but you can install it with 'sudo apt-get install ifuse'. It's in the universe repo, and works for me in lucid,

---

### Post by PythEch on 2012-02-26
I don't want to bump but if anyone trying to achieve this it is really simple if you already have mounted the device with iFuse:

Just open Nautilus (Files on my Mint) and press Ctrl+L. It should look like this:


Then put ":2" at the end of the line:


It should be appeared under the Network tab as "iPhone (jailbreak)".
:popcorn:

Also if you want to SSH into your iPhone simply enter "sftp://mobile@<YourDevice'sIP>/" to the address bar.

---

