---
title: "Can't open old jpeg images"
date: 2010-04-28
forum: General Help
---

### Post by rapattack1 on 2010-04-28
Gimp gives me an error saying i haven't got the jpeg plugin but i save images all the time as jpg's so what is going on? I had a look in synaptic and i can't pin point which plugin i am supposed to get.:confused:

---

### Post by dino99 on 2010-04-28
usually you need the ubuntu "extra" repo and you can add medibuntu repo too.
The other way is to translate theses jpeg into an other format.

---

### Post by Leppie on 2010-04-28
check if the packages libjpeg62 and libopenjpeg2 are installed.
with what app did you save these old jpeg's?

---

### Post by rapattack1 on 2010-04-28
The first one was installed but not the second so i installed it. I still can't open those files even after a reboot.
I did a capture of some of the files next to ones that do open but now i can't attach that. For some reason i click onto 'manage attachments' and nothing is popping up so i can attach....:confused:

---

### Post by Leppie on 2010-04-29
with what application were these images created?
are you sure these files aren't corrupt?

---

### Post by rapattack1 on 2010-04-29
It was yearssssssssssssssss ago so i couldn't tell you. All i know in this install of Ubuntu i can't open them. In the previous install/version i was about to. They have been burnt on a cd for years. Some can open and some cannot so this is odd.

---

### Post by Leppie on 2010-04-29
could you attach one of those?

---

### Post by rapattack1 on 2010-04-30
I will try and attach. It takes maybe 5 minutes for the thing to pop up so i can attach here in the forum. I have no idea why.
OK I tried several times and several different pic's but they would not attach. Other pictures that were viewable would attach but the ones that are not viewable would not attach

---

### Post by ssj6akshat on 2010-04-30
> **rapattack1 said:**
> Some can open and some cannot so this is odd.
then they are probably corrupt.this happens a lot with my crappy HDD

---

### Post by jobix on 2010-04-30
Can you execute this command on one of those photos and see what you get:
> file your_photoname.jpg


---

### Post by rapattack1 on 2010-04-30
Is this right?
carla@carla-desktop:/cdrom$ file aud5.jpg
aud5.jpg: data
carla@carla-desktop:/cdrom$

---

### Post by no2498 on 2010-04-30
sounds like you had a diff cd/dvd burner 
samsung / sony

or just a diff burner program

i have a few cds like that that i made on 2 diff computers

hope this points you the right way

---

### Post by jobix on 2010-04-30
> **rapattack1 said:**
> Is this right?
carla@carla-desktop:/cdrom$ file aud5.jpg
aud5.jpg: data
carla@carla-desktop:/cdrom$

That's correct but it doesn't look good. :(

If I run that command on one of my files this is what I get:
```
file hello.jpg 
hello.jpg: JPEG image data, JFIF standard 1.01

```

You can try the "convert" command and see it that works. I doubt it will though.

---

### Post by StuartN on 2010-04-30
> **rapattack1 said:**
> carla@carla-desktop:/cdrom$ file aud5.jpg
aud5.jpg: data

Is it possible that these are JPEG2000 (jp2) files? There is a Gimp plugin to read jp2, and apparently the next Gimp (2.7) will read them directly.

---

### Post by rapattack1 on 2010-05-01
no2498-yes i have probably 3 burners since that cd of data was burned and it would have been done in windows back then as i had no idea Linux existed. OK just discovered something. I took the cd over to my windows machine and they won't open there either. The cd is data from several cd's . It is actually a data dvd as i was gathering several data cd and making one dvd. If you know what i mean. So the burn process would have rendered them corrupted i think?! I thought i had viewed and opened the files since that burn but maybe i am wrong.

jobix-How do i convert via th terminal? I haven't heard of that. Still a beginner lol.

StuartN-I really don't know about that information. It sounds familiar but i don't know.

---

### Post by jobix on 2010-05-02
You open up a terminal by going to Applications->accessories->Terminal. This gives you command line access. Here you execute the convert command. Try this:

> convert yourfile.jpg newfile.jpg


This will try to convert your jpg image to a new jpg image. However, I doubt it's going to work given that your file isn't even being recognized as a jpg image file. But, hey, we can still try. To get more info on convert, type "man convert" at the command line.

---

### Post by rapattack1 on 2010-05-02
Yep know the terminal. Just not that command.
Anyway this is what i got:
carla@carla-desktop:/cdrom$ convert aud5.jpg for.jpg
convert: Not a JPEG file: starts with 0x00 0x00 `aud5.jpg' @ jpeg.c/EmitMessage/232.
convert: missing an image filename `for.jpg' @ convert.c/ConvertImageCommand/2775.

I was told first time i tried it that i had to install imagemagick so i did.

---

### Post by noelvh on 2010-05-02
I would install gthumb and try and open them in that, If that works re-save them. Another thought is to install a windows app called irfanview, it's free and a really good app.

Noel

---

### Post by rapattack1 on 2010-05-02
Isn't Gimp enough? I have never done the wine thing and since i could stuff it i prefer not to go that far

---

### Post by jobix on 2010-05-02
rapattack1, convert didn't work either. It does not think that your file is a JPEG. Sorry, I don't know what else you can do. One last attempt, just for the sake of trying, do you think you could upload a corrupt image here? I'll like to try and see if I can play with the header bits and see if that helps. The probability of success is very low so you don't have to do this if you don't feel like it.

---

### Post by rapattack1 on 2010-05-03
I tried to upload the corrupt image earlier and got no where. There is also a problem in the window that comes up to upload pic's is extremely slow. Takes more than 2 minutes to popup. I have no idea why....
Oh thats odd it opened quick today. Maybe it was the autoremove i did yesterday on some stuff when i was in the terminal...odd.
OK I tried but this is what i got: word.JPG:
This is not a valid image file. 
Ah well they are gone.....

---

