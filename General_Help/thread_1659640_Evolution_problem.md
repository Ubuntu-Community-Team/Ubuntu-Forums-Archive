---
title: "Evolution problem"
date: 2011-01-04
forum: General Help
---

### Post by Aswdriver on 2011-01-04
I have a new problem with evolution. When I launch the program it starts and then almost immediately trashes itself. I am not a power user so I don't know where to look to solve this problem. Any help will be appreciated:confused: The account has been working since October so it's unlikely a provider problem.

---

### Post by howefield on 2011-01-04
Post moved to its own thread.

Try opening via a terminal, Applications > Accessories > Terminal.

What's the output from the command

```
evolution
```

---

### Post by Aswdriver on 2011-01-04
Tried that got the following error message. EI: MAIL PREFSSegmentation fault
It blew itself away almost immediately

---

### Post by dino99 on 2011-01-04
into your /home you have a hidden .evolution folder which might be corrupted

sudo dpkg-reconfigure evolution

---

### Post by Aswdriver on 2011-01-04
Tried that. Same result. Same error message  EI: MAIL PREFSSegmentation fault
Thanks G.

---

### Post by dcstar on 2011-01-05
> **Aswdriver said:**
> Tried that. Same result. Same error message  EI: MAIL PREFSSegmentation fault
Thanks G.

Rename the **.evolution** folder and then start Evolution.

---

### Post by Aswdriver on 2011-01-06
Thanks David, The problem resolved itself. I do not know what caused the problem, which is a concern because it has now happened twice. I changed permissions on .evolution to 777 but since it had no immediate impact I don't think it was a solution. I went to the e-mail account using a Windows machine with no problem so the account appeared to be OK. Perhaps it's a bug?

G.

---

