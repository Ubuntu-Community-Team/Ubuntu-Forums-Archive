---
title: "GPG encrypt as plain text"
date: 2010-01-16
forum: General Help
---

### Post by Primefalcon on 2010-01-16
With the gpg command I used to encrypt files so they saved as plain text (the encrypted files were viewable in a plain text editor though were a encrypted nightmare)

I just forget the option in the gpg command to do this and I can't find it in a hurry either in the man file, can someone jog my memory on this please?

---

### Post by Dayofswords on 2010-01-16
wait, you want it viewable in a text editor, or not viewable?

...or what?

bit confused on the question

---

### Post by Primefalcon on 2010-01-16
> **Dayofswords said:**
> wait, you want it viewable in a text editor, or not viewable?

...or what?

bit confused on the question

I want the encrypted file to be able to be opened in say gedit rather than give an error, I know it's possible to save the encrypted file as plain text, the text is still encrypted, just the file isn't binary

---

### Post by HiImTye on 2010-01-16
-t or --textmode

---

### Post by Primefalcon on 2010-01-16
> **HiImTye said:**
> -t or --textmode
gedit is still saying it doesn't know how to open the file

---

### Post by todak on 2010-01-16
You need to first select all of the text that you wish to encrypt, then encrypt it. It will then automatically display as encrypted text in the gedit window. That is, assuming you use gedit and the encryp/decrypt plugin.

---

### Post by Primefalcon on 2010-01-16
> **todak said:**
> You need to first select all of the text that you wish to encrypt, then encrypt it. It will then automatically display as encrypted text in the gedit window. That is, assuming you use gedit and the encryp/decrypt plugin.
Nvm I found it it was using the a option for example

```
gpg -ea <filename>
```

**e** for encrypt **a** so it creates an ASCII text file rather than the binary pgp format

---

