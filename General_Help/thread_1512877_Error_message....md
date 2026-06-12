---
title: "Error message...???"
date: 2010-06-18
forum: General Help
---

### Post by robertcoulson on 2010-06-18
Can anyone tell me why I get this error message when I click the "CHECK" button in "UPDATE MANAGER"...???
Robert

---

### Post by WorMzy on 2010-06-18
You haven't added the gpg key for a the medibuntu repository.

Open a terminal and run the following: ```
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring
```

---

### Post by QIII on 2010-06-18
How did you add medibuntu to your sources list?

Your problem can most likely be solved here, with the most important part being in the first gray box down.  Read through the rest of it, though, because you probably want the stuff medibuntu offers if you have it in your sources list already.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by robertcoulson on 2010-06-18
***sudo apt-get --yes --quiet --allow-unauthenticated install[[B][I]/I]** medibuntu-keyring*[/B].....Did mot work, another error came up...Well, I can live with it...Thanks very much for trying guys.
Robert

---

### Post by WorMzy on 2010-06-18
What was the other error that came up?

---

### Post by robertcoulson on 2010-06-18
(sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring).......ah..seemed to work when I tried it a 2nd time..Thanks for the help.
Robert

---

