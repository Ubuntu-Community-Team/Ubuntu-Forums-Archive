---
title: "sending mail"
date: 2012-03-25
forum: General Help
---

### Post by Kiplagat on 2012-03-25
how do you send a mail to another user through the localhost using bash?

---

### Post by haqking on 2012-03-25
> **Kiplagat said:**
> how do you send a mail to another user through the localhost using bash?

on the same machine ? or networked ?

terminal message ?

see

```
man write
```

```
write <username>
```

enter

type message

enter

---

### Post by SeijiSensei on 2012-03-25
Install the command-line mail client with

```
sudo apt-get install mailutils
```

Now you can send an e-mail to user "joe" like this:

```
echo 'this is my message' | mail -s 'this is my subject' joe
```

If you want to send a long message, put it into a text file, then use

```
mail -s 'longer message for you' joe < /path/to/messagefile
```

However I'd recommend using the full-screen text-mode client called **alpine**.  It's a very powerful mail client from the University of Washington and was developed in conjunction with the IMAP protocol.  It's also very easy to configure and use; there are on-screen menus throughout.

---

