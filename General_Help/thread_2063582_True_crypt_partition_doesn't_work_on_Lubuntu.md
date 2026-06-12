---
title: "True crypt partition doesn't work on Lubuntu"
date: 2012-09-27
forum: General Help
---

### Post by z5um on 2012-09-27
I encrypted an external usb hdd 500GB on a windows machine. Mounted it on windows, entered pw, everything was fine, data ok. Now on linux i always get this error

```
incorrect password or not a TrueCrypt volume
```

but the pw is correct, i tried it 10 times. Both true crypt versions are 7.1a. Any ideas?

---

### Post by z5um on 2012-09-27
bumb

---

### Post by spjackson on 2012-09-27
After you got this error, did you try again from Windows? There is advice about this specific error in the [TrueCrypt documentation]("http://www.truecrypt.org/docs/?s=troubleshooting"). Does that help?

If you've only recently installed Ubuntu, perhaps your key mapping is wrong. If you type the password into gedit, do you see the right characters?

---

### Post by z5um on 2012-09-27
> did you try again from Windows?
It works perfectly on windows

> If you type the password into gedit, do you see the right characters?
I did that, typed the pw in browser bar and copied it into the shell, didn't work.


I'm going to install the gui tool for TC and see if it works.

---

