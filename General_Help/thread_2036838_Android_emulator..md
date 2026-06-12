---
title: "Android emulator."
date: 2012-08-03
forum: General Help
---

### Post by shintoff on 2012-08-03
this is what i get when i run the android emulator,
please help me. :)

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  12
  Current serial number in output stream:  12

---

### Post by Sandertje on 2012-08-03
Could you give us some more information? What version of Ubuntu are you using? And did you run the emulator from inside Eclipse (as Google recommends)?

---

### Post by shintoff on 2012-08-10
@Sandertje:

I'm using ubuntu 12.04 in my pc.
Yes i launched the emulator from eclipse, and i tried it in the terminal also, but both ways i got the same result.

---

### Post by zero2xiii on 2012-08-10
Hay,

I have android emulator running on my 12.04_64bit.

Do you have java installed? What version?

Please do:
```
java -version
```

In terminal. As example my output is:
```
java version "1.7.0_03"
OpenJDK Runtime Environment (IcedTea7 2.1.1pre) (7~u3-2.1.1~pre1-1ubuntu2)
OpenJDK 64-Bit Server VM (build 22.0-b10, mixed mode)

```

also are you starting an AVD or the toolkit?

Cherz

---

### Post by shintoff on 2012-08-13
@zero2xiii:

thanks for the reply,

but i have my java configured properly. I think the problem is with my graphics. I really don't know how to fix it. :(

Is there something called 'fxlrg' that i should configure?

---

### Post by lutepluto on 2013-06-16
Do you solve this problem? I have the same problem with yours and I don't know how to fix it. It seems that this problem is assosiated with the graphic driver... Anyway, if you have solved this problem, please tell me. Thanks!

---

### Post by MidnightGrey on 2013-06-16
> **shintoff said:**
> @zero2xiii:

thanks for the reply,

but i have my java configured properly. I think the problem is with my graphics. I really don't know how to fix it. :(

Is there something called 'fxlrg' that i should configure?

Do you mean fglrx? fglrx is the proprietary graphics drivers for AMD graphics cards. fglrx =/= glx so that is not your problem but your error msg does suggest a graphics driver issue.
What graphics card do you have and what drivers are you using?

---

