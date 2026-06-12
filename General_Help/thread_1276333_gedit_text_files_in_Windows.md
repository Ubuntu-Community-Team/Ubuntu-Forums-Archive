---
title: "gedit text files in Windows"
date: 2009-09-26
forum: General Help
---

### Post by sopadeajo on 2009-09-26
Is there a way to view correctly gedit text files in Windows OS ?
(i get some strange signs when viewed under Windows)

---

### Post by sopadeajo on 2009-09-27
More precisely, when i open a gedit file under windows with notepad i get very long lines (5 or 6 screen long) and when opening with Wordpad all the accents (of french or spanish language) are replaced with strange (ascii?) characters.
I woud like to know if this can be fixed, though i know this is a Windows problem, but viewing a text file written under Ubuntu should not be a big problem to view it correctly under windows with notepad or  wordpad, even though micro$oft windows did not collaborate to try to solve these problems.

---

### Post by peculiar penguin on 2009-09-27
The solution is to use a real text editor (these are aware of things like Unicode and the different end-of-line characters used by various operating systems) instead of the jokes included with Windows. Fortunately there's a vast number of alternatives both free (Notepad++, Scite,...) and paid (Ultraedit, Textpad,...).

---

### Post by akakingess on 2009-09-27
I highly recommend Notepad++, I use it for almost everything from coding CSS and PHP to simple text documents. It is one of the great free unknown programs out there.

---

### Post by FunkyRes on 2009-09-27
Yes - One problem is notepad in Windows does not properly handle unix line breaks. Workaround - use wordpad, notepad++, PSPad (I like PSPad). Homesite is another option but is not free.

The accents looking funny is probably a utf8 issue as mentioned, I know PSPad does utf8.

---

### Post by akakingess on 2009-09-27
Notepad++ also does utf8. Just for future reference.

---

### Post by sopadeajo on 2009-09-27
Thank you for your answers.
This is an important question since you must know what to do for a document written with gedit to be correctly viewed under windows OS since , of course, not all the computers have a Ubuntu Linux system installed.

Did i understand correctly that (the only?) solution is to download Notepad++ under windows OS (as an example) ?

No way to fix it changing some settings of Notepad or Wordpad under windows OS??

---

