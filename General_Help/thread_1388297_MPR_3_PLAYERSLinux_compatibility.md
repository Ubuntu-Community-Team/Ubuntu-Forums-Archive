---
title: "MPR 3 PLAYERS/Linux compatibility"
date: 2010-01-22
forum: General Help
---

### Post by SISU1375 on 2010-01-22
[FONT=Georgia][SIZE=4]I  [/SIZE][/FONT][SIZE=4]have just purchased an F427-5CCFO MP3 player.  I believe it's a generic Chinese knock off player that advertises as being Linux compatible.  The audio files moved over from my Ubuntu 9.4 do not play back, even though they are copied onto the player[/SIZE].    [SIZE=4][FONT=Georgia]Is there a way to get Linux audio files to play on this?[/FONT][/SIZE]

[SIZE=4][FONT=Georgia]This player was touted in the Linux[/FONT][/SIZE]  [SIZE=4][FONT=Georgia]Journal as being Linux compatible.  Is there a quality MP3 player out there that is easily adaptable for UBuntu?  :confused:[/FONT][/SIZE]

---

### Post by Stigmata13 on 2010-01-22
Edit: Nvm, read the question wrong lol.

---

### Post by stinkeye on 2010-01-23
When it says that the mp3 player is linux compatible it may just mean that it's a file-system based player.
ie. you can drag and drop your music files into the player.
It will play mp3 files but may not support ogg files.
Some of the sansa line of players are file-system based and support MP3, WMA, secure WMA, Audible, Ogg Vorbis, and FLAC music files.
I use the [_**[COLOR="DarkRed"] Sansa Clip+[/COLOR]**_]("http://www.themp3outletstore.com.au/catalog/product_info.php/cPath/67/products_id/443") and it works well with gpodder.
gpodder will also convert ogg files if your player doesn't support ogg.
SoundConverter will also convert sound files.
```
sudo apt-get install soundconverter
```

---

