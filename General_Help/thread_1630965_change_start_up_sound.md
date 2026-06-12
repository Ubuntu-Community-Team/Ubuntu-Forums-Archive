---
title: "change start up sound"
date: 2010-11-26
forum: General Help
---

### Post by dante19992 on 2010-11-26
i have ubuntu 10.10 and i do NOT like the startup sound. anyone help changeing it?

---

### Post by wei2912 on 2010-11-26
Which one? The login window sound or the logging in sound?

---

### Post by dante19992 on 2010-11-26
well both. i dont really like either

---

### Post by wei2912 on 2010-11-26
i don't like both too.

It is possible to disable the logging in sound. For the login window, i got no idea.

First, go to system then find Startup applications. Find:
GNOME login sound
Uncheck that and you're done!

---

### Post by Paddy Landau on 2010-11-26
I don't know how to change the sound, but you can turn off the sound on login.

[LIST=1]
[*]System > Preferences > Startup Applications
[*]Scroll down to "GNOME Login Sound". Uncheck.
[*]Close.
[/LIST]

---

### Post by dante19992 on 2010-11-26
thank you bolth but i don't wish to turn it off. i wish to change it. thank u anyway but ill keep hoping someone else will know

---

### Post by wei2912 on 2010-11-26
Well...

Just follow my instructions, then add your sound. :D

---

### Post by dante19992 on 2010-11-26
ok may i have ur instructions then?

---

### Post by dante19992 on 2010-11-26
or someone i cant figure this out

---

### Post by wei2912 on 2010-11-26
> **wei2912 said:**
> 
First, go to system then find Startup applications. Find:
GNOME login sound
Uncheck that and you're done!

My instructions.

Additional step for changing:
Press add and choose your sound!

---

### Post by dante19992 on 2010-11-26
ill try that. ill be back in a few i have to reinstall ubuntu. i had switched to mint cuz i dont like the opening from ubuntu

---

### Post by dante19992 on 2010-11-26
will this actually work? or do i wanna edit the already existing one?

---

### Post by dante19992 on 2010-11-26
im not sure if i did it wrong or what but it didnt work. anyone have any more in depth instructions?

---

### Post by satish_j on 2010-11-26
Go to system->Preferences-->Startup Applications->Gnome Login sound
Click on edit and share with us the command that is being used..

---

### Post by dante19992 on 2010-11-26
```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```this should be the one

---

### Post by satish_j on 2010-11-26
> **dante19992 said:**
> ```
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
```
this one?

Replace it with foll:
```

/usr/bin/canberra-gtk-play --file=/path to your sound file

```
Logout and Login again.It should play your sound file.

---

### Post by dante19992 on 2010-11-26
ok but before i do is there a length limit? and thank u very much for the help

---

### Post by satish_j on 2010-11-26
> **dante19992 said:**
> ok but before i do is there a length limit? and thank u very much for the help

There is no length limit.You can even use an entire mp3 file for Login sound.(Ofcourse,that does not make sense though)
Iam using an 20 second sound clip.;)

---

### Post by dante19992 on 2010-11-26
thank u very much. now to find an app to cut off the opening of everything's magic by AVA

---

### Post by oliwek on 2010-11-26
You can use [audacity]("apt://audacity")

you'll find online [tutorials]("http://www.audiorecording.me/audacity-mixing-tutorial-in-ubuntuimporting-audio-duplicating-clips.html") if you need it (just google tutorial audacity)

---

### Post by dante19992 on 2010-11-26
tried it it doesnt work at all

---

### Post by dante19992 on 2010-11-26
> **satish_j said:**
> Replace it with foll:
```

/usr/bin/canberra-gtk-play --file=/path to your sound file

```Logout and Login again.It should play your sound file.
it isnt working. this is the code i used
```
/usr/bin/canberra-gtk-play --file=/~/home/bobby/Music/Boot Sound/AVA_EM.mp3
```i also tried
```
/usr/bin/canberra-gtk-play --file=//home/bobby/Music/Boot Sound/AVA_EM.mp3
```and
```
/usr/bin/canberra-gtk-play --file=/home/bobby/Music/Boot Sound/AVA_EM.mp3
```any suggestions?

---

