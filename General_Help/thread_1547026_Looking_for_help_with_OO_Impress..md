---
title: "Looking for help with OO Impress."
date: 2010-08-06
forum: General Help
---

### Post by irv on 2010-08-06
Just for the record, I posted this in a thread on OpenOffice forum but never got any help or ideas, so here goes:

Back in my Windows days I used Power Point but now that I am a Linux guy I use OpenOffice Impress instead. I have some issues I need a little help on. 
First, even in power point if I embedded sound files I had to make sure they were .wav files, and in this format they grew very large. I have been told that I can embed a .wav file in Impress, but there is a limit of 100k on the file size. Also there is a place where you can change this limitation, but I can't find where to change it. Does any one know where this setting is?
Next, let me tell you what I am trying to do and maybe someone has a better way of doing it.
 I have slides in my presentation where I display text and have sound files that read the text that is displayed. I have a couple of ways to do this, but both ways are just inserting sound files into the slide. All this does is point to the sound file and then plays it. This works find until I want to transfer it to another computer. To get the presentation to run on another computer I would have to re-insert the sound file so the pointer was right. So this means I need to not only copy the presentation over but the sound files also.
My main question: Is there a better way to do this? Even if I have to use a different program if Impress is unable to embed sound files. I believe that both Power Point and Impress both fall short in this area.
I am trying to stay away from developing a program to do this. There must be something out here in the Linux world that would fit the bill?
Has anyone done this? And if so, any tips would be appreciated.
Thanks ahead of time.

---

### Post by junapp on 2010-08-06
Almost sounds like a flash file might be a better fit with either a pre-built timeline, or a button for 'next/prev' with the audio files built in. As to how to put that together in Linux - good question.

edit:
have no idea if this works:
[http://ubuntuforums.org/showthread.php?t=1224334](http://ubuntuforums.org/showthread.php?t=1224334)

---

### Post by junapp on 2010-08-06
airslider works, but probably not quite what you are after, doesn't seem to have the ability yet to give a sound file per slide.

---

### Post by LowSky on 2010-08-06
the instructions are for openoffice being used on Windows, but I read them and its pretty straight foward
[http://www.ehow.com/how_6792153_embed-sound-openoffice-impress.html](http://www.ehow.com/how_6792153_embed-sound-openoffice-impress.html)

---

### Post by irv on 2010-08-06
> **junapp said:**
> airslider works, but probably not quite what you are after, doesn't seem to have the ability yet to give a sound file per slide.

I am using Ubuntu 10.04, and I downloaded and install airslider. If I do a screen shot of my Presentation and put it into airslider as a image and attach a MP3 sound file to it, it will work in the airslider app, but when I export it to work on the web, it cuts the sound file short even if I increase the duration on the slide. I also need a sound file for each slide, and when I add a new sound file it plays on the wrong slide. Then to top this off, I need to take a snap shot of the scree I want to display, because it does not work with text but just images. I don't believe this is the tool for the job I want to do. Impress does a good job, but if I could just embed the sound and not inserting it, things would work just the way I want.
Thanks for the input on this thread.

---

### Post by irv on 2010-08-06
> **LowSky said:**
> the instructions are for openoffice being used on Windows, but I read them and its pretty straight foward
[http://www.ehow.com/how_6792153_embed-sound-openoffice-impress.html](http://www.ehow.com/how_6792153_embed-sound-openoffice-impress.html)

I tried the one "Embedding Via the "Gallery"" and it will work If I do it this way, I can upload to my web server and play them over the Internet also. I should be able to transfer them to other computer and it should work. I really appreciate the help on this one LowSky. I am going to book mark the link you sent.

---

### Post by irv on 2010-08-06
I stand corrected. I did some further testing and it does not embed the sound file. If I move it to my web server and run it on the computer I created the presentation on it works. I believe it is because I have the sound files on this computer. If I download it to another computer it works but with no sound. Even this way it is not embedding the sound file only inserting it's path to run the sound.
I really thing this is the case.

---

### Post by irv on 2010-08-06
Here is what I finely got on OpenOffice forum:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=33049&p=151602#p151602]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=33049&p=151602#p151602")

---

### Post by shailbond on 2010-12-11
1.   After trying for long, i finally could use a video and audio file in impress on Ubuntu 10.10.
2.   In Add movie and sound check link file option.
3.   This causes video and audio to be linked and while playing presentation the video and audio plays very fine.
4.   However we cannot add option of click to play in the same. Rest all options do not work. So till the time they are fixed this option seems to be the most workable.

---

