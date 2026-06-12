---
title: "*N00b* Need help installing firefox"
date: 2006-02-11
forum: General Help
---

### Post by DannyX0 on 2006-02-11
I just moved from Windows to Kubuntu Linux
I downloaded firefox from their site and I got this file:
firefox-1.5.0.1.tar.gz
how do I extract and run Firefox?
Please help.

---

### Post by aysiu on 2006-02-11
I'd advise installing Firefox 1.0.7 first:

1. Alt-F2
2. ```
konsole
```
3. ```
sudo apt-get update
sudo apt-get install firefox
```

Then, follow these instructions to get 1.5 installed. You may have to modify them slightly, as the name of the .tar.gz is slightly different now.
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by DannyX0 on 2006-02-11
ok, thanks alot.
It really helps.
So, why would that older version be better?

---

### Post by aysiu on 2006-02-11
[QUOTE=DannyX0]ok, thanks alot.
It really helps.
So, why would that older version be better?[/QUOTE] The older version isn't better. It's just that the instructions to install the newer version assume you have the older version already installed. Some of the commands won't work if you don't have the older version installed *first*.

---

### Post by KermitJr on 2006-02-11
I'd recommend Automatix for an easy install of the new firefox.

KJ

Just search the forums for automatix and it will pop up... it's a sticky.

---

### Post by DannyX0 on 2006-02-11
ok, thanks for all the help! :)

---

### Post by Neo Ex on 2006-02-11
Every day I'm reading that Automatix is not a good program: it will do some procedures which may mess up your system.
I don't think that you will have to use Automatix to install Firefox: you just have to copy and paste the commands on the wiki :)

---

### Post by aysiu on 2006-02-11
[QUOTE=Neo Ex]Every day I'm reading that Automatix is not a good program: it will do some procedures which may mess up your system.[/quote] Frankly, *anything* you install could possibly mess up your system--such is the nature of program installation. However, [this survey](http://www.ubuntuforums.org/showthread.php?t=123569) seems to indicate the overwhelming majority of Automatix users have had no problems whatsoever. It seems to be about 80% of the people who've actually used Automatix (even though it's only 50% of the people who took the survey, as some of the people who took the survey did not use Automatix).

> 
I don't think that you will have to use Automatix to install Firefox: you just have to copy and paste the commands on the wiki :) I agree with this. While Automatix may be great, it's a bit of overkill just to install Firefox. It's not that hard to copy and paste a few commands.

It's like telling someone who's on the wrong bus to buy a car rather than get off that bus and get on the correct one.

---

### Post by Neo Ex on 2006-02-11
[QUOTE=aysiu]Frankly, *anything* you install could possibly mess up your system--such is the nature of program installation. However, [this survey](http://www.ubuntuforums.org/showthread.php?t=123569) seems to indicate the overwhelming majority of Automatix users have had no problems whatsoever. It seems to be about 80% of the people who've actually used Automatix (even though it's only 50% of the people who took the survey, as some of the people who took the survey did not use Automatix).
[...][/QUOTE]
Ops... I didn't know this: I've not tried Automatix (I prefer installing programs manually), but I've always read about Automatix, and people say that it is unsafe... from the poll you posted, it seems they was wrong :)

---

### Post by Matchless on 2006-02-11
Hi,
   I have two PC's used daily with Kubuntu breezy and I just downloaded Firefox 1.5 and Thunderbird 1.5 from the Mozilla site and extracted the folder by right clicking on it, moved the folder to my home directory, created a menu item and pointed it to firebird executable in the expanded folder. Everything works, extentions installed etc. Older versions 1.07 have been uinstalled using Synaptic.
There is nothing complicated here and even noobies should find this very easy. To update to 1.5.0.1, download latest, expand and replace the folder with new one.
Hope this helps some

---

### Post by stimpack on 2006-02-11
You can just extract firefox to any directory and run it from there too, its simpler and doesnt break firefox's auto updates and autodownload of flash etc like the 'official' method does.

---

### Post by vulpine on 2006-02-11
noob here also, found these instructions on googles cache and walked me and taught me right through it

[http://72.14.207.104/search?q=cache:PkqEw8VsKnsJ:https://wiki.ubuntu.com/FirefoxNewVersion+installing+firefox&hl=en&gl=us&ct=clnk&cd=5&client=safari](http://72.14.207.104/search?q=cache:PkqEw8VsKnsJ:https://wiki.ubuntu.com/FirefoxNewVersion+installing+firefox&hl=en&gl=us&ct=clnk&cd=5&client=safari)

its a cached page from google, hope it works for ya

---

### Post by LeeUK on 2006-02-12
Hello, Just installed Kubuntu on one of my boxes.

Anyone know where I can download Firefox 1.0.7 for linux? Firefox site only has 1.5.0.1.

I prefer 1.0.7 over 1.5 still.

Thanks.

---

### Post by loser72555 on 2006-02-12
May be helpful here:   [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

---

### Post by FlakJacket on 2006-02-12
LeeUK the firefox in the repos is still 1.0.7 so if you just do 

```
sudo apt-get install firefox
``` 

it will install 1.0.7

Flak

---

