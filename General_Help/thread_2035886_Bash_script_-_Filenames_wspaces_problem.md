---
title: "Bash script - Filenames w/spaces problem"
date: 2012-07-31
forum: General Help
---

### Post by SushiAddiction on 2012-07-31
Can someone please help me with a bash script
I'm having problems with spaces in filenames. I'm trying to keep the script as simple as possible. It's for encoding and entire directory with handbrake. Output/Input is a set directory.

```
for file in `ls /home/sushi/Videos/0encode/input/`; do $(HandBrakeCLI -v -i /home/sushi/Videos/0encode/input/"$file" -f mkv -o /home/sushi/Videos/0encode/output/"${file}.mkv" -q 26 -e x264 --x264-preset veryslow --x264-tune animation --x264-profile high -m -E vorbis -B 48 -l 480 -s 1,2,3,4,5,6,7,8,9 --subtitle-default -a 1); done
``` 

I've tried using
```
OIFS="$IFS"
IFS=$'\n'
for file in `ls /home/sushi/Videos/0encode/input/`; do $(HandBrakeCLI -v -i /home/sushi/Videos/0encode/input/"$file" -f mkv -o /home/sushi/Videos/0encode/output/"${file}.mkv" -q 26 -e x264 --x264-preset veryslow --x264-tune animation --x264-profile high -m -E vorbis -B 48 -l 480 -s 1,2,3,4,5,6,7,8,9 --subtitle-default -a 1); done
IFS="$OIFS"
```
but in put out hundreds of lines of progress information when done.

---

### Post by dodo3773 on 2012-07-31
Does this work?:
```

for file in /home/sushi/Videos/0encode/input/*; do HandBrakeCLI -v -i "$file" -f mkv -o /home/sushi/Videos/0encode/output/"${f%}.mkv" -q 26 -e x264 --x264-preset veryslow --x264-tune animation --x264-profile high -m -E vorbis -B 48 -l 480 -s 1,2,3,4,5,6,7,8,9 --subtitle-default -a 1; done

```

---

### Post by Zvlwab on 2012-07-31
I think this should work:
```
for file in  /home/sushi/Videos/0encode/input/*; do
$(HandBrakeCLI -v -i "$file" -f mkv -o "${file}.mkv" -q 26 -e x264 --x264-preset veryslow --x264-tune animation --x264-profile high -m -E vorbis -B 48 -l 480 -s 1,2,3,4,5,6,7,8,9 --subtitle-default -a 1);
done
```

---

### Post by nothingspecial on 2012-07-31
Hi,

See [[COLOR="Red"]bash pitfalls #1[/COLOR]]("http://mywiki.wooledge.org/BashPitfalls/#for_i_in_.24.28ls_.2A.mp3.29")

---

### Post by SushiAddiction on 2012-07-31
Thanks dodo3773 and Zvlwab. The problem is I need the outputs in a different directory.
I feel so stupid. I cant seem to get it working :/

---

### Post by dodo3773 on 2012-07-31
> **SushiAddiction said:**
> Thanks dodo3773 and Zvlwab. The problem is I need the outputs in a different directory.
I feel so stupid. I cant seem to get it working :/

What I posted does output to a different directory. Did you even try it? What was the output?

---

### Post by SushiAddiction on 2012-07-31
Ah yes sorry. There is no output. I have a feeling that
"${f%}.mkv"
is the problem

---

### Post by dodo3773 on 2012-07-31
> **SushiAddiction said:**
> Ah yes sorry. There is no output. I have a feeling that
"${f%}.mkv"
is the problem

No output? None at all? What is in the  "/home/sushi/Videos/0encode/input/" directory? Is it full of sub directories or something? Or are all the files that need to be converted right there?

---

### Post by SushiAddiction on 2012-07-31
No files in the output directory. (failed to write. The encoding work was done but no files.)
No sub directories.
All the files for encoding are in the input directory. My first script on this thread converts all the files but creates a dump of the progress at the end of the encode instead of show % progress during then encode. 
This is driving me nuts. I know I'm missing something.

---

### Post by evilsoup on 2012-07-31
Try this variation of dodo3773, without the $() and with a slight change to the output syntax.

```
for file in  /home/sushi/Videos/0encode/input/*; do HandBrakeCLI -v -i "$file" -f mkv -o "$file".mkv -q 26 -e x264 --x264-preset veryslow --x264-tune animation --x264-profile high -m -E vorbis -B 48 -l 480 -s 1,2,3,4,5,6,7,8,9 --subtitle-default -a 1; done
```

---

### Post by SushiAddiction on 2012-07-31
Hey evilsoup. That works... thanks..... but does not put the encoded files in a different directory. Things will get very messy.

---

### Post by evilsoup on 2012-07-31
D'oh! That's because I forgot to put the /path/to/the/directory in the output. This should do it:

```
for file in  /home/sushi/Videos/0encode/input/*; do HandBrakeCLI -v -i "$file" -f mkv -o /home/sushi/Videos/0encode/output/"$file".mkv -q 26 -e x264 --x264-preset veryslow --x264-tune animation --x264-profile high -m -E vorbis -B 48 -l 480 -s 1,2,3,4,5,6,7,8,9 --subtitle-default -a 1; done 
```

---

### Post by SushiAddiction on 2012-07-31
With that command, handbrake is trying to write to
```
/home/sushi/Videos/0encode/output//home/sushi/Videos/0encode/input/hard.times-spk-sample.avi.mkv
```and exits without encoding.

Probably because
```
for file in  /home/sushi/Videos/0encode/input/*
```

---

### Post by evilsoup on 2012-07-31
Ah.
Well, I think the best solution is to just cd to the input directory, then you can cut out the huge path.

---

### Post by Vaphell on 2012-07-31
you can extract the file name part with ${file##*/} - it strips the longest '<whatever>/' from the left side

```
$ file="/home/sushi/Videos/0encode/input/hard.times-spk-sample.avi"
$ echo "${file##*/}"
hard.times-spk-sample.avi
```

target would be
```
... -o /home/sushi/Videos/0encode/output/"${file##*/}".mkv ...
```

---

### Post by SushiAddiction on 2012-07-31
Thanks Vaphell Solved. You're a legend. 
One of the great mysteries solved and I'm sure I forget it by tomorrow morning.... after I get it tattooed somewhere on my body.

---

