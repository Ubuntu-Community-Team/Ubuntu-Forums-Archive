---
title: "Sound scratches in games in ubuntu"
date: 2009-12-22
forum: General Help
---

### Post by rasmus91 on 2009-12-22
Hi there.

As the title says the sound scratches while playing games. And it's all games, Oblivion in wine to super tux and super tux 2... All games.

Works fine on the internet, and i can play music fine. just won't work in games.

Any suggestions?

---

### Post by audiomick on 2009-12-22
Hi.
I have no idea, but I would suggest posting some specs from your computer (processor, RAM, sound card, video card) so that someone who might have an idea can better estimate if if might be a hardware problem, for instance. :)

---

### Post by pbrane on 2009-12-22
Some games require openAL. Try creating a file in your home directory called **.alsoftrc** and add the contents **drivers = oss**.

1. Applications->Accessories->Text Editor
2. type **drivers = oss** in the test editor
3. save the file in your home directory ( /home/yourusername ) as **.alsoftrc**

Note the dot in front of the file name, it's important.

---

### Post by rasmus91 on 2009-12-23
> Hi.
I have no idea, but I would suggest posting some specs from your computer (processor, RAM, sound card, video card) so that someone who might have an idea can better estimate if if might be a hardware problem, for instance. 

haha, sure thing dude. coming right up... ;)

---

