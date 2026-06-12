---
title: "Installing Songbird?"
date: 2010-08-25
forum: General Help
---

### Post by xMP44x on 2010-08-25
I'd like to install Songbird on my Ubuntu installation, as I have used it previously with my Windows 7 install. It is a media player I've had experience with and like using as it allows me to scrobble to Last.FM (although Rhythmbox has this functionality), but most of all the interface is familiar. Unfortunately the Songbird team have ended the development of the Linux version. I've managed to find a version of it on the internet which is in a .tar.gz file extension - something I've never encountered. If someone has any ideas as to how I could possibly use this, it'd be greatly appreciated. I'm *loving* Linux, and I just want this one familiar program - if someone has an installer for it on their machine I'll take it :P

However, if nobody has an installer I'd appreciate an explanation as to how I should approach the .tar.gz extension. Thanks everyone! :)

---

### Post by scorp123 on 2010-08-25
Songbird is Mac OS X only now. They dropped all Linux support.

[http://mozillalinks.org/wp/2010/04/songbird-for-linux-dropped-nightingale-picks-up/](http://mozillalinks.org/wp/2010/04/songbird-for-linux-dropped-nightingale-picks-up/)

---

### Post by xMP44x on 2010-08-26
Sadly, I can't even find Nightingale for Ubuntu, as the web page seems to be down. I tried searching for its previous name of Lyrebird as well, but with no success. If it's not possible to even get Songbird or a derivative of it, could someone recommend me a media player with a familiar interface from Windows?

---

### Post by silverglade00 on 2010-08-26
For the tar.gz, you should be able to right click it and choose open with Archive Manager. That will open it up much like a ZIP file in WinZip. THen you extract the whole thing to a folder in your home folder and follow the instructions in the README file that should be there.

---

### Post by scorp123 on 2010-08-29
> **xMP44x said:**
>  recommend me a media player with a familiar interface from Windows? I personally use Exaile ... it looks similar enough to iTunes IMHO, so if you can operate iTunes then Exaile shouldn't be too much trouble.

Exaile is in the repos, so you can easily get it via the Synaptic package manager: ***System > Administration > Synaptic Package Manager***
...  then search for "exaile" and click install.

Or you simply open a terminal and quickly type this code here (waaaaay faster than having to click through menus):
```
sudo apt-get update && sudo apt-get install exaile
```

If it asks for a password: That's your password. And nope, it does not ever echo anything back, e.g. when you type there won't be any feedback, no stars, no question marks, nothing ... Just type your password blindly and hit the 'Enter' key! ... if it did work you should see some messages flush over the screen and in the end it will ask you for permission to proceed with the download and installation ... just hit "y" and the program will get downloaded and installed. You will then easily find it in the "Sound & Video" menu ...

---

### Post by polardude1983 on 2010-08-29
I found a linux version of songbird its only 1.7.3 but anyways take a looksie

[http://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds#Linux]("http://wiki.songbirdnest.com/Developer/Articles/Builds/Contributed_Builds#Linux")

---

### Post by braja74 on 2010-10-10
Try Jajuk.  I used and for the most part loved songbird (memory was an issue). Took me a long time to find something that was comparable.

---

