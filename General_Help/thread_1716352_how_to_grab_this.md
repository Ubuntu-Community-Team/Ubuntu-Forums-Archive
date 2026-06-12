---
title: "how to grab this?"
date: 2011-03-28
forum: General Help
---

### Post by vivek.pandey on 2011-03-28
hi everyone
    i am undergoing an online certification course in which they provide me kinda audio cum textual material. i guess its flash tutorial in which a slide like something appears on which a txt is written and then a woman tries to explain it. this course is 6 months after which i wont be able to access it but i want to anyhow grab it for future use. when i right click and save the page i just get an empty page the slide is not there also its not a powerpoint/presentation slide. anybody knows how can i do that
thanx in advace

---

### Post by vivek.pandey on 2011-03-29
no body can answer this?

---

### Post by ~Plue on 2011-03-29
this is just a random idea;
try using downloadhelper or flashgot to download the flash files (if it is flash)

---

### Post by TeoBigusGeekus on 2011-03-29
Can you give us a link to the page?

---

### Post by vivek.pandey on 2011-03-29
> **TeoBigusGeekus said:**
> Can you give us a link to the page?

to go to that tutorial i need to login the account given to me by them.. it requires username password...i can tell you via  a private message but if you assure me you wont be misusing me,,,please dont misunderstand me but i guess even you would do the same if asked for something which uses password...but thanx for your willingness to help

---

### Post by TeoBigusGeekus on 2011-03-29
No, DON'T do that!!! Don't trust anyone in the internet.

The only thing I can suggest is to read my posts in [this]("http://ubuntuforums.org/showthread.php?t=1688948") thread and try to grab the flash file.

The question is, how are you going to play an interactive flash animation afterwards?

---

### Post by Dimarchi on 2011-03-29
In terms of user friendliness, ~Plue's suggestion is the route to go...personally, my Firefox installation has the flashgot add-on for saving those flash files I want to watch without going to the site/page in question (such a hassle :)). You start viewing the flash file, a movie file kind of icon (which by default should be in the right side of status bar) starts pulsing for a while, indicating that the add-on has detected content it can save...click or right-click the icon to save the file.

TeoBigusGeekus' approach works, too, mind you - I haven't tested it apart from reading the thread linked by Teo.

---

### Post by TeoBigusGeekus on 2011-03-29
Found it: that was a bitch to crack!!!!!!!!!

lsof gave nothing; neither in Opera nor in Chromium - the solution was in the cache folder of Opera.

**_SOLUTION:_**

_Part 1 (easy):_
The slide can be saved with a simple printscreen... and that's it.

_Part 2 (the bitchy one):_
Log in the site but don't select a video yet.
Go to your home folder, .opera/cache folder. Delete everything in it.
Now select a video and let it play till it finishes.
In your opera cache folder, you will see that a couple of folders have been created: open them and search for shockwave files.
In the attached image, the file opr00G1K.tmp is a shockwave file (so is opr00G1J.tmp but it's too small to hold the audio we're after).
Copy and paste this file somewhere safe (your desktop for example).
The file as it is, is not playable because it's a compressed SWF file.
So, install flasm
```
sudo apt-get install flasm
```
(it must be in the ubuntu repositories)
and decompress the file
```
flasm -x ~/Desktop/opr00G1K.tmp
```
Ignore the extra temporary file that's created (opr00G1K.$wf) - delete it.
The last thing you have to do is convert your decompressed .swf file to an mp3 and you're done.
```
ffmpeg -i ~/Desktop/opr00G1K.tmp -acodec libmp3lame ~/Desktop/lesson1.mp3
```

Now you have the slide and the accompanying audio.
Good luck!!!

PS: Thanks for trusting me with your loggin details, but don't ever do it again, under no circumstances.

---

### Post by vivek.pandey on 2011-03-30
> **TeoBigusGeekus said:**
> Found it: that was a bitch to crack!!!!!!!!!

lsof gave nothing; neither in Opera nor in Chromium - the solution was in the cache folder of Opera.

**_SOLUTION:_**

_Part 1 (easy):_
The slide can be saved with a simple printscreen... and that's it.

