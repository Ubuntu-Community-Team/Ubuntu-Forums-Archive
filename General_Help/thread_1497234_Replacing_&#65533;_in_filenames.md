---
title: "Replacing &#65533; in filenames"
date: 2010-05-30
forum: General Help
---

### Post by schitthoch2 on 2010-05-30
I think files and folders names on my xfs partition could got corrupted when i copied them using rsync at the time.

The files and folders having a &#65533; in the name are not even shown i.e. in Thunar (i am using mythbuntu, xfce). The &#65533; used to be german umlauts or other special characters (norwegian, french, spanish).

As this affects my whole mp3 collection and the corrupt files are not shown in ANY player i really would like to fix the names.

How can i search for those files and replace the &#65533; with a special STRING so that a can manually change file/folder names afterwards so that string is replaced with the correct special character ?

Help greatly appreciated.

---

### Post by geirha on 2010-05-30
It would help to see the hex values of those odd characters. Could you pipe a filename through hd and paste it here?

```
printf %s *something* | hd
```
Where *something* is a glob that'll match at least one file with odd chars.

---

### Post by schitthoch2 on 2010-05-30
I am not sure if I correctly understood your instructions (what is a glob ?). I tried to do:

cd /MyMusicDirectory
printf %s corruptedFile.mp3 | hd

But i am not able to select corruptedFile.mp3 because the terminal does not recgnize it. Instead the terminal input line does weird things when using tab-completion ...

I do:
ll /media/daten/musik/2raumwohnung/Melancholi [tab]
and get:
ll /media/daten/musik/2raumwohnung/Melancholisch\ Sch&#9618;n/
try to go on:
ll /media/daten/musik/2raumwohnung/Melancholisch\ Sch&#9618;n/2Ra [tab]
Jumps back to:
ll /media/daten/musik/2raumwohnung/Melancholisch\ Sch

---

### Post by geirha on 2010-05-30
Well, assuming there's a «foo&#65533;bar.mp3», then try
```
printf %s foo* | hd
```

EDIT: ok, based on your edit, type this exactly:
```
printf %s /media/daten/musik/2raumwohnung/Melancholisch* | hd
```

---

### Post by schitthoch2 on 2010-05-30
Thank you for your patience:

printf %s /media/daten/musik/2raumwohnung/Melancholisch* | hd
00000000  2f 6d 65 64 69 61 2f 64  61 74 65 6e 2f 6d 75 73  |/media/daten/mus|
00000010  69 6b 2f 32 72 61 75 6d  77 6f 68 6e 75 6e 67 2f  |ik/2raumwohnung/|
00000020  4d 65 6c 61 6e 63 68 6f  6c 69 73 63 68 20 53 63  |Melancholisch Sc|
00000030  68 f6 6e                                          |h.n|
00000033

That is a folder, not a file !

---

### Post by geirha on 2010-05-30
Ok, the character in question has hex value F6, that is ö in latin1 and some other iso-8859-charsets. So we could try assuming the files are in latin1, and convert them to your current character encoding.

With something like this:
```
find /media/daten/musik/ -execdir bash -c \
  'f=$(iconv -f latin1 <<< "$1");
   if [[ "$f" != "$1" ]]; then 
     [color=red]echo[/color] mv -v "$1" "$f"; 
   fi' _ {} \;
```

That will go through all files and directories under /media/daten/musik and attempt to rename each file and directory from latin1. Notice the [color=red]echo[/color] marked in red, it will make it just output the mv-command instead of executing it, so it won't actually rename anything (yet). It should output lines like

```
mv -v ./Melancholisch Sc&#65533;n ./Melancholisch Scön
```

If it does that properly for all the files and dirs with odd chars. Remove the echo and it will do the actual renaming.

If you get some odd cases, post them here and we can try to adjust it a little bit.

---

### Post by schitthoch2 on 2010-05-30
TERRIFIC !!!

I uncommented echo after a few tests, and it seems to work, except in a few cases. 

Example: File Hirarchies

I have my collection in the following folder/file structure:
/media/daten/musik/ARTIST/ALBUM/CDxx/ARTIST - ALBUM - TRACKNO - TRACKTITLE.mp3

Note: CDxx only if there are multiple CDs per Album

