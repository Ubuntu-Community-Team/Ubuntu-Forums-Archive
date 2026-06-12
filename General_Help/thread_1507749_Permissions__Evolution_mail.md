---
title: "Permissions ? Evolution mail"
date: 2010-06-12
forum: General Help
---

### Post by takka on 2010-06-12
After update to 10.04, I am not longer able to print the text content of an email. If there is an attachment, eg pdf, I can print that ok.I am logged on as a user with admin privilage and I am the only person on this machine.
I have created another user (desktop) and if logged on as that desktop user, then I can print an email.
I figure this is a permissions issue, so what is the best way to fix this issue?

---

### Post by dcstar on 2010-06-12
> **takka said:**
> After update to 10.04, I am not longer able to print the text content of an email. If there is an attachment, eg pdf, I can print that ok.I am logged on as a user with admin privilage and I am the only person on this machine.
I have created another user (desktop) and if logged on as that desktop user, then I can print an email.
I figure this is a permissions issue, so what is the best way to fix this issue?

Rename the .evolution folder, start Evolution and see if printing works.

If it does then there is some configuration problem in the old setup, but you can copy your old emails etc from the old folder to the new one.

---

### Post by takka on 2010-06-13
Thanks dcstar. printing worked again  following your suggestion. So i figured I would try to get my mail all readable again, including address book etc. I found in the .evolution folder a txt file called "printing" so I copied that file into my old original evolution file, thereby overwriting that printing file. renamed evolution file back to original. everything now back to normal.
Thanks mate:guitar:

---

