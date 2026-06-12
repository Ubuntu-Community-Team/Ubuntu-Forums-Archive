---
title: "Sessions"
date: 2012-04-11
forum: General Help
---

### Post by blackangelpr on 2012-04-11
Greetings does anyone knows how to delete older sessions no longer used in Ubuntu and the entired old data of it?

Thanks in advance

---

### Post by jonobr on 2012-04-11
Hello


Im not sure what you mean by a session?

It sounds like you mean a user logged in (maybe ssh or similar) and it not clearing or staying active?

Can you give an example?

Thanks

---

### Post by blackangelpr on 2012-04-11
> **jonobr said:**
> Hello


Im not sure what you mean by a session?

It sounds like you mean a user logged in (maybe ssh or similar) and it not clearing or staying active?

Can you give an example?

Thanks

Sure, i had installed 
```
sudo apt-get install qimo-session
```
so the kids could enjoy Ubuntu at the home desktop without the need to worry but id did not work as well as when i try virtually on my windows 7 pc   so i wan to remove the installation information and from the Ubuntu log in menu as other session i had tested ... any guidance its appreciated. \\:D/

---

### Post by jonobr on 2012-04-12
Hi

So you want to remove qimo-session?

to remove it

```
sudo apt-get remove qimo-session
```

This will leave behind the config files a logs,
To completely remove 

```
sudo apt-get --purge remove qimo-session
```

apologies if I am misunderstanding

---

### Post by blackangelpr on 2012-04-14
> **jonobr said:**
> Hi

So you want to remove qimo-session?

to remove it

```
sudo apt-get remove qimo-session
```

This will leave behind the config files a logs,
To completely remove 

```
sudo apt-get --purge remove qimo-session
```

apologies if I am misunderstanding

Thanks ):P

---