### Post by credobyte on 2009-09-27
By installing Gedit on Windows ( it's a cross-platform editor ) :p

---

### Post by gadolinio on 2009-09-27
> **sopadeajo said:**
> 
Did i understand correctly that (the only?) solution is to download Notepad++ under windows OS (as an example) ?

No way to fix it changing some settings of Notepad or Wordpad under windows OS??

I had the same issue, and found a way to "fix" the file, so that windows's notepad can read it normally. Open the file from windows, with notepad; select all the text, copy, and paste everything in MS Word. You'll see that Word shows it correctly, with no strange symbols. Then copy that new text you now have in Word, and paste back it in the notepad. It should be ok now. Then save changes. When you open it in the future, both with notepad and with gedit, it should be normal text.
Hope you find this useful...

---

### Post by sopadeajo on 2009-09-27
> **credobyte said:**
> By installing Gedit on Windows ( it's a cross-platform editor ) :p

Thanks, credobyte, i did not know that.
I will probably choose this solution if there is no way to configure notepad nor wordpad on windows to fully accept Gedit text files.

---

### Post by sopadeajo on 2009-09-27
> **gadolinio said:**
> I had the same issue, and found a way to "fix" the file, so that windows's notepad can read it normally. Open the file from windows, with notepad; select all the text, copy, and paste everything in MS Word. You'll see that Word shows it correctly, with no strange symbols. Then copy that new text you now have in Word, and paste back it in the notepad. It should be ok now. Then save changes. When you open it in the future, both with notepad and with gedit, it should be normal text.
Hope you find this useful...

Thank you, gadolinio.
The only problem is i do not have Ms Word installed on my windows vista OS, but i could install it and try this solution.

---

### Post by sopadeajo on 2009-09-27
In fact there should be a way (and Microsoft should be obliged to compatibilize its notepad and wordpad with gedit) to automatically view a gedit file on windows OS text editors.

If this does not happen, i will have to worry every time i write a text with gedit on Linux, and want to share it, to warn people with windows OS, they should have to change their settings of their text editor and /or download gedit or notepad++ on their system.

These little things are responsable of the relatively low rate of developpement of linux and free open source software compared to windows OS, because most people feel annoyed if tey are asked to change some of their settings to be able to view correctly a simple text file.

The solution here would be to oblige Micro$oft to fully allow to view gedit textfiles (automatically) on notepad or wordpad on windows OS.

---

### Post by gadolinio on 2009-09-27
> **sopadeajo said:**
> 
(...) i will have to worry every time i write a text with gedit on Linux, and want to share it, to warn people with windows OS, they should have to change their settings of their text editor and /or download gedit or notepad++ on their system. (...)

That's why i choose to modify the text file itself, so that windows-user friends don't have to do something before reading the files i send them.
If you don't have Word, try doing the same with Wordpad, one of ubuntu forum's text boxes, or anywhere else where you see that the text copied from gedit appears without those symbols; if you can have it displayed that way, then you should be able to copy it back to notepad with the "normal" format.

---

### Post by bryncoles on 2009-09-27
> **sopadeajo said:**
> In fact there should be a way (and Microsoft should be obliged to compatibilize its notepad and wordpad with gedit) to automatically view a gedit file on windows OS text editors.

If this does not happen, i will have to worry every time i write a text with gedit on Linux, and want to share it, to warn people with windows OS, they should have to change their settings of their text editor and /or download gedit or notepad++ on their system.

These little things are responsable of the relatively low rate of developpement of linux and free open source software compared to windows OS, because most people feel annoyed if tey are asked to change some of their settings to be able to view correctly a simple text file.

The solution here would be to oblige Micro$oft to fully allow to view gedit textfiles (automatically) on notepad or wordpad on windows OS.

if you just want people to read the file (but not edit it) then why not convert it to PDF and send them that? its an open standard?

file->print->print to file->pdf

---

### Post by FunkyRes on 2009-09-27
> **sopadeajo said:**
> In fact there should be a way (and Microsoft should be obliged to compatibilize its notepad and wordpad with gedit) to automatically view a gedit file on windows OS text editors.

If this does not happen, i will have to worry every time i write a text with gedit on Linux, and want to share it, to warn people with windows OS, they should have to change their settings of their text editor and /or download gedit or notepad++ on their system.

These little things are responsable of the relatively low rate of developpement of linux and free open source software compared to windows OS, because most people feel annoyed if tey are asked to change some of their settings to be able to view correctly a simple text file.

The solution here would be to oblige Micro$oft to fully allow to view gedit textfiles (automatically) on notepad or wordpad on windows OS.

Use RTF for cross platform text files that are not executable script.

AbiWord can create rtf.
I'm fairly certain OpenOffice can creatre rtf.

rtf is also a good generic format for word processor documents (just about every word processor can read/create rtf files).

---

### Post by credobyte on 2009-09-27
> **sopadeajo said:**
> Thanks, credobyte, i did not know that.
I will probably choose this solution if there is no way to configure notepad nor wordpad on windows to fully accept Gedit text files.

The problem is that these editors doesn't know how to handle UNIX-type EOL's ( [http://en.wikipedia.org/wiki/Newline](http://en.wikipedia.org/wiki/Newline) ). As far as I know ( tough, I've never actually been much into Notepad and Wordpad ), you can't change the way they work .. it's Microsoft ( no source code available ).

---

### Post by lswb on 2009-09-27
Install the "tofrodos" package and you can convert a text file with unix EOL to DOS/Windows EOL. There are similar tools availale for Windows.

---

### Post by sopadeajo on 2009-09-27
Thanks again to everybody.I have learnt some new things (i did not know you could make a PDF directly fron a gedit text file (this is a great feature, indeed)....I'll try later if windows vista is able to read it. I still do not know if there is an option for RTF (viewable on windows OS) on gedit editor.

And it is a good thing that newcomers to Linux (like me) learn new things in a dynamic way from these forums.

---

### Post by sopadeajo on 2009-09-27
> **lswb said:**
> Install the "tofrodos" package and you can convert a text file with unix EOL to DOS/Windows EOL. There are similar tools availale for Windows.

Thanks but i am looking for a different solution because  i am looking rather for a universal and simple multiplatform format preferably just using gedit (not knowing previously if the end-user will be on an linux or a windows system).

---

### Post by mcduck on 2009-09-27
> **sopadeajo said:**
> 
These little things are responsable of the relatively low rate of developpement of linux and free open source software compared to windows OS, because most people feel annoyed if tey are asked to change some of their settings to be able to view correctly a simple text file.

Not really true. It's exactly the same thing if you try to move text files between Mac and Windows.. Bit hard to blame that one on FOSS/Linux, I'd say.. ;)

The thing is simply that Windows, Mac and Unix/Linux all have different way of handling this, and the difference is far older than Linux is.

edit: "flip" is a simple CLI tool for converting between Unix and DOS line ending formats. Although I don't think it's installed by default, but you'll find it in the repositories. You are not going to find a multiplatform format you could use with Gedit, as Gedit only handles raw text files (so no different formats).

---

### Post by StuartN on 2009-09-27
> **sopadeajo said:**
> Thanks but i am looking for a different solution because  i am looking rather for a universal and simple multiplatform format preferably just using gedit (not knowing previously if the end-user will be on an linux or a windows system).

Install uni2ascii from the repositories and then use something like:

```
cat unicode_text.txt | uni2ascii -B > dos_text.txt
```

There are plenty of options with uni2ascii, but -B is equivalent to -c (drop circles) -d (drop diacritics) -f (drop fancy styles) -x (convert special characters, e.g. U+20AC / € becomes "euro"). The -n option converts newlines.

---

### Post by mcduck on 2009-09-27
> **StuartN said:**
> Install uni2ascii from the repositories and then use something like:

```
cat unicode_text.txt | uni2ascii -B > dos_text.txt
```

There are plenty of options with uni2ascii, but -B is equivalent to -c (drop circles) -d (drop diacritics) -f (drop fancy styles) -x (convert special characters, e.g. U+20AC / &#8364; becomes "euro"). The -n option converts newlines.
Flip is easier:

From Unix to DOS:
```
flip -d somefile.txt
```

From DOS to Unix:
```
flip -u somefile.txt
```
..alsough I agree that doesn't solve Notepads lack of support for Unicode.

I really wonder what's the reason for Notepad's existence. I doubt there is (or has ever been) another text editor with as lame features as Notepad has. :D

---

### Post by FunkyRes on 2009-09-27
You can probably use iconv to convert from utf8 to whatever character set windows uses and keep the international characters.

I've used iconv to go to utf8 from other encodings, I'm fairly certain it can do the reverse.

I'd personally leave them as utf8.
Microsoft is behind the times, all other operating systems are going utf8 by default. Microsoft will come around, it will just take a few decades.

as far as end of line, I'm not sure what flip does, but you can do that with a perl one line regex.

---

### Post by RedRat on 2009-09-27
> **mcduck said:**
> Flip is easier:

From Unix to DOS:
```
flip -d somefile.txt
```From DOS to Unix:
```
flip -u somefile.txt
```..alsough I agree that doesn't solve Notepads lack of support for Unicode.

I really wonder what's the reason for Notepad's existence. I doubt there is (or has ever been) another text editor with as lame features as Notepad has. :D

Notepad was the first text editor in the old Windows 1. In reality, MS really thinks WordPad was supposed to be its successor, since it had limited formatting capabilities. I think MS just keeps it around because it has always been there and there are lot of people who prefer to use it in Windows. Too bad that MS, Apple, and Unix people can't come together and develop some kind of text standard, forget all the fancy formatting.

---

### Post by The Cog on 2009-09-27
> **credobyte said:**
> The problem is that these editors doesn't know how to handle UNIX-type EOL's

That's only half the problem - the long lines problem. The other half of the problem is the character encoding - those MS text editors don't use or understand unicode.

The editor geany has the ability to save files with different line endings and different character encodings, so if you know a file is going to be viewed in windows, you can set CR-LF line endings and whichever code page the the target windows machine happens to use, probably cp1252 since this is an english forum.

---

### Post by StuartN on 2009-09-27
This is like a bunch of old timers discussing emacs / vi / **ed / edlin** over a pint - but worse, much worse...

---

### Post by lswb on 2009-09-27
> **mcduck said:**
> Flip is easier:

...

I really wonder what's the reason for Notepad's existence. I doubt there is (or has ever been) another text editor with as lame features as Notepad has. :D

Pretty sure Notepad was around before unicode was adopted as a standard. If you want lame, try ed or edlin.

---

### Post by sopadeajo on 2009-09-27
> **mcduck said:**
> Not really true. It's exactly the same thing if you try to move text files between Mac and Windows.. Bit hard to blame that one on FOSS/Linux, I'd say.. ;)

The thing is simply that Windows, Mac and Unix/Linux all have different way of handling this, and the difference is far older than Linux is.



Yes, but the vocation of free and open source software is a vocation of universality (this is not the case of Mac for which it suffices a small percentage of the microsoft market to be well and alive (speaking in dollars) and whose philosophy is a stand-alone philosophy which is not obviously (and must not be) the philosophy of open source.

Open source can do anything alone, but seeks to convince the more people as possible, that it is the best way for a universal kind of software open source and free .For this to be done, one of the steps is to  let some of the common Linux-Unix files (simple text files ,as an example) to be able to be used by the majority users (micro$oft users, but Mac users as well) in a very simple way.

 I remember i have spent many years not using Linux because there was no interaction at all between Linux and Windows and i had the totally  false idea that Linux was only a command line OS (which is not at all true, in fact there are as many GUI programs as in windows or even more), and that it would be boring and difficult to use because you'll have to remember tons of commands to make it work and this is not true: Linux (Ubuntu at least) is very easy to use (as easy as window$ or even easier).

So, what i mean, is that to break the fear of the newcomer, something should be done to let him know that Linux works at least as well as Windows, and is as easy to use, and is not a closed OS. (windows, and Mac OS are closed systems, Linux, must not be).


I am not a developer, but if i was i would look for to try to find a software solution for a universal simple text editor that detects the OS and changes automatically the settings such that a file written in a system is viewable in another one and vice versa. I believe this would not be too hard to be done. I know there is already PDF, but i am talking of simple text files to be shared between different OS.

Sorry for the bad English.


Edited yust to say that i did not understand the comment: "Bit hard to blame that one on FOSS/Linux, I'd say.. :wink:· ". Sorry but i am a newbie to Linux, do not know what is FOSS.

---

### Post by Tamalin on 2009-09-27
> **sopadeajo said:**
> 
Did i understand correctly that (the only?) solution is to download Notepad++ under windows OS (as an example) ?

No way to fix it changing some settings of Notepad or Wordpad under windows OS??

Notepad is not quality software.  It is just there so microsoft can say they include a text editor in their system.

---

### Post by sopadeajo on 2009-09-27
> **The Cog said:**
> That's only half the problem - the long lines problem. The other half of the problem is the character encoding - those MS text editors don't use or understand unicode.

The editor geany has the ability to save files with different line endings and different character encodings, so if you know a file is going to be viewed in windows, you can set CR-LF line endings and whichever code page the the target windows machine happens to use, probably cp1252 since this is an english forum.

Reading this comment from The Cog , gave me a clue as for why WordPad on windows showed a gedit text file lines correctly but accents (spanish and french accents) incorrectly. My windows Vista is set to Spanish language while i choosed English language for Ubuntu Jaunty settings. Gedit accepts the accents and represents them correctly on Jaunty Ubuntu, since i have the appropriate keyboard, but transported to Spanish-settings Vista WordPad, it cannot show the accents. Not sure this is the problem, though.

---

### Post by sopadeajo on 2009-09-27
> **RedRat said:**
> Notepad was the first text editor in the old Windows 1. In reality, MS really thinks WordPad was supposed to be its successor, since it had limited formatting capabilities. I think MS just keeps it around because it has always been there and there are lot of people who prefer to use it in Windows. Too bad that MS, Apple, and Unix people can't come together and develop some kind of text standard, forget all the fancy formatting.

I have written some long mathematical equations and results using only Notepad and the keyboard characters. I prefer it to WordPad and some people say it's still worse than Notepad, though it is true that Notepad is Nothing.

To develop some kind of text standard would certainly be a very good thing.
Text is a basic and important matter.

---

### Post by Marlonsm on 2009-09-27
Also, instead of running some alternative to notepad in Windows, you can also use Notepad itself in Linux, it comes with Wine, a program that runs programs for Windows inside Linux (you can find in Applications > Add/Remove).

I wouldn't recomend using it over gedit, but if you have to be sure people using Windows will see your files correctly, you can use it.

---

### Post by mcduck on 2009-09-28
> **lswb said:**
> Pretty sure Notepad was around before unicode was adopted as a standard. If you want lame, try ed or edlin.

Been there, done that. But my point was that even Edit was more usable editor, and somehow Microsoft didn't manage to improve a bit from that when creating Notepad. It's basically ancient DOS text editor converted into a graphical interface. And hasn't realy improved a bit since those days.

(besides, when it comes to Microsoft Unicode still isn't adopted as a standard. :D)

I don't prefer Wordpad over Notepad, if I need text formatting I use a full-blown office app like OpenOffice or some proper desktop publishing tool. What I mean that even as a plain text editor Notepad is pretty much the worst one around.

---

### Post by mcduck on 2009-09-28
> **sopadeajo said:**
> 
I am not a developer, but if i was i would look for to try to find a software solution for a universal simple text editor that detects the OS and changes automatically the settings such that a file written in a system is viewable in another one and vice versa. I believe this would not be too hard to be done. I know there is already PDF, but i am talking of simple text files to be shared between different OS.

The problem is that the editor would have no way of recognizing which OS you are sending the files to. :)

I mean it's not  hard to make editor that detects what OS *you* are runing, and what format the file you open is. But that won't help a bit when you send the file to somebody else. 

(And FOSS is short for free, open-source software. I mentioned that since you clamed that Linux/FOSS shouldn't use different format from Wndows. he point was that the line ending format Linux uses comes from Unix, and therefore existed long before Linux. So the difference between Windos and Unix/Linux line endings can in no way be blamed on Linux developers. They are simply folowing the Posix standars, which is pretty much one of te main points behind Linuxes existence. To be a free, Posix-compatible OS. The only surprise is that when Apple moved to Unix base they still kept their own old line ending format instead of moving to the Unix standard when they had a chance. Bt they didn't move to the Windows format either..)

---

### Post by The Cog on 2009-09-28
> **sopadeajo said:**
> I have written some long mathematical equations and results using only Notepad and the keyboard characters. I prefer it to WordPad and some people say it's still worse than Notepad, though it is true that Notepad is Nothing.

To develop some kind of text standard would certainly be a very good thing.
Text is a basic and important matter.

Tell that to Microsoft. Unicode has been around for more than a few weeks. It's MS that doesn't bother to support it. No change there then. And if you are trying to argue that what Notepad does should be a standard, then you have to decide **which** notepad that should be. Notepad uses different character codes depending on where you are in the world.

There is a standard, it is called Unicode, and Linux uses it. MS doesn't want to. At least part of the reason is so that they can point at files that don't render right in their programs like notepad (same goes for IE and web documents) and say "Look, see, life would be so much easier if everyone just used windows.". Seems like they have you believing it.

Edit:
On re-reading this, that last sentence comes across as rather insulting. Sorry, that wasn't the intention. I am irritated at MSs ignoring and wilful corruption of standards at the rest of the world's expense.

---

### Post by sopadeajo on 2009-09-28
> **mcduck said:**
> The problem is that the editor would have no way of recognizing which OS you are sending the files to. :)

I mean it's not  hard to make editor that detects what OS *you* are runing, and what format the file you open is. But that won't help a bit when you send the file to somebody else. 



I am saying that Micro$oft should add some software capabilities to Notepad or Wordpad such that a Linux text file (a Gedit file as an example) is automatically recognized and viewed correctly by displaying the correct EOL settings and whatever settings are needed for a correct view.. What i am saying is forcing (asking to) Micro$oft to act this way. And conversely i would add software to Gedit such that a a Nnotepad or Wordpad text file would be correctly viewed with Gedit text editor. In fact i do not know if Gedit is already able to view correctly windows simple text files. 
And certainly i never said Notepad is a good text editor. It is a very bad one, Gedit is much better, but what i said is Wordpad is not really better in my opinion than Notepad, and so i have been using Notepad rather than Wordpad  (all is bad in the Micro$oft closed kingdom).

 And i said also that it would be important, besides that to try to implement a text standard though i know that the lack of will to do this is the lack of will of Micro$oft who wants to create the more bordiers as possible between systems by not permitting interchangeability (or simple portability). The guilty is Micro$oft with its closed OS system.
But i'll do what i could to show microsoft that Linux software is able of accepting and viewing windows simple text files even though the contrary is not true.

---

### Post by RedRat on 2009-09-28
It is not entirely true that MS doesn't want to use unicode, I believe that you can actually select it for use in Windows. However it is not there by default.

As to the debate over which text editor to use, I think the argument is somewhat pointless, face the fact that Unix, MS, and Apple all have their ways of EOL. Pain in the @ss for sure, but this does not appear to be changing in the near or even far future. Which is better? Much like asking which is better: Apple or Orange. Make you choice and live with it for better or worse. Should things be different, sure, but it is what it is, let's get on with it.

---

### Post by sopadeajo on 2009-09-28
In fact all the windows text files i have (written using Notepad) can be viewed correctly with gedit on Jaunty Ubuntu except for the french "apostrophe": ( "c'est" as an example) which is shown as "cŽest" by gedit on Jaunty. This could be due to the fact that my windows Vista is configured for Spanish language while Jaunty is configured for English language (I do not know).
But the contrary is worse.No format at all is kept (very long lines (6 or 7 screens long) when viewing a Gedit file with Notepad on windows Vista).

---

### Post by sopadeajo on 2009-09-28
> **sopadeajo said:**
> In fact all the windows text files i have (written using Notepad) can be viewed correctly with gedit on Jaunty Ubuntu except for the french "apostrophe": ( "c'est" as an example) which is shown as "cŽest" by gedit on Jaunty.  

And so anybody could help with any idea  to fix this problem?
How to view correctly the French apostrophe?
And get rid of a strange square that disappears when pasted on this window which seems to replace "..." or ".." ?

See an example of what gedit shows in french language:

"JŽai lu au moins une douzaine de commentaires se plaignant du nom du futur parti. Je nŽai pas beaucoup dŽimagination, mais si vous voulez un  
parti de gauche (de vraie gauche) au nom vraiment percutant nous pourrions le nommer le Parti Supercalifragilisticoexpialidose (PS). Ce nom 
 donne une grande impression de puissance et de mystère; mais est-il de gauche?&#133;avec un nom comme ça on sŽen fiche. 
Est-ce quŽune rose est plus importante par son nom que par ce quŽelle est? 
Est-ce que le titre (le nom), le continent,lŽenveloppe, est plus important que le contenu? "

---

### Post by StuartN on 2009-09-29
> **sopadeajo said:**
> See an example of what gedit shows in french language:

"JŽai lu au moins une douzaine de commentaires

Well **cat test.txt | sed s/Ž/\'/** would work, if that is the only problem character.

---

### Post by The Cog on 2009-09-29
Can you make a small file containing maybe a sencence including that apostrophe and also the ... thing you say you are losing in the pasting? Copy the file to Linux and run the command **hexdump -C <filename>** and post it here. Then we can see exactly what's in the file itself, ruling out any copy/paste/post/webserver/browser translations.

Edit:
On further reading, I see that **hd <filename>** does the same as **hexdump -C <filename>**

---

### Post by sopadeajo on 2009-09-29
I get this error:

-desktop:~$ hexdump -C <Example>
bash: syntax error near unexpected token `newline'

Edited:
Pasting the text directly to terminal and doing hexdump -C :

q
Mais il y a aussi le danger d&#381;un culte excessif de la personnalité de la part de Chavez, et en ce sens l&#381;action de l&#381;extrême droite -qui le pousse à se 

retrancher- est efficace dans le sens qu&#381;ils peuvent provoquer une stratification et une paralysation du processus de chamboulement social qui doit se 

mener à terme.

J&#381;avoue que je n&#381;aime pas le populisme excessif de” harangue des masses” que Chavez utilise, parce qu&#381;il faut davantage transformer réellement sur le 

terrain et moins dire vainement. Faisons les transformations sociales nécessaires; on a l&#381;impression que Chavez ne sait trop quoi faire ou n&#381;a pas de 

vrais organisateurs parmi ses appuis, et que tout le monde attend que ce soit l&#381;autre qui décide et/ou organise pour lui. Je me souviens du ministre

 d&#381;éducation du Nicaragua (Fernando Cardenal) qui m&#381;avait dit- quand je lui demandais pourquoi la révolution s&#381;était tarie, avait presque perdu; qu&#381;ils

 ne savaient pas trop quoi faire, que soudain ils avaient le pouvoir, il était ministre, mais que faire rapidement et efficacement??

Mais ils avaient perdu (aux elections législatives et présidentielles, aux urnes), parce que les etatsuniens (CIA) avaient organisé une contreguerrilla

 (avec la même extrême droite sociologique que celle qui s&#381;oppose à Chavez) en Honduras qui avait presque ruiné le pays déjà sousdéveloppé.

Il m&#381;avait dit aussi que Daniel Ortega (ancien et actuel président et chef du FSLN) était un traître. Apparemment ils n&#381;étaient plus d&#381;accord sur tout…

00000000  71 0a 4d 61 69 73 20 69  6c 20 79 20 61 20 61 75  |q.Mais il y a au|
00000010  73 73 69 20 6c 65 20 64  61 6e 67 65 72 20 64 c5  |ssi le danger d.|
00000020  bd 75 6e 20 63 75 6c 74  65 20 65 78 63 65 73 73  |.un culte excess|
00000030  69 66 20 64 65 20 6c 61  20 70 65 72 73 6f 6e 6e  |if de la personn|
00000040  61 6c 69 74 c3 a9 20 64  65 20 6c 61 20 70 61 72  |alit.. de la par|
00000050  74 20 64 65 20 43 68 61  76 65 7a 2c 20 65 74 20  |t de Chavez, et |
00000060  65 6e 20 63 65 20 73 65  6e 73 20 6c c5 bd 61 63  |en ce sens l..ac|
00000070  74 69 6f 6e 20 64 65 20  6c c5 bd 65 78 74 72 c3  |tion de l..extr.|
00000080  aa 6d 65 20 64 72 6f 69  74 65 20 2d 71 75 69 20  |.me droite -qui |
00000090  6c 65 20 70 6f 75 73 73  65 20 c3 a0 20 73 65 20  |le pousse .. se |
000000a0  0a 0a 72 65 74 72 61 6e  63 68 65 72 2d 20 65 73  |..retrancher- es|
000000b0  74 20 65 66 66 69 63 61  63 65 20 64 61 6e 73 20  |t efficace dans |
000000c0  6c 65 20 73 65 6e 73 20  71 75 c5 bd 69 6c 73 20  |le sens qu..ils |
000000d0  70 65 75 76 65 6e 74 20  70 72 6f 76 6f 71 75 65  |peuvent provoque|
000000e0  72 20 75 6e 65 20 73 74  72 61 74 69 66 69 63 61  |r une stratifica|
000000f0  74 69 6f 6e 20 65 74 20  75 6e 65 20 70 61 72 61  |tion et une para|
00000100  6c 79 73 61 74 69 6f 6e  20 64 75 20 70 72 6f 63  |lysation du proc|
00000110  65 73 73 75 73 20 64 65  20 63 68 61 6d 62 6f 75  |essus de chambou|
00000120  6c 65 6d 65 6e 74 20 73  6f 63 69 61 6c 20 71 75  |lement social qu|
00000130  69 20 64 6f 69 74 20 73  65 20 0a 0a 6d 65 6e 65  |i doit se ..mene|
00000140  72 20 c3 a0 20 74 65 72  6d 65 2e 0a 0a 4a c5 bd  |r .. terme...J..|
00000150  61 76 6f 75 65 20 71 75  65 20 6a 65 20 6e c5 bd  |avoue que je n..|
00000160  61 69 6d 65 20 70 61 73  20 6c 65 20 70 6f 70 75  |aime pas le popu|
00000170  6c 69 73 6d 65 20 65 78  63 65 73 73 69 66 20 64  |lisme excessif d|
00000180  65 c2 94 20 68 61 72 61  6e 67 75 65 20 64 65 73  |e.. harangue des|
00000190  20 6d 61 73 73 65 73 c2  94 20 71 75 65 20 43 68  | masses.. que Ch|
000001a0  61 76 65 7a 20 75 74 69  6c 69 73 65 2c 20 70 61  |avez utilise, pa|
000001b0  72 63 65 20 71 75 c5 bd  69 6c 20 66 61 75 74 20  |rce qu..il faut |
000001c0  64 61 76 61 6e 74 61 67  65 20 74 72 61 6e 73 66  |davantage transf|
000001d0  6f 72 6d 65 72 20 72 c3  a9 65 6c 6c 65 6d 65 6e  |ormer r..ellemen|
000001e0  74 20 73 75 72 20 6c 65  20 0a 0a 74 65 72 72 61  |t sur le ..terra|
000001f0  69 6e 20 65 74 20 6d 6f  69 6e 73 20 64 69 72 65  |in et moins dire|
00000200  20 76 61 69 6e 65 6d 65  6e 74 2e 20 46 61 69 73  | vainement. Fais|
00000210  6f 6e 73 20 6c 65 73 20  74 72 61 6e 73 66 6f 72  |ons les transfor|
00000220  6d 61 74 69 6f 6e 73 20  73 6f 63 69 61 6c 65 73  |mations sociales|
00000230  20 6e c3 a9 63 65 73 73  61 69 72 65 73 3b 20 6f  | n..cessaires; o|
00000240  6e 20 61 20 6c c5 bd 69  6d 70 72 65 73 73 69 6f  |n a l..impressio|
00000250  6e 20 71 75 65 20 43 68  61 76 65 7a 20 6e 65 20  |n que Chavez ne |
00000260  73 61 69 74 20 74 72 6f  70 20 71 75 6f 69 20 66  |sait trop quoi f|
00000270  61 69 72 65 20 6f 75 20  6e c5 bd 61 20 70 61 73  |aire ou n..a pas|
00000280  20 64 65 20 0a 0a 76 72  61 69 73 20 6f 72 67 61  | de ..vrais orga|
00000290  6e 69 73 61 74 65 75 72  73 20 70 61 72 6d 69 20  |nisateurs parmi |
000002a0  73 65 73 20 61 70 70 75  69 73 2c 20 65 74 20 71  |ses appuis, et q|
000002b0  75 65 20 74 6f 75 74 20  6c 65 20 6d 6f 6e 64 65  |ue tout le monde|
000002c0  20 61 74 74 65 6e 64 20  71 75 65 20 63 65 20 73  | attend que ce s|
000002d0  6f 69 74 20 6c c5 bd 61  75 74 72 65 20 71 75 69  |oit l..autre qui|
000002e0  20 64 c3 a9 63 69 64 65  20 65 74 2f 6f 75 20 6f  | d..cide et/ou o|
000002f0  72 67 61 6e 69 73 65 20  70 6f 75 72 20 6c 75 69  |rganise pour lui|
00000300  2e 20 4a 65 20 6d 65 20  73 6f 75 76 69 65 6e 73  |. Je me souviens|
00000310  20 64 75 20 6d 69 6e 69  73 74 72 65 0a 0a 20 64  | du ministre.. d|
00000320  c5 bd c3 a9 64 75 63 61  74 69 6f 6e 20 64 75 20  |....ducation du |
00000330  4e 69 63 61 72 61 67 75  61 20 28 46 65 72 6e 61  |Nicaragua (Ferna|
00000340  6e 64 6f 20 43 61 72 64  65 6e 61 6c 29 20 71 75  |ndo Cardenal) qu|
00000350  69 20 6d c5 bd 61 76 61  69 74 20 64 69 74 2d 20  |i m..avait dit- |
00000360  71 75 61 6e 64 20 6a 65  20 6c 75 69 20 64 65 6d  |quand je lui dem|
00000370  61 6e 64 61 69 73 20 70  6f 75 72 71 75 6f 69 20  |andais pourquoi |
00000380  6c 61 20 72 c3 a9 76 6f  6c 75 74 69 6f 6e 20 73  |la r..volution s|
00000390  c5 bd c3 a9 74 61 69 74  20 74 61 72 69 65 2c 20  |....tait tarie, |
000003a0  61 76 61 69 74 20 70 72  65 73 71 75 65 20 70 65  |avait presque pe|
000003b0  72 64 75 3b 20 71 75 c5  bd 69 6c 73 0a 0a 20 6e  |rdu; qu..ils.. n|
000003c0  65 20 73 61 76 61 69 65  6e 74 20 70 61 73 20 74  |e savaient pas t|
000003d0  72 6f 70 20 71 75 6f 69  20 66 61 69 72 65 2c 20  |rop quoi faire, |
000003e0  71 75 65 20 73 6f 75 64  61 69 6e 20 69 6c 73 20  |que soudain ils |
000003f0  61 76 61 69 65 6e 74 20  6c 65 20 70 6f 75 76 6f  |avaient le pouvo|
00000400  69 72 2c 20 69 6c 20 c3  a9 74 61 69 74 20 6d 69  |ir, il ..tait mi|
00000410  6e 69 73 74 72 65 2c 20  6d 61 69 73 20 71 75 65  |nistre, mais que|
00000420  20 66 61 69 72 65 20 72  61 70 69 64 65 6d 65 6e  | faire rapidemen|
00000430  74 20 65 74 20 65 66 66  69 63 61 63 65 6d 65 6e  |t et efficacemen|
00000440  74 3f 3f 0a 0a 4d 61 69  73 20 69 6c 73 20 61 76  |t??..Mais ils av|
00000450  61 69 65 6e 74 20 70 65  72 64 75 20 28 61 75 78  |aient perdu (aux|
00000460  20 65 6c 65 63 74 69 6f  6e 73 20 6c c3 a9 67 69  | elections l..gi|
00000470  73 6c 61 74 69 76 65 73  20 65 74 20 70 72 c3 a9  |slatives et pr..|
00000480  73 69 64 65 6e 74 69 65  6c 6c 65 73 2c 20 61 75  |sidentielles, au|
00000490  78 20 75 72 6e 65 73 29  2c 20 70 61 72 63 65 20  |x urnes), parce |
000004a0  71 75 65 20 6c 65 73 20  65 74 61 74 73 75 6e 69  |que les etatsuni|
000004b0  65 6e 73 20 28 43 49 41  29 20 61 76 61 69 65 6e  |ens (CIA) avaien|
000004c0  74 20 6f 72 67 61 6e 69  73 c3 a9 20 75 6e 65 20  |t organis.. une |
000004d0  63 6f 6e 74 72 65 67 75  65 72 72 69 6c 6c 61 0a  |contreguerrilla.|
000004e0  0a 20 28 61 76 65 63 20  6c 61 20 6d c3 aa 6d 65  |. (avec la m..me|
000004f0  20 65 78 74 72 c3 aa 6d  65 20 64 72 6f 69 74 65  | extr..me droite|
00000500  20 73 6f 63 69 6f 6c 6f  67 69 71 75 65 20 71 75  | sociologique qu|
00000510  65 20 63 65 6c 6c 65 20  71 75 69 20 73 c5 bd 6f  |e celle qui s..o|
00000520  70 70 6f 73 65 20 c3 a0  20 43 68 61 76 65 7a 29  |ppose .. Chavez)|
00000530  20 65 6e 20 48 6f 6e 64  75 72 61 73 20 71 75 69  | en Honduras qui|
00000540  20 61 76 61 69 74 20 70  72 65 73 71 75 65 20 72  | avait presque r|
00000550  75 69 6e c3 a9 20 6c 65  20 70 61 79 73 20 64 c3  |uin.. le pays d.|
00000560  a9 6a c3 a0 20 73 6f 75  73 64 c3 a9 76 65 6c 6f  |.j.. sousd..velo|
00000570  70 70 c3 a9 2e 0a 0a 49  6c 20 6d c5 bd 61 76 61  |pp.....Il m..ava|
00000580  69 74 20 64 69 74 20 61  75 73 73 69 20 71 75 65  |it dit aussi que|
00000590  20 44 61 6e 69 65 6c 20  4f 72 74 65 67 61 20 28  | Daniel Ortega (|
000005a0  61 6e 63 69 65 6e 20 65  74 20 61 63 74 75 65 6c  |ancien et actuel|
000005b0  20 70 72 c3 a9 73 69 64  65 6e 74 20 65 74 20 63  | pr..sident et c|
000005c0  68 65 66 20 64 75 20 46  53 4c 4e 29 20 c3 a9 74  |hef du FSLN) ..t|
000005d0  61 69 74 20 75 6e 20 74  72 61 c3 ae 74 72 65 2e  |ait un tra..tre.|
000005e0  20 41 70 70 61 72 65 6d  6d 65 6e 74 20 69 6c 73  | Apparemment ils|
000005f0  20 6e c5 bd c3 a9 74 61  69 65 6e 74 20 70 6c 75  | n....taient plu|
00000600  73 20 64 c5 bd 61 63 63  6f 72 64 20 73 75 72 20  |s d..accord sur |

---

### Post by The Cog on 2009-09-29
Sorry, the <> brackets were meant to indicate the filename should be entered there, not to be typed. So **hexdump -C Example.txt** would have done the trick. But never mind, I have the attached file to look at.

Well, It's got me stymied. It's encoding your apostrophe as two bytes 0xc5, 0xbd which is the UTF8 encoding for unicode character 0x017d which is the Z with the accent over the top. I can't think of a two byte encoding where those two bytes could mean an apostrophe. It's got me beat.

And the other odd one is the two bytes 0xc2, 0x94 which decodes to character value 0x94 which is not a printable character at all in Unicode. 

So I really don't know what character coding Notepad is using. It can't be one of the normal windows code pages because they all only use one byte per character. Sorry, I really don't know. All I can think of is to use a program to find and replace those sequences with the characters you know they should be. I'll work on a script to do that and get back to you when I get more time.

Edit:
```
cat Example.txt | sed "s:\xc5\xbd:\x27:g" | sed "s:\xc2\x94:...:g" > Example2.txt
``` does most of it,but I also see that the last word is followed by a pair of bytes 0xc2, 0x85 and I don't know what this character shold be.

I really think you should give up on notepad. I suggest using geany, which can save text files in many different character codings, but at leasy you have control and know which characterset your output file is using.

---

### Post by StuartN on 2009-09-29
Like I said, **cat Example.txt | sed s/Ž/\'/** converts your example correctly, but there is at least one other character that needs replacing, so you could add the substitutions for that.

---

### Post by The Cog on 2009-09-29
> **StuartN said:**
> Like I said, **cat Example.txt | sed s/Ž/\'/** converts your example correctly, but there is at least one other character that needs replacing, so you could add the substitutions for that.

Yes it does. For some reason, I'm not comfortable using those characters without explicit hex values. I can't think of a good justification for that uneasiness though - it just feels fragile to me. Oh, that second byte sequence doesn't have a printable unicode mapping, so you have to use the \x representation in that instance.

---

### Post by sopadeajo on 2009-09-29
> **The Cog said:**
> 

So I really don't know what character coding Notepad is using. It can't be one of the normal windows code pages because they all only use one byte per character. Sorry, I really don't know. All I can think of is to use a program to find and replace those sequences with the characters you know they should be. I'll work on a script to do that and get back to you when I get more time.

  

In fact those texts were not written directly on Notepad on Windows Vista but rather written on different Internet forums and then copied and pasted to Notepad (all this on Windows Vista, not on Linux).The problem comes when viewing these Notepad Windows text files with Gedit on Linux.

---

### Post by sopadeajo on 2009-09-29
The square with 4 numbers in it appears for " and ...

Edited To The Cog:

The first two of these squares replace " and not ... and the last is for ...

You must modify your code

---

### Post by StuartN on 2009-09-29
> **The Cog said:**
> that second byte sequence doesn't have a printable unicode mapping, so you have to use the \x representation in that instance.

But how do you enter a unicode sequence in Bash? \x will only accept two hexadecimal characters, not four. <OOPS edit>

You can use **sed s/$'\xc5'$'\xbd'/\'/g** to encode the character values.

---

### Post by The Cog on 2009-09-30
You are actually entering the UTF8 byte sequence, not the unicode character, since it is the byte sequence in the file that you are seeking and replacing. 

Typing the unicode character to be replaced is presumably having that character translated into the utf8 representation before passing it to sed. So I guess the results should be the same, but it makes me feel nervous to rely on these hidden translations.

Maybe something like this:
```
cat Example.txt | sed s/$'\xc5\xbd'/\'/g | sed s/$'\xc2\x94'/\"/g | sed s/$'\xc2\x85'/.../g > Example2.txt
```

---

### Post by sopadeajo on 2009-09-30
Can you explain what does exactly this code do and the semantics of it? If you do so, people would be able to code themselves rather than just copy and paste

Are c5 and c2 characters replaced by bd and 94 or 85 characters?

---

### Post by StuartN on 2009-09-30
> **sopadeajo said:**
> Can you explain what does exactly this code do and the semantics of it?

Sed edits a stream and the argument s/pattern1/pattern2/ means find pattern 1 and substitute with pattern 2. The final g (s/p1/p2/g) means global, i.e. every occurrence of p1 is replaced with p2.

The first call **sed s/$'\xc5'$'\xbd'/\'/g** is looking for a pattern consisting of the hex byte c5 ($'\xc5') followed by the hex byte bd and replacing both bytes with an apostrophe (\'). This is piped through successive calls to sed to replace the other two-byte accented characters with an appropriate substitute.

---

### Post by The Cog on 2009-09-30
Stuarts explanation is pretty good. I'll try to fill in some small gaps:

cat (short short concatenate) is being used to read the file and send it to its standard output. Hence the ```
cat Example.txt
```. The vertial line | says to take the output from one program and feed it into the input of another program. So this:
```
cat Example.txt | sed s/$'\xc5\xbd'/\'/g
```
uses cat to type the file, and passes that to the program **sed** (stream editor), the arguments of which tell it to replace those two bytes with an apostrophe. But the output of that sed program still has other byte pairs that need replacing, so we pass its output to another copy of sed which replaces another pair, and pass the output of that to a third set program which replaces the third pair of bytes. And the > symbol says to take the output of a command (the third sed in this case) and write it to a file. In all this command
```
cat Example.txt | sed s/$'\xc5\xbd'/\'/g | sed s/$'\xc2\x94'/\"/g | sed s/$'\xc2\x85'/.../g > Example2.txt
```runs 4 separate programs chained together with the output of one feeding into the input of the next, and the last one writing to another file. In fact it could be shortened because sed can be told to read directly from a file rather than the default standard input, so we could do this:```
sed s/$'\xc5\xbd'/\'/g Example.txt | sed s/$'\xc2\x94'/\"/g | sed s/$'\xc2\x85'/.../g > Example2.txt
```but I felt that showing you two different ways to use sed might just confuse you to start with.

It's probably best to google for a good explanation of sed. The manual that you see with the command **man sed** is rather dry, and without better tutorials found by google, I probably still wouldn't know how to use sed now.

This way of chaining programs together is a very unix-like way of doing things. It's very powerful but there's nothing really like it in windows so not that many people know about it.

Sed can also do in-place file editing so another possible solution might be a script that goes something like:
```
#!/bin/sh
filename=Example.txt
sed -i s/$'\xc5\xbd'/\'/g $filename
sed -i s/$'\xc2\x94'/\"/g $filename
sed -i s/$'\xc2\x85'/.../g $filename
```

---

### Post by sopadeajo on 2009-09-30
> **StuartN said:**
> Sed edits a stream and the argument s/pattern1/pattern2/ means find pattern 1 and substitute with pattern 2. The final g (s/p1/p2/g) means global, i.e. every occurrence of p1 is replaced with p2.

The first call **sed s/$'\xc5'$'\xbd'/\'/g** is looking for a pattern consisting of the hex byte c5 ($'\xc5') followed by the hex byte bd and replacing both bytes with an apostrophe (\'). This is piped through successive calls to sed to replace the other two-byte accented characters with an appropriate substitute.

Thanks, Stuart.It is clearer now. 
(s/p1/p2/g) Why pattern p1 is two hexadecimal bytes and p2 is written as it is: '  ?
Where to find which character is each hexadecimal value?

The other problem were the " and the ... represented by (different, i think) squares.

And why gedit is unable to correct this (automatically) since all other accents and characters are correctly shown as well as the EOL and the format of the lines ?

We can even imagine a software detecting that the language is French or English or Spanish and a few more languages (must not ne too hard) and then detecting by the relative frequency of the apostrophe (as an example) and its situation at the beginning of words, that it is an apostrophe and then showing the right character. It would be  more difficult for " and ... but not impossible .

And now if i correct all my texts to be correctly viewed by gedit i am afraid there will be a problem back when i view then back with Notepad on Windows, since i want to use them with both systems.

Will Open Office word processor be able to correct these texts by itself (not using the sed capabilities in Terminal) ?  If so what should i have to do (transform the text to RTF, or what other operations can be done with Word Open Office?
Edited:
And what is the meaning of the dollar symbol in this case?
Unix seems to have the $ everywhere, in Terminal, for example. And it is  a bad symbol since it is the symbol of money (a true paradox for a free software in Linux) and more than this it is the money symbol of only a very few countries (canada, usa, australia,..)
Nobody ever thought in changing this sign/character for a more neutral and universal one?

---

### Post by sopadeajo on 2009-09-30
> **The Cog said:**
> \x94'/\"/g | sed s/$'\xc2\x85'/.../g > Example2.txt[/code]but I felt that showing you two different ways to use sed might just confuse you to start with.



No, it's the contrary. I have often thought (This happened with old Dos commands as well, though i am not a programmer and never worked  (nor even played) really with Dos) that the command line was too arbitrary (had a too arbitrary syntax) at first sight. When working with it (professionally) you might quickly get used to it, but not as an amateur.
Showing several ways to do a task lets you understand more on how the commands work, in my opinion.
Your explanation is good, thanks.

---

### Post by The Cog on 2009-10-01
> (s/p1/p2/g) Why pattern p1 is two hexadecimal bytes and p2 is written as it is: ' ?
Where to find which character is each hexadecimal value?

Since we don't know what character coding notepad is using, we have to look at the actual file contents to figure out what sequence in the file needs replacing. In this snippet in the output from **hd Example.txt** there are two odd looking sequences:
```

00000010  69 20 6c 65 20 64 61 6e  67 65 72 20 64 c5 bd 75  |i le danger d..u|
00000020  6e 20 63 75 6c 74 65 20  65 78 63 65 73 73 69 66  |n culte excessif|
00000030  20 64 65 20 6c 61 20 70  65 72 73 6f 6e 6e 61 6c  | de la personnal|
00000040  69 74 c3 a9 20 64 65 20  6c 61 20 70 61 72 74 20  |it.. de la part |
```
You can read the hex dump OK I hope? The first long number is an address - how far into the file the line is. Then there is a list of 16 byte values, then on the right is those 16 bytes shown as text (or a dot if that byte isn't an ASCII value).

On the first line above, near the end, between "d" and "u" is the hex pair "c5 bd". So they need replacing with whatever should be there - an apostrophe. But an apostrophe "'" has special meaning to the command interpterer so that you either have to type "\'" or put its hex value "\x27" on the command line.

The last line has bytes c3 a9 near the start of the line, after "it". I don't think we've discussed this pair yet.

---

### Post by inso_741 on 2010-05-26
isn't there a text editor that is compatible with windows available for linux?

---

