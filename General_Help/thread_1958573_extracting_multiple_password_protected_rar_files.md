---
title: "extracting multiple password protected rar files"
date: 2012-04-14
forum: General Help
---

### Post by sohlinux on 2012-04-14
Is there any way of extracting multiple password protected rar files which all have the same password without entering the password for each rar file as they are extracted?

I can extract multiple rar files to separate directories OK but each rar file asks me for the password, is there anyway of just letting it get on with it as I have 300 password protected rar files to extract and I dont want to keep entering the password for each one as its extracted.

```

find -type f -name '*.rar' -exec unrar x {} \;

```

---

### Post by CharlesA on 2012-04-14
Does unrar have a switch for providing the password? If not, you might be able to pipe the echoed password or something. I've seen that used with sudo.

```
echo password | unrar x
```

---

### Post by sohlinux on 2012-04-14
> **CharlesA said:**
> Does unrar have a switch for providing the password? If not, you might be able to pipe the echoed password or something. I've seen that used with sudo.

```
echo password | unrar x
```

thanks but that doesnt work im afraid

enter password  - (password will not be echoed)

also when I extract the rar files it first asks for the password then it asks if I want to use the same password for all files inside the rar file 

use current password (Y)es (N)o (A)ll

looks like I will just have to extract them one by one unless anyone has an ideas? I think this is a difficult one.

thanks

---

### Post by matt_symes on 2012-04-14
Hi

From man unrar

> -p-    Do not query password.

Does that help along with CharlesA suggestion of piping in a password ?

Kind regards

---

### Post by matt_symes on 2012-04-14
Hi

Try something like this

```
unrar e -p_pass_ test.rar test2.rar
```Where _pass_ is the password above. No spaces between the -p and the password.

Kind regards

---

### Post by sohlinux on 2012-04-14
> **matt_symes said:**
> Hi

From man unrar



Does that help along with CharlesA suggestion of piping in a password ?

Kind regards

that gives out  - CRC failed in the encrypted file

---

### Post by sohlinux on 2012-04-14
> **matt_symes said:**
> Hi

Try something like this

```
unrar e -p_pass_ test.rar test2.rar
```Where _pass_ is the password above. No spaces between the -p and the password.

Kind regards

that worked!

find -type f -name '*.rar' -exec unrar x -ppass {} \;

why didnt I think of that.

thanks

---

