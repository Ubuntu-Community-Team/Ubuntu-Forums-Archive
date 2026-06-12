---
title: "Evolution - How do I import emails into another email program"
date: 2010-08-06
forum: General Help
---

### Post by Dave_gb on 2010-08-06
Normally I just use the backup feature in evolution but how would I go about saving my emails if I wanted to import them into another email program?

I am going to install Mint 9 KDE on a separate partition and I have found evolution does not play nicely in KDE so was hoping there was a way of importing my evolution mail into Mints KDE email program.

Thanks for any help

Cheers
Dave

---

### Post by apmcd47 on 2010-08-06
Evolution uses mbox format, so it should be possible to find locally saved messages and import them into say Thunderbird simply by putting the message folders into the correct directory structure. However kmail (and Thunderbird, since I mentioned it) has an import feature and looks as though it can import evolution V1 and V2 mail. Just make sure your $HOME/.evolution folder is copied into your new $HOME and start up kmail/kontact, select *File/Import Messages...* and follow the instructions.

Andrew

---

### Post by Dave_gb on 2010-08-06
Thanks Andrew, I will give that a try this evening.

---

### Post by Dave_gb on 2010-08-06
Worked a treat, thanks again.

---

