---
title: "Empathy, Evolution &amp; hotmail contacts"
date: 2010-05-31
forum: General Help
---

### Post by cyberEl on 2010-05-31
Hi, i use 10.04 and i have an issue with my mail contacts.
when i was on windows i used "windows mail" now i use empathy as messenger and evolution as mail client which works fine.
my problem is that i cannot import my hotmail contacts and my folders from "windows mail" to evolution
i also tried to export the contacts from empathy to evolution with no result.
i tried to find some help in the forum and in  google without positive results too.
My contacts are also imported and saved in a gmail account, can i import them in evolution from gmail?
I hope you can help me!

---

### Post by Seq on 2010-05-31
I can't help with Microsoft's email products, but for Evolution/Gmail, you can do 'File > New > Address Book'. There is a 'Google' type in that list that will sync with your GMail address book.

---

### Post by cyberEl on 2010-05-31
> **Seq said:**
> I can't help with Microsoft's email products, but for Evolution/Gmail, you can do 'File > New > Address Book'. There is a 'Google' type in that list that will sync with your GMail address book.

thanx, i resolved like this:

1.import hotmail contacts in gmail
2.export contacts from gmail as "vcard format"
3.import "vcard" in evolution

all this because evolution cannot import .cvs files......

i think that importing my folders from the old mail client (windows live mail) it is impossible, right?

---

### Post by Seq on 2010-05-31
> **cyberEl said:**
> thanx, i resolved like this:

1.import hotmail contacts in gmail
2.export contacts from gmail as "vcard format"
3.import "vcard" in evolution

If you set up your google contacts in Evolution, you get two-way sync. Only useful if you use gmail I suppose.

> **cyberEl said:**
> all this because evolution cannot import .cvs files......

"File > Import", then selecting 'import a single file' gives several csv options. I would imagine it is possible. Worst-case scenario would be some sed-fu to change the order to something Evolution expects.

> **cyberEl said:**
> i think that importing my folders from the old mail client (windows live mail) it is impossible, right?

No idea. Never used Windows Live mail.

---

### Post by malleeblue on 2010-06-07
> **cyberEl said:**
> i think that importing my folders from the old mail client (windows live mail) it is impossible, right?

There might be a way, but it'll seem fiddly. If it's possible for you to set up another account in Windows Mail, but so that your current account is still visible, then you could set up your Gmail account as an IMAP account in Windows Mail (remember to turn on this option at Gmail first). Then, in Windows Mail, just copy and paste (or drag and drop) your mails from your local account to the Gmail IMAP account. Once complete, return to Evolution and do the same in reverse.

Hopefully this makes sense, but I can offer more detail if you need it.

---

