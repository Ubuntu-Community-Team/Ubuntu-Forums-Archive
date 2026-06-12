---
title: "Kanji in Ubuntu bash 10.04 x86 Minimal"
date: 2011-10-05
forum: General Help
---

### Post by preguntom on 2011-10-05
I need to see kanji on my terminal command, I have now installed this
apt-get install ttf-takao-mincho 
apt-get install ttf-takao
apt-get install ttf-dejima-mincho ttf-hanazono ttf-kochi-mincho ttf-vlgothic ttf-mikachan

Added to /etc/apt/sources.list
deb [http://archive.ubuntulinux.jp/ubuntu-ja](http://archive.ubuntulinux.jp/ubuntu-ja) hardy/

after 
apt-get install ubuntu-ja-keyring
apt-get update
mkdir /usr/share/fonts/truetype/msjapanesefonts
cd /usr/share/fonts/truetype/msjapanesefonts
wget [http://www.linux.ryukent.co.uk/download/msgothic.zip](http://www.linux.ryukent.co.uk/download/msgothic.zip)
wget [http://www.linux.ryukent.co.uk/download/msmincho.zip](http://www.linux.ryukent.co.uk/download/msmincho.zip)
unzip msgothic.zip
rm msgothic.zip
unzip msmincho.zip
rm msmincho.zip -y

fc-cache -f -v
-bash: fc-cache: command not found
[URL="https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM"]
https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM[/URL]

came up here, then do not know how to follow? :(

---

### Post by AskTell on 2011-10-05
fc-cache command requires fontconfig

apt-get install fontconfig

---

### Post by preguntom on 2011-10-05
I was able to empty the cache, which most would fail me to do to see kanji in bash :)

---

### Post by AskTell on 2011-10-05
So does that mean you were successful? it works? I'm having a hard time deciphering your reply..:-k

---

### Post by preguntom on 2011-10-26
I cannot see kanjis of unrar files in bash. :(
If I can see them in utorrent. but it is the only program :confused:

---

### Post by AskTell on 2011-10-26
.

---

### Post by preguntom on 2011-10-26
sorry sir :rolleyes:, perhaps not understood, why use a translator.
 the problem is global.
 Not a problem with winrar. or other progam.
 BASH where I need to see kanji ):P

---

### Post by AskTell on 2011-10-28
have your tried this link? 
[http://ubuntuforums.org/showthread.php?t=975144](http://ubuntuforums.org/showthread.php?t=975144)

I found it linked at the bottom of this link
[https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM)

Japanese Supportyou're probably already using
 
[LIST]
[*] Website: [http://www.ubuntulinux.jp/ ]("http://www.ubuntulinux.jp/")
[*] Forums: [http://forum.ubuntulinux.jp/ ]("http://forum.ubuntulinux.jp/")
[*] Wiki: [https://wiki.ubuntulinux.jp/ ]("https://wiki.ubuntulinux.jp/")
[*] IRC: #ubuntu-jp on irc.freenode.net
[*] Mailing list: [ubuntu-jp@lists.ubuntu.com ]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-jp")
[/LIST]

---

