---
title: "Speech Control Like Windows 7 Speech Recognition"
date: 2012-06-12
forum: General Help
---

### Post by zoffix on 2012-06-12
Hey,

Does Ubuntu have whole-computer voice control capability?

I've been using Ubuntu ever since Edgy, and never looked back on Windows until... I've tried Windows 7 with its Speech Recognition Software, and absolutely felt in love with it.

I often have pains in my hands, and controling the computer with voice is invaluable to me.

I've found some things with Google (like sphinx), of course, but I wasn't even sure how to launch any of it, never mind using it. Gnome Voice Control seems like four commands to manipulate windows, but I'm looking for something to type text, primarily.

Has anyone managed to setup at least some for of voice recognition on Ubuntu? At least something where you couldd dictate text into an active window?

Thanks in advance.

---

### Post by Ubun2to on 2012-06-12
Well, there appear to be none in the Software Center at the moment.
There is an entire [page on Wikipedia]("http://en.wikipedia.org/wiki/Speech_recognition_in_Linux") dedicated to this kind of software.
I wish I could try this stuff out myself, but I don't have a microphone.
This is a good idea for future versions.

---

### Post by irv on 2012-06-12
I don't know if this would be worth looking at:
[http://www.em-t.com/Free-Voice-Recognition-Software-For-Linux-s/222.htm]("http://www.em-t.com/Free-Voice-Recognition-Software-For-Linux-s/222.htm")

---

### Post by RimSide on 2012-06-24
I have tried vedics. Apparently it is supposed to be good, but I have not been able to figure out how to use it very well

---

### Post by UbuKunubi on 2012-07-19
Try this: [http://ubuntuspeechinput.zymichost.com](http://ubuntuspeechinput.zymichost.com)

---

### Post by LordEager on 2012-07-20
There are several ways t obtain speech recognition on Linux, but noway is just comparable with Dragon Natural Speaking for Win that is much superior to Win7SR...
The main lack is that usually linux SR do not have the capacity to train according to the user's voice, but have predefinied acoustic libraries, so in order to use them you have to learn the right pronunciation and intonation of the commands which is not a very easy task to accomplish...
I know there is an ubuntu specifically SP that is work in progress in development stage which promises to be the top linux SR, it's called Speech Controller and can be found and tested by adding this repo ppa:speechcontrol-devel/unstable .
It's still at early devel stage so 99% won't work and you won't be able to end the wizard.
The main question is how is it possible that the first SR on linux started to be developed about 10 years ago and now in 2012 there is still not a real alternative to win SR on linux... Sphinx which is one of the best SR engines Open Source has reached the version 4 entirely based on Java and promises to be good... I can suggest you however 2 softwares to try, the first is Perlbox Voice which you can find on the relative website, in order to work you need to download the .deb packets sphinx2.bin libsphinx2 and the acoustic libraries... The fact that it uses sphinx2 makes it evident that is an old project... In order to make it work you need to install Tk perl components with "cpan -i Tk" it's a long compiling and install and sometimes fails, so it's reccomended to compile and install it wit --force-install option .
Perlbox Voice works with oss not with ALSA, so you have to download alsa-oss compatibility packet and start it by typing "aoss perlbox-voice".
The most modern alternative i found so fare working is called speechlion , it's based on sphinx4 and needs sphinx4 and Java JDK 6+ to work plus some other components which are listed on speechlion site... Actually it works fine with ALSA but it's only in english /american and with my built-in mic it seems like it understands one command on ten and some commands refuses totally to work... However it shows sphinx4 could be a good start, it seems to work fine as browser firefox controller i'v been able to go back and to open new tabs...
I am going to test Dragon Natural Speaking with wine but on Wine HQ it seems it has almost a null compatibility and when it works it's confined to wine apps, so totally unuseful... I hope someone else can update this thread with his experiences, i think the lack of a SR in linux nowadays is a great missing, especially for the ones with accessibility problems...

EDIT: I have just succesfully installed and am running Dragon Naturally Speaking 11 premium with Wine 1.4 on Mint 13 KDE (based on ubuntu 12.04)... It works flawlessly, dragonpad dictature is almost perfect and the great thing of this software is that it improves and learns day by day by listening to your voice... The fact remains that it seems impossible to use it to control Ubuntu tasks, i will check and see if there is a way to export the commands... it would be great.

Note: it uses a lot of RAM, it works but a bit slow for dictature on an Atom 1.66 Ghz 1Gb Ram DDR2, 2Gb RAM memory are reccomended.

EDIT2: i found the app that exports command from wine to linux, it's called platypus, that's great !

---

