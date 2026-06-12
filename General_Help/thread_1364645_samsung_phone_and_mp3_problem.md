---
title: "samsung phone and mp3 problem?"
date: 2009-12-26
forum: General Help
---

### Post by tonyuk123 on 2009-12-26
hi,
my daughter has a samsung tocco lite or GT-S5230 phone
it has a 2gb memory card and she wants a lot of her cd's in mp3 on it
i ripped some of them using RipperX into mp3 at 128k
ok the phone doesn't get recognised by ubuntu even if using BitPim so i tried using the memory card directly in the pc, which is fine
but when i put the files on the card into the phone, it says files are wrong format!
so i tried using Grip also, which i did the same process (re-ripped the files) but it shows the files as you would expect, in both cases says they are mp3, but this time it just ignores playing them and selects the next 'sound' it can play, no error atall
anybody got any idea what i am doing wrong?

my daughter bluetoothed a couple of tracks from her old phone, which work perfectly on it, so we know the phone is ok
would be nice to get ubuntu to talk directly to the phone but just being able to add mp3's to the memory card would do
Tony

---

### Post by tonyuk123 on 2009-12-26
ok, i found out you can make the phone a mass storage device which eliminates the need totake the card out now, no different on the mp3 side though!

---

### Post by NFblaze on 2009-12-26
I've never used RipperX or Grip. I use (sound-converter  to convert and sound juicer if ripping from CDs rarely)  

Though, can they also rip into AAC. You can try to see if that will play.

Also do you have the encoder for MP3 which is called LAME.

Type in '*whereis lame*' or '*man lame*' in a terminal and see if you get the output.

---

### Post by tonyuk123 on 2009-12-26
well i didn't have lame, but i do now, saw something about it in another part of forum
would that mean that ripperx or grip wouldn't have made them mp3 before?
it seemed to think they were on pc and phone

---

### Post by NFblaze on 2009-12-26
No if you didnt have LAME they wouldnt have been able to encode them, now the program might have still gave the files the .mp3 extension...which would have been useless for the phone's decoder as it would've been a junkfile with .mp3 after it.

---

