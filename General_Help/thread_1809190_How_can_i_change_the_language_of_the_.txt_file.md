---
title: "How can i change the language of the .txt file ?"
date: 2011-07-21
forum: General Help
---

### Post by Trolen on 2011-07-21
I have a file which is in .txt .

And has written inside , with a different language than the ubuntu.
So ....

Now i open it , and it shows to me like this > $)IR""RJU((AF < how can i change the format ?

In windows we have the regional settings and we change them to unicode , and everything are fixed.

Here what can i do ?

I 'm desperate ! 

Please help me! :KS

---

### Post by Vaphell on 2011-07-21
do you use gedit?
in Save as... you can select encoding, the same thing can be done in Open file dialog (combobox at the bottom). Gedit has a defined queue of encodings to try (you can customize that), let's say iso8859-1, utf8, iso8859-2. If it tries 1st one and fails at reading the file, it picks second one and tries again.

It's strange that your file shows garbage, ubuntu and gedit have utf8 as a default setting so if you haven't played with settings it should work right off the bat.

---

### Post by Trolen on 2011-07-21
done it...but still is like garbage.

---

### Post by Vaphell on 2011-07-21
can you post an example of garbage and what it's supposed to look like?

---

### Post by Trolen on 2011-07-24
It took me so long but i have figure it out and found out the way.

I went into the 'Text Editor' > Open File > My file > Encoding > Greek > Then i saved it as UTF-8 and everything was clear :)

Thank you for your help :)

---