### Post by satish_j on 2010-11-26
> **dante19992 said:**
> it isnt working. this is the code i used
```
/usr/bin/canberra-gtk-play --file=/~/home/bobby/Music/Boot Sound/AVA_EM.mp3
```i also tried
```
/usr/bin/canberra-gtk-play --file=//home/bobby/Music/Boot Sound/AVA_EM.mp3
```and
```
/usr/bin/canberra-gtk-play --file=/home/bobby/Music/Boot Sound/AVA_EM.mp3
```any suggestions?

Your 3rd attamept is correct.There will be only one slash(/) for --file option and **not** two..
Also,try renaming 'Boot Sound' directory to 'BootSound' i.e remove the space.
Always try to avoid spaces in folder/file names in ***Linux***

---

### Post by Paddy Landau on 2010-11-26
> **dante19992 said:**
> ```
/usr/bin/canberra-gtk-play --file=/home/bobby/Music/Boot Sound/AVA_EM.mp3
```
See the space in your file name? That means the program sees the following *two* options:

[LIST=1]
[*]--file=/home/bobby/Music/Boot
[*]Sound/AVA_EM.mp3
[/LIST]
You need to put quotes whenever you have spaces.
```
/usr/bin/canberra-gtk-play --file='/home/bobby/Music/Boot Sound/AVA_EM.mp3'
```

---

### Post by dante19992 on 2010-11-26
ah i thought of that but i figured sumtin so minor wouldnt be the cause in an operating system as great as linux

---

### Post by dante19992 on 2010-11-26
no dice. as well how do i change the sound theme?

---

### Post by Paddy Landau on 2010-11-26
> **dante19992 said:**
> no dice. as well how do i change the sound theme?
You may have a problem with the sound file. I find that canberra doesn't play my MP3 files.

Open a terminal and enter the command there. See if it gives you an error message.

---

### Post by oliwek on 2010-11-26
You could try to convert your mp3 login sound to wav, then enter the right path to the wav file

if you convert the mp3 file to a wav file named AVA_EM.wav, you'll try :

```
/usr/bin/canberra-gtk-play --file='/home/bobby/Music/Boot Sound/AVA_EM.wav'
```

---

### Post by oliwek on 2010-11-26
for information about how to change the gnome login sound :

read the pdf you'll find from : [http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

-> direct link : [http://www.mediafire.com/?2yimyo3ow3t](http://www.mediafire.com/?2yimyo3ow3t) ; page 41 to page 44

really good guide

note the sentence :
[I]To play a sound file that is not part of the sound theme, use the file=PATH commandline parameter. To play a file named loginmusic.wav, enter (replace /dir/ with the directory containing the sound file):
canberragtkplay file="/dir/loginmusic.wav"
NOTE:The specified path must be an absolute path. Also, **[COLOR="Red"]canberragtkplay can only play files in the ogg, oga and wav format[/COLOR]**.[/I]

so you convert your mp3 file to wav (or ogg if you prefer), or you can try to replace canberra with mplayer to play the login sound...

the easiest way will be the first one, use soundconverter : [http://solitarygeek.com/linux/convert-audio-files-in-ubuntu-with-sound-converter](http://solitarygeek.com/linux/convert-audio-files-in-ubuntu-with-sound-converter)

---

### Post by QLee on 2010-11-26
[QUOTE=dante19992]ah i thought of that but i figured sumtin so minor wouldnt be the cause in an operating system as great as linux[/QUOTE]
What can appear "minor" to a human reader isn't necessarily minor to a computer which parse lines literally, seeing the space as a delimiter.

If you were in a command prompt window in Windows (sometimes called a DOS prompt from the days before GUIs), you would have to enclose a pathname that included a space in quotes too.

---

### Post by t0p on 2010-11-26
> **dante19992 said:**
> ah i thought of that but i figured sumtin so minor wouldnt be the cause in an operating system as great as linux

Don't all operating systems need some way of recognizing a space in a file name?  In Linux we either enclose the file name in quotation marks ("file name.mp3") or use the \ symbol (file\ name.mp3).

So what do other "great" OSes do?

---

### Post by dante19992 on 2010-11-26
ok that worked thanks

---

### Post by JungleFish on 2011-03-25
> **wei2912 said:**
> My instructions.

Additional step for changing:
Press add and choose your sound!

More detailed explanation:
goto system -> preferences -> startup applications.
Disable the gnome login sound by clicking the little box on the left hand side.
Click add.
name -> whatever you want
command -> aplay -q yourfile.wav
description -> funny sound to impress my friends
Then click save. Then close.

---

