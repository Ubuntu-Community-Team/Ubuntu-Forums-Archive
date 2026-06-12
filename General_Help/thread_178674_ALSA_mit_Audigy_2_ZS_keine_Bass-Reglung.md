---
title: "ALSA mit Audigy 2 ZS keine Bass-Reglung"
date: 2006-05-18
forum: General Help
---

### Post by Peet2001 on 2006-05-18
Hallo Ubuntu-Community,

bisher bin ich immer super damit ausgekommen bei Problemen nur in Foren/Wiki zu suchen und dort die Lösungen schon fertig zu finden. Mein Problem scheint aber zu speziell, deswegen frage ich nun hier.

Ich habe Ubuntu 5.10 mit ALSA v1.0.9a am Laufen. Darunter läuft meine Audigy 2 ZS [SB0350]. Musik und Ton geht einwandfrei. Leider hat es überhaupt keine Auswirkung, wenn ich im Alsamixer den Bass hoch oder runterregel. Hab den Wert jetzt auf 50 stehen. Da hier aber die Wände dünn sind möchte ich den Wert gern runterregeln.

Was muß ich machen, damit der Bass-Pegel angepaßt werden kann. Hab ich ein Treiberproblem oder liegt das generell am ALSA?

Bitte um Hilfe. Dank vorab!

Grüße, Peter.

---------------------------------------------------
in English: (at least i will try it)

I have got a very special problem, where i havn't found an answer for on the internet/forum/wiki, jet.

I work with Ubuntu 5.10 and got ALSA v1.0.9a. My soundcard is an Audigy 2 ZS [SB0350]. The music/tone works fine, but i can't change the volume for the bass. Because of our thin walls, I want the bass on a lower value.

Where is the problem? Driver, ALSA???

If you wanna answer in english, I can read it much better then I can write it ;-) So please be welcome to answer in english.

Yours, Peter.

---

### Post by woedend on 2006-05-18
if you run alsamixer in the terminal, the second bar over I believe is "Tone" for me - is it for you also?  It should have a small green box above it, if not, push the "m" key on your keyboard and it should get the green box.  This should allow you to arrow over to the bass option and push the down arrow to lower the bass. 
Let me know if you have something different.

---

### Post by Peet2001 on 2006-05-18
](*,)  OMG, works! I have tried almost everything, but not this. Thanks.

---

### Post by Gavin77 on 2008-01-11
> **woedend said:**
> if you run alsamixer in the terminal, the second bar over I believe is "Tone" for me - is it for you also?  It should have a small green box above it, if not, push the "m" key on your keyboard and it should get the green box.  This should allow you to arrow over to the bass option and push the down arrow to lower the bass. 
Let me know if you have something different.



Sorry for resurrecting an old thread but I just wanted to say thanks.  I just got some surround speakers and the bass was really thumping, clicking the tone button worked for me :)

---

