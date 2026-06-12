---
title: "Conky doesn't autostart"
date: 2011-09-10
forum: General Help
---

### Post by Pirate Zoro on 2011-09-10
I recently started using conky, but can't get it to autostart. I found a command on these forums, but it doesn't work. Conky itself works just fine when I start it via run or in the terminal, I just can't get it to run automatically.

---

### Post by Frogs Hair on 2011-09-10
```
#!/bin/bash
 sleep 10 && conky;

```

Copy and paste the code into Gedit and save as start . Save the script in documents and create a folder for it . (any name you want)

Right click the start document and enter Properties > Permissions and check the execute box .

Close the folder and open startup applications and select add and enter the name Conky.

In the command box use browse and migrate to the folder where your script is saved . Open the folder and click on your script .

Finally , select save and your done 

The sleep 10 portion is a delay to let other processes , such as Compiz to start before Conky . You can increase or decrease this time .

---

### Post by Enigmapond on 2011-09-10
Frogs Hair, Thanx for this simple script. Conky always started too soon when I just entered the command in the startup apps. This delays it. Works like a charm and gives everthing a chance to start and connect. Cheers!

---

### Post by Frogs Hair on 2011-09-10
Your welcome !

---

### Post by Pirate Zoro on 2011-09-13
@ Frogs Hair, thank you. Turns out the problem was that the script I had set the time variable too low. Works perfectly now :)

---

### Post by Sigma1 on 2012-05-21
This thread suggested an alternative solution to me, without the script. In the start-up applications command box, put ```
conky -p 10
```.
Explanations here:
```
man conky
-p | --pause= SECONDS
Time to pause before actually starting Conky

```

---

