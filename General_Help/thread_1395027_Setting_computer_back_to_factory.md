---
title: "Setting computer back to factory"
date: 2010-01-31
forum: General Help
---

### Post by machosos on 2010-01-31
Hello all....I am running 9.10 and I might be selling my computer.  The person interested is interested in trying out Ubuntu.  I want to be able to give it to them as a fresh install.  Is there a way to restore the computer back to when I first installed Ubuntu?  I just dont want to go through the hassle of downloading the disk and everything again.  Not sure if there is an easy way to restore everything back to defaults and even delete all of my info if possible.

Thanks!

---

### Post by milton1 on 2010-01-31
Best way to do this really is a fresh install.

---

### Post by audiomick on 2010-01-31
+1 Fresh install. You don't have to put any extras on, just a plain install with everything working.

---

### Post by Swagman on 2010-01-31
Cant he add user with 777 privileges and then delete old user.
gksudo nautilus and copy over stuff in old user dir then delete it ?

---

### Post by howefield on 2010-01-31
> **Swagman said:**
> Cant he add user with 777 privileges and then delete old user.
gksudo nautilus and copy over stuff in old user dir then delete it ?

Yep, but it isn't what he wants - a fresh install.

Given the sheer speed of installing Ubuntu (especially without configuring, installing extras, personalising ect) I'd go for a real fresh install.

---

### Post by machosos on 2010-02-01
ok so i have tried doing the fresh install.  I downloaded and burned the image CD.  I boot from disk and i get a select language prompt.  I select english and then I am unable to select install or anything.  Did I miss a step or anything?

---

### Post by howefield on 2010-02-02
Check the mdsum to ensure integrity of the disk ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by electricFan on 2010-02-02
> **machosos said:**
> ok so i have tried doing the fresh install.  I downloaded and burned the image CD.  I boot from disk and i get a select language prompt.  I select english and then I am unable to select install or anything.  Did I miss a step or anything?

There may be something wrong with the download or disk.  Check the MD sum as the poster above me suggested.

---

### Post by machosos on 2010-02-02
cool thanks...i will give it a try tonight or tomorrow

---

### Post by machosos on 2010-02-02
yeah i will give it a try soon...in the case that something is wrong with it i am guessing i should just re-download it from ubuntu site and burn the iso again?

---

### Post by gletob on 2010-02-02
> **machosos said:**
> yeah i will give it a try soon...in the case that something is wrong with it i am guessing i should just re-download it from ubuntu site and burn the iso again?

Yes

EDIT: BTW if you follow the instructions above and find that the md5 is not off.  Then try re-burning you disc at a lower speed.

---

### Post by HPD2 on 2010-02-02
You can also try an oem install, not sure if the live cd will do that but if u use the alternate install cd u can hit f4 and sellect an oem install. That will allow the person buying the maching to enter his or her name and what not.

---

### Post by howefield on 2010-02-04
> **HPD2 said:**
> You can also try an oem install, not sure if the live cd will do that...

That's a pretty good idea, I didn't know there was such an option. Just for the record, the live cd does have an OEM install option.

---

