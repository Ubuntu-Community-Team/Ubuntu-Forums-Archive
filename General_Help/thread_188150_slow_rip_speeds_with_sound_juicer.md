---
title: "slow rip speeds with sound juicer"
date: 2006-06-03
forum: General Help
---

### Post by lime4x4 on 2006-06-03
I've manualy edited my hdparm file to allow dma but it's still slow
it's a sony dru500 dvd/burner
/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/hdc {
   dma = on
   }

---

### Post by blackjack6.21.91 on 2006-06-03
Look in your sound juicer preferences and make sure your not decoding to FLAC or anything..

---

### Post by lime4x4 on 2006-06-03
ripping to mp3.. Most times the speed is around 4X sometimes it jumps to 6x for a few secs

---

### Post by MetalMusicAddict on 2006-06-03
Does Sound Juicer enable cdparanoia by default? See my sig for a Grip Mp3 guide. Feel free to ask questions.

---

### Post by meng on 2006-06-03
You're not ripping to some ridiculously high bitrate are you? Just checking. I would have thought 4x was not too bad, at until I recently got a new drive and managed to get 6x.

---

### Post by lime4x4 on 2006-06-03
192 bitrate on xp with the same drive i was ripping around 20x

---

