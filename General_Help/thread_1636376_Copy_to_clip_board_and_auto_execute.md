---
title: "Copy to clip board and auto execute"
date: 2010-12-03
forum: General Help
---

### Post by Bobscrachy on 2010-12-03
I have bought a cepstral Text to speech voice, but it is only usable from the command line. I want to be able to copy text from firefox and execute it automatically in the command line. Is there a way I can do that?

---

### Post by Bobscrachy on 2010-12-03
This couldn't be that hard to do. Am I asking in the wrong place?

---

### Post by stinkeye on 2010-12-03
Can"t help, but you do know there is a text to voice add-on for firefox.

---

### Post by Bobscrachy on 2010-12-03
> **stinkeye said:**
> Can"t help, but you do know there is a text to voice add-on for firefox.

There use to be one called speakit that used the windows tts engine. I was able to install cepstral and at&t's voices on windows and use it, but it isn't supported by firefox anymore. 

The only one I know of on firefox nowadays sends the text to a third party server, which converts the text to mp3 and then streams it. It's slower than using a local tts engine, and the voices are horrible. I want my irish emilie to lull me in my office chair ;)

---

### Post by stinkeye on 2010-12-03
Oh well, at least I've given you a bump or 2.
More than what emilie is giving you at the moment.
:tongue:

---

### Post by cgroza on 2010-12-03
The Paste command should work in terminal!

---

### Post by Bobscrachy on 2010-12-03
> **cgroza said:**
> The Paste command should work in terminal!

This is the main sticking point keeping me from moving over from windows. I can right click and speak anything using the local tts engine in windows. I can't do the same in linux. It looks like it use to be available in ubuntu 7, but the updates broke the kde text to speech manager and now it won't work. 

[http://www.youtube.com/watch?v=if0lWJa6jOg](http://www.youtube.com/watch?v=if0lWJa6jOg)

---

### Post by stinkeye on 2010-12-04
This blog may be of some use to you. [**_[COLOR="DarkRed"]http://www.myoutsourcedbrain.com/2010/06/free-text-to-speech.html[/COLOR]_**]("http://www.myoutsourcedbrain.com/2010/06/free-text-to-speech.html")
It describes how to use a program called **xsel** to read the selected
text in any application using a keyboard shortcut and espeak.
You may be able to adapt it to use cepstral.

I tried it with espeak and it works.
You will need to install **xsel**.
```
sudo apt-get install xsel
```

---

### Post by Habitual on 2010-12-04
GNOME text-to-speech library (Cepstral swift engine support)

in package gnome-speech-swift

---

### Post by Bobscrachy on 2011-05-21
> **Habitual said:**
> GNOME text-to-speech library (Cepstral swift engine support)

in package gnome-speech-swift

I don't know enough about linux to get it to work.

---

### Post by Bobscrachy on 2011-05-22
Is there a way to use the clipboard to execute a shell script? Every time a user would copy something, the text would become a variable which would signal a shell script to execute.

---

### Post by dwhitney67 on 2011-05-22
No.

---

### Post by Bobscrachy on 2011-05-22
> **dwhitney67 said:**
> No.

Are you being serious, or being a jackass? I can't tell. 

I've been trying to figure out how to run my cepstral Text to Speech engine by mouse click on the desktop.

---

### Post by uRock on 2011-05-22
Duplicate threads merged.

---

### Post by katykat on 2011-05-23
> **Bobscrachy said:**
> Is there a way to use the clipboard to execute a shell script? Every time a user would copy something, the text would become a variable which would signal a shell script to execute.


I think you are asking the wrong question:

It should rather be if there is a way to have a shell scipt poll the clipboard and parse its contents into your app, preferably via a pipe. 

There is a tool to do this already, BUT... it is a Perl module, and would require spending a bit of time learning the best scripting language ever devised. 

[http://search.cpan.org/~king/Clipboard-0.09/lib/Clipboard.pm](http://search.cpan.org/~king/Clipboard-0.09/lib/Clipboard.pm)

---

### Post by dragonfly41 on 2011-05-23
**[COLOR=DarkSlateGray]Autokey[/COLOR]** should be able to do that .. link script to a hot key ..

there is an example clipboard script in Autokey Sample Scripts

"Abbreviation from selection" .. which needs only a Hotkey to be set.

You can adapt this.

---

