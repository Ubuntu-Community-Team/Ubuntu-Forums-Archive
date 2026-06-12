---
title: "Transfer of data"
date: 2010-07-08
forum: General Help
---

### Post by agamjain on 2010-07-08
How can I transfer data from one user account to the other? I wish to delete one of the accounts but before that I want to transfer all the data in that account to the other account so that my data is saved.

---

### Post by Ocxic on 2010-07-08
just copy the home folder of the account you want to delete to somewhere safe then:
"sudo chown user:user $HOME$"

replace "user" with your username and "$HOME$" with the location of the folder you saved.

then you can delete the account without worry and with full access to the saved data.

---

### Post by nothingspecial on 2010-07-08
You will need to use the -R flag to make it recursive

---

### Post by agamjain on 2010-07-08
> **nothingspecial said:**
> You will need to use the -R flag to make it recursive
I did it in another way. I gave full permissions to the home folder of the other user and then copied it. But I believe yours is the better way. I will keep that in mind. Thanks a ton.

---