_Part 2 (the bitchy one):_
Log in the site but don't select a video yet.
Go to your home folder, .opera/cache folder. Delete everything in it.
Now select a video and let it play till it finishes.
In your opera cache folder, you will see that a couple of folders have been created: open them and search for shockwave files.
In the attached image, the file opr00G1K.tmp is a shockwave file (so is opr00G1J.tmp but it's too small to hold the audio we're after).
Copy and paste this file somewhere safe (your desktop for example).
The file as it is, is not playable because it's a compressed SWF file.
So, install flasm
```
sudo apt-get install flasm
```
(it must be in the ubuntu repositories)
and decompress the file
```
flasm -x ~/Desktop/opr00G1K.tmp
```
Ignore the extra temporary file that's created (opr00G1K.$wf) - delete it.
The last thing you have to do is convert your decompressed .swf file to an mp3 and you're done.
```
ffmpeg -i ~/Desktop/opr00G1K.tmp -acodec libmp3lame ~/Desktop/lesson1.mp3
```

Now you have the slide and the accompanying audio.
Good luck!!!

PS: Thanks for trusting me with your loggin details, but don't ever do it again, under no circumstances.


thanx for your help
here are certain points

!)  i dont just wanna the textual content of the slide so printscreen is not the thing i am looking for
2) i use chrome and right now my internet speed is not that great so i am avoiding any download which is not there in software center
sudo apt-get install opera too doesnt work
in my home folder i dont have .chrome neither .google-chrome

so how should i proceed next . please dont advice to use firefox i find it really slow on my laptop

thanx again

---

### Post by TeoBigusGeekus on 2011-03-30
In the case of Chrome, the files will be in
```
~/.cache/chrome/
```

---

### Post by vivek.pandey on 2011-03-31
> **TeoBigusGeekus said:**
> Found it: that was a bitch to crack!!!!!!!!!

lsof gave nothing; neither in Opera nor in Chromium - the solution was in the cache folder of Opera.

**_SOLUTION:_**

_Part 1 (easy):_
The slide can be saved with a simple printscreen... and that's it.

_Part 2 (the bitchy one):_
Log in the site but don't select a video yet.
Go to your home folder, .opera/cache folder. Delete everything in it.
Now select a video and let it play till it finishes.
In your opera cache folder, you will see that a couple of folders have been created: open them and search for shockwave files.
In the attached image, the file opr00G1K.tmp is a shockwave file (so is opr00G1J.tmp but it's too small to hold the audio we're after).
Copy and paste this file somewhere safe (your desktop for example).
The file as it is, is not playable because it's a compressed SWF file.
So, install flasm
```
sudo apt-get install flasm
```
(it must be in the ubuntu repositories)
and decompress the file
```
flasm -x ~/Desktop/opr00G1K.tmp
```
Ignore the extra temporary file that's created (opr00G1K.$wf) - delete it.
The last thing you have to do is convert your decompressed .swf file to an mp3 and you're done.
```
ffmpeg -i ~/Desktop/opr00G1K.tmp -acodec libmp3lame ~/Desktop/lesson1.mp3
```

Now you have the slide and the accompanying audio.
Good luck!!!

PS: Thanks for trusting me with your loggin details, but don't ever do it again, under no circumstances.
thanx a lot i got it all completely but i faced certain issues

1) while using
```
ffmpeg -i ~/Desktop/f_000066 -acodec libmp3lame ~/Desktop/lesson1.mp3
```
i got an error there is some problem with libmp3lame
last few lines of the error are
```
[swf @ 0x8dd1420]max_analyze_duration reached
[swf @ 0x8dd1420]Estimating duration from bitrate, this may be inaccurate
Input #0, swf, from '/home/vivek/Desktop/f_0000d4':
  Duration: 00:01:19.67, bitrate: 64 kb/s
    Stream #0.0: Audio: mp3, 22050 Hz, 2 channels, s16, 64 kb/s
Unknown encoder 'libmp3lame'

```
2) i just executed the first command and i got the decompressed file . i opened it with vlc and it worked fine.. i changed the name to .mp3 but then there was no audio . i then changed to .mp4 and it works fine but i just cant forward the audio and it goes with its own speed
but thanx a lot

---

### Post by TeoBigusGeekus on 2011-04-01
See [this]("http://ubuntuforums.org/showthread.php?t=1385688").

---

