---
title: "Ubuntu and Dropbox"
date: 2010-01-25
forum: General Help
---

### Post by b1lancer on 2010-01-25
Hey all,

I download the package from the dropbox website and installed it... and nothing. It doesn show up anywhere. Dropbox does not show up anywhere within nautilus. How can I be sure that dropbox didn't install? Is there some command I can use to see if it is installed somewhere?

---

### Post by howefield on 2010-01-25
It should show in your Applications > Internet menu. But you might need to logout/log back in for it to take effect ?

Once you launch that for the first time, it'll download some more packages and when done, start the account wizard.

---

### Post by duracell999 on 2010-01-25
I would open up the terminal and just type in "dropbox" and see what happens. You might want to try different versions by typing "drop" and then hitting tab several times.
If you want to know where it is installed to you can find out by using the "whereis" command in the terminal.
For example: "whereis dropbox"

--------------------------------------

too slow ^^

---

### Post by howefield on 2010-01-25
> **duracell999 said:**
> I would open up the terminal and just type in "dropbox" and see what happens.

The command from the menu launcher is 

```
dropbox start -i
```

Just for info.

---

