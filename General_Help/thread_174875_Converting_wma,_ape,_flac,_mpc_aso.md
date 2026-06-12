---
title: "Converting wma, ape, flac, mpc aso"
date: 2006-05-12
forum: General Help
---

### Post by GabrielWolff on 2006-05-12
I'm trying to convert different sound files to mp3 to be able to listen to it in my mp3 player that doesn't play anything but mp3s.

In SoundConverter, only ogg and flac converts to mp3. Other files *seem* to be converted but there is no output.

Using the script audio-convert most of the time does nothing. It asks me some questions, and then strikes

Any other ideas?

G

---

### Post by dschaller on 2006-05-12
There are probably more elegant ways, but using mplayer and lame you can convert most anything to mp3. Have mplayer "play" the file to wav and then use lame to create the mp3 from the wav.

mplayer <infile> -ao pcm:file=<outfile>
lame [options] <infile> <outfile>

---

### Post by GabrielWolff on 2006-05-13
[QUOTE=dschaller]There are probably more elegant ways, but using mplayer and lame you can convert most anything to mp3. Have mplayer "play" the file to wav and then use lame to create the mp3 from the wav.

mplayer <infile> -ao pcm:file=<outfile>
lame [options] <infile> <outfile>[/QUOTE]

1) MPlayer won't play neither the ape files nor the mpc files. wma files will be played (but are recognized by Nautilus as ASF video's - what the heck?)

2) Don't I loose sound quality this way? Like: I do anyway while converting, but isn't that kinda like plugging in a analog cable and recording it on the other side?

Thanks

Gabriel

---

### Post by dschaller on 2006-05-13
1) I'm not too sure about the trouble here. I'd have to do a little more digging online. It should play Monkey's Audio (.ape) files. I'm not sure about mpc. I think that used to be a closed-source format and it's possible that no free player will support it, but I don't know.

2) You will not lose quality by "playing" it to wav. wav is a lossless audio format. You will get a copy of the same data that would have been sent to your sound card. You will, however, lose quality when you convert that wav to mp3, but this is always the case. mp3 is a "lossy" audio format. It compresses the sound file by throwing away frequencies you can't usually hear. So yes, you will always lose quality when you're converting to mp3 no matter what software you use. If encoding with lame, you can set a "quality" level for encoding your mp3. The higher the quality setting, the less noticable the loss will be.

---

### Post by GabrielWolff on 2006-05-14
[QUOTE=dschaller]1) I'm not too sure about the trouble here. I'd have to do a little more digging online. It should play Monkey's Audio (.ape) files. I'm not sure about mpc. I think that used to be a closed-source format and it's possible that no free player will support it, but I don't know.[/QUOTE]

But you say that if MPlayer manages to play a file I could use your way to convert it?
So the only thing I'd have to do is to find the right codec/plugin?

G

---

### Post by dschaller on 2006-05-24
[QUOTE=GabrielWolff]But you say that if MPlayer manages to play a file I could use your way to convert it?
So the only thing I'd have to do is to find the right codec/plugin?
[/QUOTE]

That's right. If you can play it, you can get it to wav. And once it's in wav, you can do anything with it.

---

### Post by KnottyMan on 2006-05-24
Rather than write it out to a wav file everytime, just pipe it to lame...

mplayer [options] file | lame [options] - file.mp3

Notice the dash.  "-" is StandardIn.

That plus a for loop saved me many a hassle when transcoding a bunch of flacs.

for i in *.flac ; do mplayer "$i" | lame -b 160 - "`echo $i | sed 's/flac/mp3/'`" ; done

Check the output, then rm *.flac.

But yes, mplayer will need the proper codec to work.

---

### Post by GabrielWolff on 2006-05-25
OK, thanks for all that, guys, it's surely gonna be very helpfull* once I manage to play these darn files*!!

Both mpc and ape just say "sorry, we're not playable" in MPlayer. 
mpc says: "No stream found". 
ape says: "failed to open /home/gabriel/<"

How come? And how do I fix that?

Gabriel

---

### Post by fubarbundy on 2006-06-06
[QUOTE=GabrielWolff]1) MPlayer won't play neither the ape files nor the mpc files. wma files will be played (but are recognized by Nautilus as ASF video's - what the heck?)

2) Don't I loose sound quality this way? Like: I do anyway while converting, but isn't that kinda like plugging in a analog cable and recording it on the other side?

Thanks

Gabriel[/QUOTE]

wma files ARE asf! Anything with the extension .wma is actually wma-encoded audio wrapped in an asf container. Kind of like .ogg files are vorbis, theora or something else wrapped in an ogg container. Useless information is my speciality.

And in case you haven't already found it, debs for ape playback can be found in the link on this post: 
[http://www.ubuntuforums.org/showthread.php?t=189418#8](http://www.ubuntuforums.org/showthread.php?t=189418#8)

---

### Post by Bseater on 2006-06-08
Is there a way do have that if statement go through a directory tree, so I can just run it once in the top dir that all my music is in?

---

