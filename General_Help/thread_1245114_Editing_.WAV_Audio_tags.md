---
title: "Editing .WAV Audio tags"
date: 2009-08-20
forum: General Help
---

### Post by Ceiber Boy on 2009-08-20
Hello All

i have a couple of .WAV files leftover from my microsoft days.

i want to edit the the 'audio tags' that are attached to the file. but the properties box or rhythmbox music player dose not allow me to do this!

once i've put the artist and track title on the tag (instead as the file name) i'll then want to convert them all to .flac files.

is their a program that will allow me to edit the audio tags?

thanks

---

### Post by credobyte on 2009-08-20
Try EasyTag ( available in repos ).

---

### Post by CatKiller on 2009-08-20
WAVs don't have tags. Trying to force them to have tags will cause them to not work as WAVs any more. Convert them to FLAC files first (which does support tags) and then tag them.

---

### Post by mcduck on 2009-08-20
> **CatKiller said:**
> WAVs don't have tags. Trying to force them to have tags will cause them to not work as WAVs any more. Convert them to FLAC files first (which does support tags) and then tag them.

+1 for this

(although there are ways to attach tags to .wav files, there isn't any standard for such tags so it's pretty much useless.)

---

### Post by CatKiller on 2009-08-20
> **mcduck said:**
>  (although there are ways to attach tags to .wav files, there isn't any standard for such tags so it's pretty much useless.)

I did this by mistake once. I had been using Audacity for some WAV file editing fun, and exporting to FLAC, so I'd put tags in. Then I needed to export them as WAVs for someone else, and Audacity continued to try to put the tags in the headers of the resulting files (without a warning to that effect). Everything that managed to play the resulting files interpreted the corrupted headers as audio. Sounded horrible.

---

