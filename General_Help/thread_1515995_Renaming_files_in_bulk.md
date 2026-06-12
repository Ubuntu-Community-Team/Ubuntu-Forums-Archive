---
title: "Renaming files in bulk"
date: 2010-06-23
forum: General Help
---

### Post by dheerajkabra on 2010-06-23
[COLOR=Blue]**I have following files:**[/COLOR]

**# ls -1 *.mp3**
Megadeth - Killing Is My Business...And Business Is Good! - 01 - Last Rites-Loved To Death.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 02 - Killing Is My Business...And Business Is Good.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 03 - Skull Beneath The Skin.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 04 - These Boots.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 05 - Rattlehead.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 06 - Chosen Ones.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 07 - Looking Down The Cross.mp3
Megadeth - Killing Is My Business...And Business Is Good! - 08 - Mechanix.mp3


[COLOR=Blue]**i want to rename it to:**[/COLOR]

 01 - Last Rites-Loved To Death.mp3
 02 - Killing Is My Business...And Business Is Good.mp3
 03 - Skull Beneath The Skin.mp3
 04 - These Boots.mp3
 05 - Rattlehead.mp3
 06 - Chosen Ones.mp3
 07 - Looking Down The Cross.mp3
 08 - Mechanix.mp3


[COLOR=Blue]**Queastion is HOW ???**[/COLOR]

[COLOR=Blue]**here is my RnD so far:**[/COLOR]


 [FONT=Calibri]**# ls -1 *.mp3 | sed "s/"Megadeth\ -\ Killing\ Is\ My\ Business\.\.\.And\ Business\ Is\ Good\!\ -\ "/ /g"**[/FONT]
01 - Last Rites-Loved To Death.mp3
 02 - Killing Is My Business...And Business Is Good.mp3
 03 - Skull Beneath The Skin.mp3
 04 - These Boots.mp3
 05 - Rattlehead.mp3
 06 - Chosen Ones.mp3
 07 - Looking Down The Cross.mp3
 08 - Mechanix.mp3


[COLOR=Blue]**so it does give me the output that I want on the console...so i need to have him actually rename the files...this is what i tried:**[/COLOR]

**# ls -1 *.mp3| sed "s/\("Megadeth\ -\ Killing\ Is\ My\ Business\.\.\.And\ Business\ Is\ Good\!\ -\ "\)\(.*\)/mv & \2/g"**
mv Megadeth - Killing Is My Business...And Business Is Good! - 01 - Last Rites-Loved To Death.mp3 01 - Last Rites-Loved To Death.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 02 - Killing Is My Business...And Business Is Good.mp3 02 - Killing Is My Business...And Business Is Good.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 03 - Skull Beneath The Skin.mp3 03 - Skull Beneath The Skin.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 04 - These Boots.mp3 04 - These Boots.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 05 - Rattlehead.mp3 05 - Rattlehead.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 06 - Chosen Ones.mp3 06 - Chosen Ones.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 07 - Looking Down The Cross.mp3 07 - Looking Down The Cross.mp3
mv Megadeth - Killing Is My Business...And Business Is Good! - 08 - Mechanix.mp3 08 - Mechanix.mp3

[COLOR=Blue]**so it does show that i can run [COLOR=Black]"mv"[/COLOR] and reame the files the way i want. BUT...there are lots of spaces in each file, and hence when I append [COLOR=Black]"|sh"[/COLOR] to above command to have him actually rename the files, my [COLOR=Black]"mv"[/COLOR] command is failing.**[/COLOR]

[COLOR=Blue][B]
ANY SUGGESTIONS please.
BTW, I tried exploring perl "rename" command, but I could not understand it's regex.

thnx.
[/B][/COLOR]

---

### Post by realzippy on 2010-06-23
..I used to do that with *pyRenamer*.

[http://www.infinicode.org/code/pyrenamer/](http://www.infinicode.org/code/pyrenamer/)

---

### Post by dheerajkabra on 2010-06-23
pyRenamer is a new information for me. Many thnx. 

But I would stick to sed. I know it's not very difficult with sed, I am making some stupid mistake and that's it.

anyway...

i think I am close to the solution now, but need your help
i have to insert the qoutes for the "mv" command I mentioned above. 

How to insert quotes??

---

### Post by dheerajkabra on 2010-06-23
I GOT it:


**ls -1 *.mp3| sed "s/\("Megadeth\ -\ Killing\ Is\ My\ Business\.\.\.And\ Business\ Is\ Good\!\ -\ "\)\(.*\)/mv \"&\" \"\2\"/g" | sh**


Many thnx who viewed and replied.

---

