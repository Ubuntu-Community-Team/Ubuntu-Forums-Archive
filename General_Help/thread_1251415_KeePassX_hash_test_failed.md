---
title: "KeePassX: hash test failed"
date: 2009-08-27
forum: General Help
---

### Post by jomex on 2009-08-27
while opening my database:

> The following error occured while opening the database:
Hash test failed.
The key is wrong or the file is damaged.

i'm PRETTY FREAKED right now as it contained about 100 entries..
please help!!! :(

---

### Post by mike555 on 2009-08-27
That is why you should always backup ...... if you do have a backup of your file , try to open it (it will be file with .kdb extension )

---

### Post by jomex on 2009-08-27
how is this possible anyway? i remember KeyPassX complained of not being able to save the file.
any chance the recover them?

---

### Post by phillgg on 2010-04-12
I've just had same problem.  I changed my password (for OS and Keypassx) to a 16 character password.  And it seems to me that since then I've had this problem.  I cannot open a backup copy I keep nor can I open an archived copy which was saved with my old password.  As for other users, I have 100s of passwords which I can't now access. ANy useful info out there?
Ta, Phillgg

---

### Post by karthick87 on 2010-04-12
> **phillgg said:**
> I've just had same problem.  I changed my password (for OS and Keypassx) to a 16 character password.  And it seems to me that since then I've had this problem.  I cannot open a backup copy I keep nor can I open an archived copy which was saved with my old password.  As for other users, I have 100s of passwords which I can't now access. ANy useful info out there?
Ta, Phillgg


Did you set any keyfile for your [COLOR=Red]keepassx[/COLOR].?

---

### Post by phillgg on 2010-04-13
! No !

---

### Post by phillgg on 2010-04-14
How embarrassing! I thought I had changed the password, couldn't log in, but the old password wouldn't work either.  It turns out I hadn't changed my password and I suddenly remembered the correct 'old' password today. Apologies if I've wasted anyone's time.

---

### Post by Keith1212 on 2010-04-14
glad i came upon this even tho i don't have a solution for the OP i'm now gonna back up my pw file.

---

### Post by joelc_usa on 2011-03-02
In my particular case this error message only appears on Ubuntu (Lucid Lynx).
Using the exact same .kdb file works fine on Windows and OS X.
So it's not a corrupt file.

---

### Post by bepoka on 2012-02-24
**Solution**

The resolution for this (for those people who are using keyfiles generated *on different operating systems).

The problem is the file encoding. I generated my key on linux, and on Win XP it didn't work with the aforementioned error. The answer was to save the keyfile as "UNIX" type and the encoding as UTF-8. Various adjustments to this based on your environment should fix the problem.

---

### Post by oldos2er on 2012-02-25
Closed, necromancy.

---

