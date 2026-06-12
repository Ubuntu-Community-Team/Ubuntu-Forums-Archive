---
title: "gnome-search-tool"
date: 2010-07-26
forum: General Help
---

### Post by SagnaB on 2010-07-26
Hi all,

I have a predicament with an external USB HDD that I use in my car as my player has USB support, albeit limited. As you may have guessed my music collection is contained within - all being .mp3 files but there also seems to be .jpg, .txt, .m3u, and a few other **unsupported** files scattered around the place in various directories.

Rather than going through and manually finding and deleting these rouge files, is there a way to use gnome-search-tool (or any other search tool) to **search for all files except .mp3 files**?

I was thinking of something like this:

```

! *.mp3

```!Cheers
[SIZE=1]Pun intended[/SIZE]

---

### Post by prodigy_ on 2010-07-26
If you're not against terminal, then there's a way. For example, if your USB stick is mounted as **/media/USB**, then the following command will **theoretically** list all non-MP3 files: 

```
find /media/USB -type f -print0|xargs -0 file|grep -v 'Audio file .* MPEG .* layer III'|cut -d: -f1
```

If none of those files has whitespaces in its name, you can just slap **|xargs rm** at the end of the previous command to auto-remove. If there are names with whitespaces, it'll be trickier.

---

### Post by SagnaB on 2010-07-26
Prodigy_,
Not that I don't trust you personally, I'm probably just over cautious; but can someone else verify that this command will work and/or is not harmful?
I am fairly comfortable using terminal, so long as I'm not entering random commands lol
My terminal experience is limited, but growing day by day :)

---

### Post by prodigy_ on 2010-07-26
Hehe. I myself never run things I don't understand either. :-)

---

Well, so far I tested this with one MP3 file and it worked. Presumable there should be no problems, but if there are files with whitespaces or colons in their names, some amendments will be needed. Anyway using the command I suggested (without the extra **|xargs rm** part) is safe because it only lists the names of files, nothing else.

---

### Post by hakermania on 2010-07-26
I dont know the command prodigy_ gave you but you can check it by making a temporary folder let's say 'Test', put some mp3s and non-mp3s files in there and change the /media/USB/ path to this folder (e.g. /home/SangaB/Test/) By this way you'll test what this command does.[URL="http://ubuntuforums.org/member.php?u=518500"]
[/URL]

---

### Post by thebigob on 2010-07-26
cd into the disk ie:

```

cd /media/myDisk

```

I would use the command:

```

find ./ -type f  | grep -iv mp3 

```

This will show all files from the current directory down without mp3 in the file name ignoring case.

if you are happy with the output of this command then you can run:

```

find ./ -type f  | grep -iv mp3 | xargs rm

```

This will remove the files as seen in the output of the previous command

---

### Post by prodigy_ on 2010-07-26
Ok, this should handle any special characters except newline. (Although newlines in filenames are permitted in Linux, it's really hard to handle them because not everything supports ASCII NUL character as a delimiter.) ```
find /media/USB -type f -print0|xargs -0 file -F '/' \
        |grep -v 'Audio file .* MPEG .* layer III'|rev \
        |cut -d '/' -f 2-|rev|tr '\012' '\000'|xargs -0 rm
```

Of course you'll need to replace **/media/USB** with the actual mount point.

---

### Post by SagnaB on 2010-07-26
Oh wow! I didn't expect this much assistance, but then again, we're talking about the Ubuntu Community here :p

I ended up cd-ing into mount point and:
```
find ./ -type f  | grep -iv mp3 | xargs rm
``` only 'cause it seemed simpler and it **worked a treat!**
No more jpg (nor jpeg), txt, m3u, wav, nfo, ini, aac or url files hooray!
Hopefully the drive works in my car now.

If you're curious,[ _here's a Link_]("http://www.kenwood.com/usb/compatibility/m.html") to the specification page of my actual head unit player in my car; you can see the ridiculous compatibility.

Thanks heaps Prod* and thebigob

---

### Post by prodigy_ on 2010-07-26
You're welcome. :-)

---

