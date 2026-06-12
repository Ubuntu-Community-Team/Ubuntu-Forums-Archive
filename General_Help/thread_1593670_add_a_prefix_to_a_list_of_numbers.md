---
title: "add a prefix to a list of numbers???"
date: 2010-10-11
forum: General Help
---

### Post by spiky001 on 2010-10-11
I have a list of numbers I want to add a prefix number to the front of all of them,Is this possible with terminal, example "222222" put "1111" in front make the number "111122222" I have the list of 2222etc but not a list of 1111, Hope you can make sense of this thks

---

### Post by spiky001 on 2010-10-12
Bump

---

### Post by apmcd47 on 2010-10-12
> **spiky001 said:**
> I have a list of numbers I want to add a prefix number to the front of all of them,Is this possible with terminal, example "222222" put "1111" in front make the number "111122222" I have the list of 2222etc but not a list of 1111, Hope you can make sense of this thks

More info required. How is the list held? Is it the same prefix for the list?

Given a file named numbers containing e.g.
```
22222
22223
22224
22225
22226
...
...
22999
23000
``` and wanting to prefix each number with 1111 you could try
[PHP]sed -i.bak 's/^/1111/' numbers[/PHP]

Andrew

---

### Post by spiky001 on 2010-10-12
Hi thks for reply, the list is called numberlist.txt at the moment,The numbers are all random, yes the prefix is the same number for all of them, I dont have a file for the prefix numbers, It,s just a number to go infront of all the numbers in the list

---

### Post by apmcd47 on 2010-10-12
Okay, so my sed solution should work for you.

Andrew

---

### Post by spiky001 on 2010-10-15
I would like to thank you apmcd47 just got round to trying what you suggested worked like a dream

---

