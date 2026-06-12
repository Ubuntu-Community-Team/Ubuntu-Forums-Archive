---
title: "How to UnZip in Kubuntu."
date: 2011-08-27
forum: General Help
---

### Post by JoshDempsey on 2011-08-27
Hi guys.

I was wondering how to UnZip a file in Kubuntu, as when I select the folder to UnZip, I get the message: "Error opening Ark - failed to find file path."

I have searched around the web a little and have not found anything.

Any help you be Much appreciated.

Thanks.

:)

---

### Post by dniMretsaM on 2011-08-27
Run this in Terminal and post the output:
```
ark --version
```

---

### Post by JoshDempsey on 2011-08-27
Thanks.

I get;

```

josh@JoshPC:~$ ark --version
Qt: 4.7.2
KDE Development Platform: 4.6.2 (4.6.2)
Ark: 2.16
josh@JoshPC:~$ ^C
josh@JoshPC:~$ 

```

Josh.

---

### Post by dniMretsaM on 2011-08-27
What happens if you open Ark and then try to unzip the file from there (instead of finding the file and then right click-unzip)?

---

### Post by JoshDempsey on 2011-08-27
I get the same message (pictured in the attachment.)

---

### Post by howefield on 2011-08-27
Do you have rar and unrar installed ?

If not, in terminal type..

```
sudo apt-get install rar unrar
```

Or install with kpackagekit.

---

### Post by dniMretsaM on 2011-08-27
Yeah do what howefield said. It can't find the program unrar (that allows you to unpack .rar archives), not the actual path. Thanks for the screen shot.

---

### Post by JoshDempsey on 2011-08-27
Thanks guys.

This worked perfectly in about twenty seconds!

[A very happy] Josh :D

---

### Post by dniMretsaM on 2011-08-27
Glad you got it to work! It would be very helpful if you mark this thread as solved. Click on "Thread Tools" (up at the top) and then select "Mark Thread As Solved."

---

