---
title: "Music players, shuffle, and classical music."
date: 2011-05-26
forum: General Help
---

### Post by 8jwong14 on 2011-05-26
As a fan of classical music, I listen to classical pieces in whole parts.  However, one annoyance is that I shuffle my music when playing them in Banshee.  The various parts of classical pieces aren't in order and they are mixed up.  Is there any music player for Ubuntu that allows for a grouping function where a person can select to group classical pieces together so even if the library is shuffled, the parts of the piece are still in proper order?

---

### Post by wildmanne39 on 2011-05-27
> **8jwong14 said:**
> As a fan of classical music, I listen to classical pieces in whole parts.  However, one annoyance is that I shuffle my music when playing them in Banshee.  The various parts of classical pieces aren't in order and they are mixed up.  Is there any music player for Ubuntu that allows for a grouping function where a person can select to group classical pieces together so even if the library is shuffled, the parts of the piece are still in proper order?
Hi, I use rythmbox and it plays in alphabetical order, it has a button to play random, so you might could put your music in a certain order not for sure though.

---

### Post by linuxinstalledfromhdd on 2011-05-27
I'm a big fan of Clementine myself.. You can try it out over here:

[http://cinderbox.net/2011/04/18/clementine-steadily-improving-ppa-for-ubuntu-maverick-natty-updated/](http://cinderbox.net/2011/04/18/clementine-steadily-improving-ppa-for-ubuntu-maverick-natty-updated/)

---

### Post by coffeecat on 2011-05-27
> **8jwong14 said:**
> As a fan of classical music, I listen to classical pieces in whole parts.  However, one annoyance is that I shuffle my music when playing them in Banshee.  The various parts of classical pieces aren't in order and they are mixed up.  Is there any music player for Ubuntu that allows for a grouping function where a person can select to group classical pieces together so even if the library is shuffled, the parts of the piece are still in proper order?

Hi. If I understand you correctly, you've switched shuffle on in Banshee, but you don't want your classical pieces shuffled. I agree - playing Beethoven's Ninth in the order 2,1,3,5,4 would be... weird.

I don't know of a music player that will do this, but I do have a suggestion. You could concatenate (join together) the separate movement mp3s of a classical work into one long mp3. You could use the terminal cat command for this, but the problem is that the header metadata for each of the original mp3s (except for the first) is then inside the stream and some music players stumble over this - some simply stopping when they get to the first join.

To get over this, you can use mp3wrap, but this introduces two problems of its own. It spams its own id3 tags into the metadata and it does not correct the duration field. Again, some music players simply stop when they get to the time of the duration field, which is the end of the first movement/track.

Here are a couple of links, neither of which is the complete solution:

[http://lyncd.com/2009/02/how-to-merge-mp3-files/](http://lyncd.com/2009/02/how-to-merge-mp3-files/)

[http://lyncd.com/2011/03/lossless-combine-mp3s/](http://lyncd.com/2011/03/lossless-combine-mp3s/)

Or rather, the second has an error.

If I remember correctly, what I did was:

1 - use mp3wrap to concatenate the mp3 files.

2 - use id3cp to copy the id3 tags from the first track to the large mp3 file. (Install libid3-tools to get id3cp.)

3 - use Easytag to edit the id3 metadata in the large file - optional, if you want individual fields different.

4 - use vbrfix to re-sync the vbr header. In Ubuntu, the package is vbrfix, not vbrfixc, and the option '--XingFrameCrcProtectIfCan' is meaningless, at least in Ubuntu. I don't know whether that's an option in the Mac version that the author of that link used, or an attempt at a joke.

I've assumed that your music files are mp3s. If you are using flac or ogg files, you could try concatenating the individual tracks but what problems you may or may not get with metadata, I don't know.

---

### Post by nothingspecial on 2011-05-27
If you create a playlist file in each album then something like

```
for p in $(find ~/Music -type f -name '*.pls' | sort -R); do mplayer -playlist "$p"; done
```

Should play a random album but with the tracks in order.

You can automate the playlist generation with fapg, but I've never used it so am unsure of the exact syntax.

---

### Post by 8jwong14 on 2011-05-28
> **coffeecat said:**
> Hi. If I understand you correctly, you've switched shuffle on in Banshee, but you don't want your classical pieces shuffled. I agree - playing Beethoven's Ninth in the order 2,1,3,5,4 would be... weird.

I don't know of a music player that will do this, but I do have a suggestion. You could concatenate (join together) the separate movement mp3s of a classical work into one long mp3. You could use the terminal cat command for this, but the problem is that the header metadata for each of the original mp3s (except for the first) is then inside the stream and some music players stumble over this - some simply stopping when they get to the first join.

To get over this, you can use mp3wrap, but this introduces two problems of its own. It spams its own id3 tags into the metadata and it does not correct the duration field. Again, some music players simply stop when they get to the time of the duration field, which is the end of the first movement/track.

Here are a couple of links, neither of which is the complete solution:

[http://lyncd.com/2009/02/how-to-merge-mp3-files/](http://lyncd.com/2009/02/how-to-merge-mp3-files/)

[http://lyncd.com/2011/03/lossless-combine-mp3s/](http://lyncd.com/2011/03/lossless-combine-mp3s/)

Or rather, the second has an error.

If I remember correctly, what I did was:

1 - use mp3wrap to concatenate the mp3 files.

2 - use id3cp to copy the id3 tags from the first track to the large mp3 file. (Install libid3-tools to get id3cp.)

3 - use Easytag to edit the id3 metadata in the large file - optional, if you want individual fields different.

4 - use vbrfix to re-sync the vbr header. In Ubuntu, the package is vbrfix, not vbrfixc, and the option '--XingFrameCrcProtectIfCan' is meaningless, at least in Ubuntu. I don't know whether that's an option in the Mac version that the author of that link used, or an attempt at a joke.

I've assumed that your music files are mp3s. If you are using flac or ogg files, you could try concatenating the individual tracks but what problems you may or may not get with metadata, I don't know.

Thanks for the suggestion.  Its great in that it will work on my cellphone too!

---

### Post by 8jwong14 on 2011-05-28
> **wildmanne39 said:**
> Hi, I use rythmbox and it plays in alphabetical order, it has a button to play random, so you might could put your music in a certain order not for sure though.
I'm usign Banshee and I would prefer for me to be able to keep using it.

---

### Post by abre on 2011-06-01
hi, i like banshee too, but if i start the computer for the first time and then open banshee player and play one of the song, it wont to play it. if i choose other songs, it wont play too. the banshee player can play the songs if I :
- open the folder from home folder and choose the folder where i placed all of my flacs file, choose one of it and play it
- or i open another music player just like vlc, play some songs with it, and after that banshee can play the songs again

someone can help me?

---

