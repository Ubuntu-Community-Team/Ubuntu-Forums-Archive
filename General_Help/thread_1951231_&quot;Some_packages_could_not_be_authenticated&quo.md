---
title: "&quot;Some packages could not be authenticated&quot;"
date: 2012-04-02
forum: General Help
---

### Post by grey1beard on 2012-04-02
I'm trying to sort out my sound system (!) in Natty on a 32-bit Toshiba laptop, and as a first step I had problems downloading Audacity via Software centre, which said "check your internet connection" - there's nothing wrong there.
Then tried via terminal which gave "E: Some packages could not be authenticated", so I tried, successfully, using package manager.
Then I went back to terminal to use **sudo apt-get install pavucontro**l to get pulse audio, but again got "E: Some packages could not be authenticated".

Do I need to install some repository or other to get unauthenticated packages, or do I have some other problem ?

Thanks in advance,
John

---

### Post by Lars Noodén on 2012-04-02
Did you refresh the database first?

```

sudo apt-get update

```

---

### Post by grey1beard on 2012-04-02
I ran update manager first, but it reported the system was up to date.
Is this the same thing, or does running apt-get update in terminal more effective/different in some way ?

John

---

### Post by grey1beard on 2012-04-02
Just in case, I've just carried out your suggestion, and all is now installing correctly.
I have to assume the answer to my question above is yes, it is different, but I'd be interested to know what the difference is.

John

---

