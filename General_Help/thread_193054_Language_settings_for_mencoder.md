---
title: "Language settings for mencoder"
date: 2006-06-09
forum: General Help
---

### Post by mathiasv on 2006-06-09
Hi am having some problems with dvd-ripping and mencoder

I have ripped two dvd's with dvdrip 0.52.5, and all works fine but all the files for one movie takes up approx. 4 GB. So I have tried to compress the movies by re-encoding with mencoder. Each .avi-file takes up around 20% space of the original .vob-file after compression.

My problem is that after mencoder dvdmovie-1 only has Spanish soundtrack and dvdmovie-2 only has German :confused: , where the originals both have english as original language and several other audio channels available. I have tried the following:

Spanish/German audio:```

mencoder dvdmovie.vob -ovc lavc -oac lavc -lavcopts aspect=16/9 -ffourcc DX50 -o dvdmovie.avi
mencoder dvdmovie.vob -ovc lavc -oac lavc -lavcopts aspect=16/9 -alang en -ffourcc DX50 -o dvdmovie.avi

mencoder dvdmovie.vob -ovc lavc -oac mp3lame -lavcopts aspect=16/9 -ffourcc DX50 -o dvdmovie.avi
mencoder dvdmovie.vob -ovc lavc -oac mp3lame -lavcopts aspect=16/9 -alang en -ffourcc DX50 -o alang.avi

mencoder dvdmovie.vob -oac mp3lame -ovc xvid -xvidencopts aspect=16/9:bitrate=678 -ffourcc DX50 -o dvdmovie.avi
mencoder dvdmovie.vob -oac mp3lame -ovc xvid -xvidencopts aspect=16/9:bitrate=678 -alang en -ffourcc DX50 -o dvdmovie.avi
```

No sound or Spanish/German (depending on -aid number):
```
mencoder dvdmovie.vob -ovc lavc -oac lavc -lavcopts aspect=16/9 -aid 1 -ffourcc DX50 -o dvdmovie.avi
mencoder dvdmovie.vob -ovc lavc -oac mp3lame -lavcopts aspect=16/9 -aid 1 -ffourcc DX50 -o dvdmovie.avi
mencoder dvdmovie.vob -ovc xvid -oac mp3lame  -xvidencopts aspect=16/9:bitrate=678 -aid 1 -ffourcc DX50 -o dvdmovie.avi

```
If I try to open one of the .vob-files with dvdrip, my machine freezes. 

Thanks for any advice on the encoding.

Mathias

---

### Post by mathiasv on 2006-07-27
Myself again. In case anyone else reads this, you select the rigth language like this.

You find the language tracks available in the prompt output from:
```
mplayer -v dvdmovie.vob
```

Listen to languages one at a time (here "128"):
```
mplayer -v -aid 128 dvdmovie.vob
```

Specify wanted -aid when running mencoder.

Happy mencoding.
Mv.

---

