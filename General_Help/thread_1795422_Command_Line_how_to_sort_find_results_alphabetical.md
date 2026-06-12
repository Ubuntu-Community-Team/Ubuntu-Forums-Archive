---
title: "Command Line: how to sort find results alphabetically?"
date: 2011-07-02
forum: General Help
---

### Post by UranUtan on 2011-07-02
Hi,

I would like to re-encode media files to mp3 64 Kbps bitrate using ffmpeg. The work need to be done for an entire folder so I would like to generate the syntax automatically. Example the folder has the following content:

01 - MyTrack.mp3
02 - MyTrack.mp3
03 - MyTrack.mp3
etc.

The syntax to convert 1 file is:

ffmpeg -i "01 - MyTrack.mp3" -acodec libmp3lame -ab 64k "BR64K/01 - MyTrack.mp3"


To generate the syntax for the entire folder, I use this command:

**find . -iname "*.mp3" -printf "ffmpeg -i \"%f\" -acodec libmp3lame -ab 64k \"BR64K/%f\"\n" > ReencodeBitrate.sh**

The result is OK and the ReencodeBitrate.sh works as expected. However, I would like to make the script more readable by having the lines which are displayed in the script sorted alphabetically. Because currently it looks like there are no apparent order.

**Question**: is there a way to sort the find output? And better yet, can you apply it to improve the command line above? Or may be there is a an even more elegant solution using another command than find?

Thanks in advance for any help.

---

### Post by AlphaLexman on 2011-07-02
Not tested...
```
for f in "*.mp3"; do ffmpeg -i "$f" -acodec libmp3lame -ab 64k "BR64K/$f"; done

```

---

### Post by UranUtan on 2011-07-02
> **AlphaLexman said:**
> Not tested...
```
for f in "*.mp3"; do ffmpeg -i "$f" -acodec libmp3lame -ab 64k "BR64K/$f"; done
```

Thanks for suggesting an alternative solution. I keep this on file to put it in use next time. However, I am still interested in a solution that generate a script.

---

### Post by AlphaLexman on 2011-07-02
You could try:
```
find . -iname "*.mp3" | sort
```
but unfortunately you lose the functionality of **-printf**
Maybe some redirection could offer a solution?

---

### Post by gmargo on 2011-07-02
> **UranUtan said:**
> 
**find . -iname "*.mp3" -printf "ffmpeg -i \"%f\" -acodec libmp3lame -ab 64k \"BR64K/%f\"\n" > ReencodeBitrate.sh**
is there a way to sort the find output?

Is there some reason not to use the most obvious solution?

[FONT=Courier New]find . -iname "*.mp3" -printf "ffmpeg -i \"%f\" -acodec libmp3lame -ab 64k \"BR64K/%f\"\n"  **[COLOR=Red]| sort[/COLOR]**  > ReencodeBitrate.sh[/FONT]

---

### Post by UranUtan on 2011-07-03
> **gmargo said:**
> Is there some reason not to use the most obvious solution?

[FONT=Courier New]find . -iname "*.mp3" -printf "ffmpeg -i \"%f\" -acodec libmp3lame -ab 64k \"BR64K/%f\"\n"  **[COLOR=Red]| sort[/COLOR]**  > ReencodeBitrate.sh[/FONT]

Oh wow! super nice, exactly what I was looking for. The reason? My ignorance in the command line intricacies. Thanks very much for your help.

---

