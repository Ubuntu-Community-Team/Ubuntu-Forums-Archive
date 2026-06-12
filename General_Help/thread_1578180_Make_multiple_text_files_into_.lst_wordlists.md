---
title: "Make multiple text files into .lst wordlists?"
date: 2010-09-20
forum: General Help
---

### Post by jakeeee on 2010-09-20
Is it possible? :)

---

### Post by jakeeee on 2010-09-20
Bump. :P

---

### Post by amauk on 2010-09-20
what is an lst wordlist?

---

### Post by jakeeee on 2010-09-20
lst is the file extension.
Its used for programs like aircrack-ng to crack WPA encryption keys.
Aircrack will go through the wordlist and test to see if that word is the correct passphrase.

But I want to make my own wordlist.
Anyone know how?

---

### Post by CharlesA on 2010-09-20
cat samefile >> someotherfile?

---

### Post by amauk on 2010-09-21
something like this?
```
cat *.txt | sort -u > wordlist.lst
```

---

### Post by n~kf)}BW% on 2010-09-21
You got your answer, but if you are a total beginner, i can explain further:

Open up the terminal
```

cat /mywordlists/* | sort -u > wordlist.lst

```Sort -u will sort your wordlist and remove all duplicates.
If your wordlists are big, sort -u can take a long time, but don't give up on it :)

---

### Post by jakeeee on 2010-09-24
Thank you guys(:
Think I got it to work.

---

