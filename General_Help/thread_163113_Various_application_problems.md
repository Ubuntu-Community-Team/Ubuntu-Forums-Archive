---
title: "Various application problems"
date: 2006-04-20
forum: General Help
---

### Post by Rhapsody on 2006-04-20
Not sure if this is the place, but after waiting three days on the amaroK forums for a response, they decided to refer me back here (distro-specific problem aparrently, how helpful of them). But while I'm making a topic, I figure I might as well state all of the application problems and queries I can think of right now.

**_amaroK_**
Very simple here. It won't play MP3s. This problem has its [own entry](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10) in the amaroK wiki of course, with instructions on how to make it work. Which I followed. The part with Adept worked fine, but typing the command listed into Konsole produced the following:

Reading package lists... Done
Building dependency tree... Done
Package libmad0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmad0 has no installation candidate

My best guess is that I have to uncomment some more lines in Adept, but I've no idea which. For further information, consult the [first topic](http://amarok.kde.org/component/option,com_simpleboard/Itemid,57/func,view/id,11918/catid,8/) I made over at the amaroK forums.

**_Mozilla Firefox_**
I've downloaded it, extracted it, but how do I start it? Seriously, I've been a Windows user for ten years, I usually just find the .exe file and it fires up. Which of the multitude of files in this folder is actually the browser?

**_Irssi_**
I like the looks of this over Konversation, but what exactly do I download? I know Ubuntu and Debian share more than a few similarities, but will the Debian download just extract and run?

**_VLC media player_**
As with Irssi really. In fact, am I likely to be installing a lot of stuff that is actually labelled as being for Debian?

I'm sure I'll have more stuff to ask in the future, but that's all I can really think of for now.

---

### Post by Al3xanR0 on 2006-04-20
[QUOTE=Rhapsody]Not sure if this is the place, but after waiting three days on the amaroK forums for a response, they decided to refer me back here (distro-specific problem aparrently, how helpful of them). But while I'm making a topic, I figure I might as well state all of the application problems and queries I can think of right now.

**_amaroK_**
Very simple here. It won't play MP3s. This problem has its [own entry](http://amarok.kde.org/amarokwiki/index.php/MP3_on_Ubuntu_5.10) in the amaroK wiki of course, with instructions on how to make it work. Which I followed. The part with Adept worked fine, but typing the command listed into Konsole produced the following:

Reading package lists... Done
Building dependency tree... Done
Package libmad0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libmad0 has no installation candidate

My best guess is that I have to uncomment some more lines in Adept, but I've no idea which. For further information, consult the [first topic](http://amarok.kde.org/component/option,com_simpleboard/Itemid,57/func,view/id,11918/catid,8/) I made over at the amaroK forums.

**_Mozilla Firefox_**
I've downloaded it, extracted it, but how do I start it? Seriously, I've been a Windows user for ten years, I usually just find the .exe file and it fires up. Which of the multitude of files in this folder is actually the browser?

**_Irssi_**
I like the looks of this over Konversation, but what exactly do I download? I know Ubuntu and Debian share more than a few similarities, but will the Debian download just extract and run?

**_VLC media player_**
As with Irssi really. In fact, am I likely to be installing a lot of stuff that is actually labelled as being for Debian?

I'm sure I'll have more stuff to ask in the future, but that's all I can really think of for now.[/QUOTE]


One question? Have you updated your sources.list? If not go [here]("http://www.ubuntulinux.nl/source-o-matic") you will find that some of your problems namely libmad0 will go away. You should be able to ```
apt-get install firefox Konversation vlc 
``` but if you insist .bin will be the equiv to .exe. If you have located open the command line in the directory where it resides then ```
./firefox
``` (the .bin file)

---

### Post by localzuk on 2006-04-20
All of those files are in the repositories. Take a look at [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) and [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) to solve 2 of the issues.

After you have ran through both of the above, fire up Adept and you should be able to install all the applications you need.

If you want a quick 'how to' sort of guide to linux, take a look at [http://help.ubuntu.com/](http://help.ubuntu.com/) it contains all the official documentation and should be able to point you in the right direction. Other, docs are available from the wiki at [https://wiki.ubuntu.com](https://wiki.ubuntu.com)

---

