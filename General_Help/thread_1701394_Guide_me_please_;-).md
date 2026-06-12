---
title: "Guide me please ;-)"
date: 2011-03-06
forum: General Help
---

### Post by vivek.pandey on 2011-03-06
hi everyone

   i installed ubuntu in my laptop some 5 months back and since then i am like 24*7 into ubuntu and ubuntu forums.. in this duration i learnt a lot especially from this forum... but i get to learn it in chunks and no definite order,,even through googling i havent been able to get some solid foundation.. i want to learn stuffs like writing my own patches or  kernel stuffs then to be able to use application just through terminal and dont require gui ;-) i want to learn shell scripting like i can write scripts which asks me which wallpaper do i like to have today on my desktop when i login for the first time on a day...and crazy stuffs like this .. i know it would require a lot of reading but i am ready to do that provided it should be orderly and with examples..can anyone better guide me or tell me links or books to go through
THANX TO ALL

---

### Post by mmsmc on 2011-03-06
c and java i think are the most applicable in your situation

---

### Post by vivek.pandey on 2011-03-06
> **healthtourism said:**
> You need to be a good programmer first. R u?

i have good skills in c and c++..then know more than just basics in java , python and web languages as javascript, php ,html know basics in perl..have done basic shell programming like c implementation of commands like grep,rm,cat,copy etc. have done basic bash shell programming like we do in c++ etc eg loops but not in big detail.can write shell codes of level like listing all java files in a folder etc

---

### Post by vivek.pandey on 2011-03-07
bump?

---

### Post by vivek.pandey on 2011-03-08
double bump :-(

---

### Post by Spyderkid on 2011-03-08
i can givee you some basic stuff of making a script...


always start with #!/bin/bash
for example...
```

#!/bin/bash
echo "hello"

```

that script outputs hello as you may have of guessed.

then you can start to ask questions and get responses...

```

#!/bin/bash
echo "play some music, queen maybe?"
read answ
if [ "$answ" = "y" ]
then
	cd Music
	rhythmbox "Don't Stop Me Now!"
else
	echo "not playing queen"
watch 1
fi

```

The script above is asking me whether I would like to listen to some queen, after the echo if I answer with 'y' then it plays the music as you can see using rhythmbox. and if i asnwer with anything else it says back "not playing queen" and the bit where it says 'watch 1' means that the script pauses for a defined amount in this case 1 second and then quits which is defined by the command 'fi'


Is that any help to make a basic bash shell script?

---

### Post by vivek.pandey on 2011-03-08
> **Spyderkid said:**
> i can givee you some basic stuff of making a script...


always start with #!/bin/bash
for example...
```

#!/bin/bash
echo "hello"

```

that script outputs hello as you may have of guessed.

then you can start to ask questions and get responses...

```

#!/bin/bash
echo "play some music, queen maybe?"
read answ
if [ "$answ" = "y" ]
then
	cd Music
	rhythmbox "Don't Stop Me Now!"
else
	echo "not playing queen"
watch 1
fi

```

The script above is asking me whether I would like to listen to some queen, after the echo if I answer with 'y' then it plays the music as you can see using rhythmbox. and if i asnwer with anything else it says back "not playing queen" and the bit where it says 'watch 1' means that the script pauses for a defined amount in this case 1 second and then quits which is defined by the command 'fi'


Is that any help to make a basic bash shell script?

i really appreciate your help. thanx for that but as i already mentioned in first post i know these basic steps i want to go for deeper things like event shell programming net programming writing my kernel patches etc.. how should i learn that?

---

### Post by Spyderkid on 2011-03-08
not a clue sorry can't help you there

---

