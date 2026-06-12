---
title: "greek subtitles"
date: 2010-10-04
forum: General Help
---

### Post by ddimit on 2010-10-04
im opening greek subtitles on ubuntu but i cannot see them
i know this happen because the subtitle created on a windows system
but  i would appreciate it if you tell me a method step  by step (because im begginer ) for how to be able to open the srt file and see the normal greek characters 
i dont want to use the option on the player to recognize the subtitle.. 
i want to be able to open the srt and edit some words for example
pls help me

---

### Post by ddimit on 2010-10-04
also i have downloaded Universal Encoding Detector because i have red somewhere that it helps for suck as these problems
i have installed it but i  dont know how to run it and work it

---

### Post by TeoBigusGeekus on 2010-10-04
Using Geany:
File->Open->More Options->Set Encoding
Select Greek-Windows 1253 and then select the srt file.

My favourite subtitle editor is gaupol - you can find it in the software center.

---

### Post by ddimit on 2010-10-05
ok but
1st: if i convert my subtitles to utf-8 then if i  go back to windows .. windows will not recognize the utf-8 srt?
2st: i have converted them and always when im playing the movie with the greek subtitles via any program when im forwarding it the subtitles dissappear
this happen only with the greek subtitles

---

### Post by TeoBigusGeekus on 2010-10-05
Forgot to tell you that when you use geany to alter greek subtitles, always make sure that before you save the file you do this:
Document->Set line endings->Convert and set to CR/LF(Win)

It wouldn't hurt to check the encoding as well:
Document->Set encoding->West European->Greek Windows 1253.

No need to convert to utf for windows to recognise the file; WIN1253 is enough and it's also the encoding that's recognised by all dvd-divx players.

---

### Post by krimmas on 2011-01-12
hi, i think i have the same problem as you did...when i play a movie with greek subs (not embedded) the outcome is some kind of unknown symbols instead of letters such as " Ï ðñïìåëåôçìÝíïò öüíïò åßíáé ç ðéï óïâáñÞ êáôçãïñßá ðïõ áðáó÷ïëåß ôá êáêïõñãïäéêåßá ìá "... i downloaded Geany as recommended but i cant really use it, there is no srt option in .../more options/set filetype and also i dont know what to do then...

i hope you can help me...

---

### Post by TeoBigusGeekus on 2011-01-12
Right click srt file>Open with Geany.
Once opened with geany, go to Document>Set Encoding>West European>Greek (Windows 1253).
Then again Document>Set Line Endings>Convert and Set to CR/LF (Windows)
Save the document and you're done.

---

### Post by krimmas on 2011-01-12
hi, TeoBigusGeekus thanks very much for you really quick reply filaraki!!!
i did as you said but an error occurred ("An error occurred while converting the file from UTF-8 in WINDOWS-1253. The file remains unsaved...)...do you have any other suggestions? thanks for your time and i hope i am not a pain in the ***...kalh xronia kiolas!

---

### Post by TeoBigusGeekus on 2011-01-12
&#935;&#961;&#972;&#957;&#953;&#945; &#960;&#959;&#955;&#955;&#940; &#960;&#945;&#964;&#961;&#953;&#974;&#964;&#951;!
UTF-8 has screwed my subtitles in the past as well.
The only other thing to suggest, is to download gaupol (it's in the software center-best subtitles' editor out there), open the file with it and try to Save As from the file menu. There you can put Greek 1253 encoding and windows endlines and try to save it.

Although it hasn't worked for me in the past, you could give it a try...

---

### Post by krimmas on 2011-01-13
i have the same problem again using the gaupol (same error)... i have searched a lot in ubuntu forums both Greek and foreign but the posts are either very old or give the same advice (about sub progs...)! i am going to install even more progs and hope that at least one will be solve the problem...i will post a reply if i have any luck... euxaristw pali filaraki!

---

### Post by TeoBigusGeekus on 2011-01-13
Where did you get the subtitle in the first place?
Also, what is the name of the movie?

---

### Post by krimmas on 2011-01-13
i have the same problem with all _greek_subs to all movies tested/played in vlc, Kplayer, movie player...i have also tried the subdownloader(by the way great prog!) but the subs downloaded dont play...

---

