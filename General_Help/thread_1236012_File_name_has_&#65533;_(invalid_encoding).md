---
title: "File name has &#65533; (invalid encoding)"
date: 2009-08-09
forum: General Help
---

### Post by ridgeland on 2009-08-09
For me this is happening in mp3 files in French with accented vowels.  I'm in the U.S.
So for instance the file:
12 - La Bottine Souriante - &#65533; Travers La Vitre.mp3 (invalid encoding)
should be:
12 - La Bottine Souriante - À Travers La Vitre.mp3

I can fix this.  Enable composite keys  Menu -> System -> Preferences -> Keyboard.  Tab Layouts - select US click [Layout Options] expand "Compose Key Position" then select [x] Left Win.  Now to compose an accented key: Press and release the "Compose Key" Left Win then the accent like ` then A -> À (the back quote, next to the 1).  Nice to find a use for that MS-key.
But the challenge is what was that &#65533; anyway?  convmv requires me to know the original locale, I haven't a clue.  I found EasyTag shows the name as it was meant to be so I copy and paste from EasyTag to Nautilus and I have the name right again.

$ locale
LANG=en_US.UTF-8

Set in /etc/defaults/locale

What should I have done to avoid the error in the first place?  Why does EasyTag understand it but Nautilus does not?  Was there an easier way than EasyTag? convmv proved useless or I just do not know how to use it.

---

### Post by michy99 on 2009-08-09
Try this:```
sudo apt-get install unifont
```

---

### Post by ridgeland on 2009-08-09
I tried unifont from synaptics GUI - no change - booted - no change
Tried apt-get ---> already latest version --- &#65533; still there.

Is more required than just installing it?

---

### Post by michy99 on 2009-08-09
Just thought it was worth a try. Sorry, I don't have any other ideas on this one.

---

### Post by 80aless on 2009-12-20
maybe try this
convmv -r --notest -f windows-1255 -t UTF-8 *

---

### Post by negativism on 2011-04-15
> **80aless said:**
> maybe try this
convmv -r --notest -f windows-1255 -t UTF-8 *

this old post just made my day. thank you, dear sir

---

### Post by mrsfixit on 2011-11-04
> **80aless said:**
> maybe try this
convmv -r --notest -f windows-1255 -t UTF-8 *

I just ran into the problem- and this old post helped me as well.

Thank goodness for the Ubuntu forums, I'd be lost without them. :razz:

---

### Post by wingnux on 2011-12-08
> **80aless said:**
> maybe try this
convmv -r --notest -f windows-1255 -t UTF-8 *

You, sir, are a genius!

---

### Post by pulsarunlimited on 2012-01-07
> **80aless said:**
> maybe try this
convmv -r --notest -f windows-1255 -t UTF-8 *

Awesome!

For me the source encoding was different, but this did the trick!

My command was:
```

convmv -r --notest -f windows-1252 -t UTF-8 *
```(so 1252 instead of 1255)

---

### Post by mrguga on 2012-01-26
1252 is Latin 
1255 is Hebrew

For brazilian Windows users, like me, 1252 is the one that works flawlessly.

Thanks for the post!

---

### Post by audunmb on 2012-01-30
Great, thanks for the post!

---

### Post by rich1842 on 2012-07-31
**Re: File name has &#65533; (invalid encoding)** 			
 			 			 		   		 		 		This really does work! Lets you delete these files.

'gksudo nautilus /home/carl/Desktop/' --- example - takes you to where your file/folder is.

[http://ubuntuforums.org/showthread.php?t=1123479](http://ubuntuforums.org/showthread.php?t=1123479)

That's where I got it.

---

