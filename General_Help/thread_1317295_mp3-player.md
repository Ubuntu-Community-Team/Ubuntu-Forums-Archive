---
title: "mp3-player"
date: 2009-11-06
forum: General Help
---

### Post by koenfloris on 2009-11-06
hi, i got an philips gogear. it does mount almost correctly.

just one smal thing ,by default, ubuntu sees it as an external harddrive. 
how do i manually configure ubuntu to see it as an generic-mp3-player?

if i just drop mp3-files on it it works, so how can i do that without nautilus, but with banshee?

it is just i got a lot of junk-files between my music, and it is a pain to remove the junk everytime i copy some music-files to my mp3-player.

---

### Post by dragonboss on 2009-11-06
Have you tried Rythmbox or Amarok? They both feature mp3 player support.

---

### Post by koenfloris on 2009-11-06
rhythmbox does not detect it.

i think the whole system sees it as an external disk.

what should i do?

edit1
btw: i use ubuntu 9.10

---

### Post by sgosnell on 2009-11-06
Try creating an empty file named .is_audio_player and copying it to the root directory of the player.  Note the "." at the start, which makes it a hidden file.  You'll need to press Ctrl-H in nautilus to see these files.  Once that file is there, both Banshee and Rhythmbox should see it as a player.

---

### Post by koenfloris on 2009-11-07
> **sgosnell said:**
> Try creating an empty file named .is_audio_player and copying it to the root directory of the player.  Note the "." at the start, which makes it a hidden file.  You'll need to press Ctrl-H in nautilus to see these files.  Once that file is there, both Banshee and Rhythmbox should see it as a player.
@sgosnell

Thanks dude, that did the trick.

I did ask the question on launchpad to, but they never seemed to understand my problem correctly.

anyway, i was looking for ages for this, where did you find that information?

---

### Post by koenfloris on 2009-11-07
to early said thx.

now i get this when i this

using banshee

"error: Object reference not set to an instance of an object"

rhythmbox does the job fine. but i like banshee more, any suggestions?

---

### Post by sgosnell on 2009-11-07
I found the fix I posted with about 2 minutes on Google.  It's also here in the forums.

I don't use Banshee, so I don't have any suggestions for that, but Google might be of help.

---

### Post by koenfloris on 2009-11-08
i needed to put the lines
"
audio_folders=MyMusic/
folder_depth=2
output_formats=audio/mpeg,audio/mp3,audio/x-aac
"

in the .is_audio_player file. now it works fine.

---