So for the above example, your code worked for 
/media/daten/musik/ARTIST/ALBUM/ but no more down in an the directory tree

See:

/media/daten/musik/2raumwohnung/Melancholisch\ Sch**ö**n/2Raumwohnung\ -\ Melancholisch\ Sch
2Raumwohnung - Melancholisch Sch**&#9618;**n - 01 - Melancholisch Sch**&#9618;**n.mp3

I have uploaded the output of your script (echoing) [here]("http://www.file-upload.net/download-2559756/mp3DOfixingnames.sh.html").

---

### Post by schitthoch2 on 2010-05-30
Oh no ! I was too enthusiastic

I ran it two times, and that gave me strange characters again

---

### Post by geirha on 2010-05-30
Is that after you ran it without the echo? Because now it will treat the ones with multi-byte utf-8 characters as "bad" ones and convert it doubly, giving a bad result.

I should've been more clear that you shouldn't run it if the output showed "bad" cases. And it should not be run more than once for the same reason.

I was initially under the impression that all files under that dir where "badly" named..?

Does this show any files or directories:
```
find . -regextype posix-basic ! -regex "[[:print:]]*"
```
(should possibly have used that from the start, but I didn't think of it at the time)

---

### Post by geirha on 2010-05-30
Ok, you ran it twice, that complicates things quite alot. We'll have to reverse the conversion done the second time, but that may worsen the files that were bad initially.

Try:
```
find /media/daten/musik/ -regextype posix-basic ! -regex "[[:print:]]*" -execdir bash -c \
  'f=$(iconv -t latin1 <<< "$1");
   if [[ "$f" != "$1" ]]; then 
     echo mv -v "$1" "$f"; 
   fi' _ {} \;

```

Does that appear to reverse it?

---

### Post by schitthoch2 on 2010-05-30
Well don't appologise, I appreciate your help and as I said before I was too enthusiastic ...

First a diagnose of your latest proposal, then a possible solution approach by me.

With:
```

find /media/daten/musik/ -regextype posix-basic ! -regex "[[:print:]]*" -execdir bash -c \
  'f=$(iconv -t latin1 <<< "$1");
   if [[ "$f" != "$1" ]]; then 
     echo mv -v "$1" "$f"; 
   fi' _ {} \;

```
I get for all files:
iconv: illegal input sequence at position xyz
xyz may vary but seems to be the position of the "wrong" character

> 
We'll have to reverse the conversion done the second time, but that may worsen the files that were bad initially.

I could first try to rename the files with EasyTAG using the ID3 tags which seem to be correct and since the first run of your initial code i can now access the folders/files with most applications. We could then look for remaining problems.

---

### Post by geirha on 2010-05-30
> **schitthoch2 said:**
> First a diagnose of your latest proposal, then a possible solution approach by me.

I get for all files:
iconv: illegal input sequence at position xyz
xyz may vary but seems to be the position of the "wrong" character


Hm, I checked more closely, and checking for non-printable characters is not the right thing to do. UTF-8, treated as latin1 and converted to UTF-8 does not generate unprintable chars, but rather things like Ã¶ (iconv -f latin1 <<< 'ö'), so
```

find /media/daten/musik/ -name "*Ã*" -execdir bash -c \
  'f=$(iconv -t latin1 <<< "$1");
   if [[ "$f" != "$1" ]]; then 
     echo mv -v "$1" "$f"; 
   fi' _ {} \;

```
Should hopefully be more useful, though it'll probably not catch all cases.

> **schitthoch2 said:**
> 
I could first try to rename the files with EasyTAG using the ID3 tags which seem to be correct and since the first run of your initial code i can now access the folders/files with most applications. We could then look for remaining problems.

Agreed, if all (or at least most) of the files have proper tags, then that would indeed be the easiest way to fix it.

---

### Post by schitthoch2 on 2010-06-01
Ok, I tried using EasyTAG but that was not really stable to run a rename on the whole (big) music collection. 

But I managed to use Mp3tag from Windows over Samba to rename the whole collection (files).

For the folder names, I had to manually rename the corrupted ones, but that was only 1 hour of work.

In the end I would still thank you very much, as you made me access the files and folders again. I finally have a fully working mp3 collection again.

And believe me this is quite important to me.

KUDOS go to geirha

[SOLVED]

---

