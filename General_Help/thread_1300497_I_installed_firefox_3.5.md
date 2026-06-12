---
title: "I installed firefox 3.5"
date: 2009-10-25
forum: General Help
---

### Post by kixome on 2009-10-25
from the firefox site, copied it to /usr/share/firefox/ 

can someone give me the command to make it where i can run it by typing firefox at the cli? any help appreciated.

---

### Post by kixome on 2009-10-25
also copied to /usr/bin

---

### Post by Dark_Stang on 2009-10-25
Edit: nevermind...

---

### Post by kixome on 2009-10-25
thanks, i appreciate it

---

### Post by kixome on 2009-10-25
thanks, i appreciate that

---

### Post by Dark_Stang on 2009-10-25
Heh, sorry. You need to make a simlink in /usr/bin.

I had a brain fart. I thought it was /usr/lib for some reason then I realized I was wrong.

---

### Post by kixome on 2009-10-25
oh, i thought you were maybe being purposely rude.(another reason text isn't as good as real life conversation) Thank you kind sir for your reply!

---

### Post by kixome on 2009-10-25
i did that and now i get this
Cannot find Firefox runtime directory. Exiting.
any ideas, if you BF again i'll know what you mean

---

### Post by lidex on 2009-10-25
> **kixome said:**
> from the firefox site, copied it to /usr/share/firefox/ 

Not sure why you'd go that route. Easy enough to install from the repositories then run with command "firefox-3.5"

---

### Post by kixome on 2009-10-25
I got it, you were right, for anyone else that wants firefox 3.5 not shiretoko "because some sites don't accept it do this:

make sure you have downloaded and unzipped firefox from the tar.bz2 at the firefox site

#sudo apt-get autoremove firefox firefox-gnome-support
sudo cp -r /home/username/Desktop/firefox /usr/share/firefox
sudo ln -s /usr/share/firefox/firefox /usr/bin/firefox
sudo chmod+x /usr/share/firefox/firefox
and you will have actual firefox 3.5

---

### Post by kixome on 2009-10-25
now any launcher you create woth the word firefox as the command will work.

---

### Post by kixome on 2009-10-25
if it doesn't then sudo chmod 777 /usr/share/firefox/firefox

---

### Post by kixome on 2009-10-25
> **lidex said:**
> Not sure why you'd go that route. Easy enough to install from the repositories then run with command "firefox-3.5"

because I want firefox, not shiretoko, because some sites reject it, and furthermore I use debian because it is faster on this system!

---

### Post by kixome on 2009-10-25
and even if i did use ubuntu it would be lts, and 8.04 doesn't nor does 9.04 have it in the officially supported repositories. Not to be a wiseacre but yeah, to be one.

---

### Post by lovinglinux on 2009-10-25
Are you discussing with someone else or with your alter ego? It seems to me most of the replies are form the OP or I'm missing something? :)

Anyway, you method seems weird to me.

This is the way Psychocats recommends installing manually:

```
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-*.tar.bz2 -C /opt
rm firefox-*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
```

The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm.

---

### Post by kixome on 2009-10-29
might be from the OP, but I will argue my point when I am asked a question.

---

### Post by ElSlunko on 2009-10-29
To make shiretoko or minefield work with some sites (like facebook for the chat feature) you can enter

about:config

into the address bar and do a search for shiretoko or minefield (or the codename for 3.6, it escapes me at the moment). Double click the result and change the value to "firefox" without quotes.

---

