---
title: "Help required with pwgen commands"
date: 2009-11-01
forum: General Help
---

### Post by Rytron on 2009-11-01
Hi.
I used to use the program **pwmanager**. However it is now no longer in the repos.

There is a command line tool: **pwgen**

How would I use **pwgen** to generate a password that contained upper & lower case letters, numbers & special characters? I would like the password to be 512 characters in length.

Thank you.

---

### Post by Rytron on 2009-11-02
Anyone?

---

### Post by HiImTye on 2009-11-02
[http://lmgtfy.com/?q=man+pwgen](http://lmgtfy.com/?q=man+pwgen)

---

### Post by Rytron on 2009-11-02
Okay. I made this line:
```
pwgen -1 -y -s
```
How do I make it 512 characters long? The default password is 8 characters!

```
Notes:
-1 Print the generated passwords one per line.
-s, --secure
-y, --symbols
```

---

### Post by Rytron on 2009-11-04
I've just decided to settle with 

```
keepassx
```

to generate long passwords.

;)

---

### Post by sisco311 on 2009-11-04
> **Rytron said:**
> Okay. I made this line:
```
pwgen -1 -y -s
```
How do I make it 512 characters long? The default password is 8 characters!

```
Notes:
-1 Print the generated passwords one per line.
-s, --secure
-y, --symbols
```

```
unset passwd && for i in $(seq 0 63);do passwd=${passwd}"$(pwgen -1 -y -s)";done && echo $passwd
```

---

### Post by Rytron on 2009-11-04
Much appreciated sisco311.
;)

---

### Post by sisco311 on 2009-11-04
> **Rytron said:**
> Much appreciated sisco311.
;)

d'oh, there is an easier way:
```
 pwgen 512 -1 -y -s
```

---

### Post by Rytron on 2009-11-04
> **sisco311 said:**
> d'oh, there is an easier way:
```
 pwgen 512 -1 -y -s
```

Precise! ):P

---

