---
title: "I get stuck trying to install internet explorer"
date: 2009-08-12
forum: General Help
---

### Post by Jo Crawshaw on 2009-08-12
I need Internet Explorer for a professional application. I've looked in the forum and tried following instructions about installing ies4linux but I keep getting stuck. When I try to download it I keep getting messages like 'access denied', file not found' and other frustrating things.

Please can someone with some patience for Ubuntu babies talk me through it? I have Ubuntu 9.04 and Wine 1.1.26.
Thanks.

---

### Post by JohnWesleyMethodist on 2009-08-12
> **Jo Crawshaw said:**
> I need Internet Explorer for a professional application. I've looked in the forum and tried following instructions about installing ies4linux but I keep getting stuck. When I try to download it I keep getting messages like 'access denied', file not found' and other frustrating things.

Please can someone with some patience for Ubuntu babies talk me through it? I have Ubuntu 9.04 and Wine 1.1.26.
Thanks.

[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)

 I'm no Linux guru but I'll try to help.

 That link above should take you to a place where you can download this program. I don't know anything about IES4Linux but it sounds to me from your comments that maybe the place you were attempting to download it from was having server issues or perhaps you are behind a proxy at work and your proxy server doesn't like you downloading that program?

 If you actually have the file on your computer then it sounds to me like you need to run gksu nautilus and access the program there. You hold down Alt-F2 and when the run box appears you type: gksu nautilus . Then from there you access the file that way.

---

### Post by P4man on 2009-08-12
Did you install cabextract ?
The help page there says:
"IEs 4 Linux needs two packages: cabextract and Wine."

If you don't have it, you have to install it first.

```
sudo apt-get install cabextract
```

After that, it seems rather straightforward. Just copy paste the instructions on that page line by line in to a terminal:

```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux

```

hint: to paste in a terminal, use shift+control+v

If you get stuck anywhere, paste the error here.

---

### Post by Jo Crawshaw on 2009-08-14
[COLOR=#000000]Thanks very much to P4man and JohnWesleyMethodist for your replies.[/COLOR]
 [COLOR=#000000]I've tried a combination of what you both said.[/COLOR]
 

 [COLOR=#000000]I'm using my home computer, so there shouldn't be any firewall problem, unless I've set up Firestarter wrongly.[/COLOR]
 

 [COLOR=#000000]I tried gksu nautilus but nothing shows up, so I guess it's not already on my computer.[/COLOR]
 

 [COLOR=#000000]I tried “sudo apt-get install cabextract”[/COLOR]
 [COLOR=#000000]and this is what I got:[/COLOR]
 

 [COLOR=#000000]Reading package lists... Done [/COLOR]
 [COLOR=#000000]Building dependency tree        [/COLOR]
 [COLOR=#000000]Reading state information... Done [/COLOR]
 [COLOR=#000000]cabextract is already the newest version. [/COLOR]
 [COLOR=#000000]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. [/COLOR]
 [COLOR=#000000]W: Duplicate sources.list entry [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) jaunty/main Packages (/var/lib/apt/lists/wine.budgetdedicated.com_apt_dists_jaunty_main_binary-i386_Packages) [/COLOR]
 [COLOR=#000000]W: You may want to run apt-get update to correct these problems [/COLOR]
 

 [COLOR=#000000]So I've already got cabextract, but maybe twice? Is this a problem?[/COLOR]
 

 [COLOR=#000000]I then tried “wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)”[/COLOR]
 [COLOR=#000000]and this is what I got:[/COLOR]
 

 [COLOR=#000000]--2009-08-14 11:16:32--  [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz) [/COLOR]
 [COLOR=#000000]Resolving [www.tatanka.com.br](www.tatanka.com.br)... 208.113.179.228 [/COLOR]
 [COLOR=#000000]Connecting to [www.tatanka.com.br|208.113.179.228|:80](www.tatanka.com.br|208.113.179.228|:80)... connected. [/COLOR]
 [COLOR=#000000]HTTP request sent, awaiting response... 200 OK [/COLOR]
 [COLOR=#000000]Length: 332341 (325K) [application/x-tar] [/COLOR]
 [COLOR=#000000]ies4linux-latest.tar.gz: Permission denied [/COLOR]
  [COLOR=#000000]Cannot write to `ies4linux-latest.tar.gz' (Permission denied). [/COLOR]

  	 	 	 	 	 	  On [www.tatanka.com.br/ies4linux/page/Installation](www.tatanka.com.br/ies4linux/page/Installation) in the specific instructions for Ubuntu it says you have to enable universe packages first. I have done this before and added the lines it says, and also added them substituting 'jaunty' for 'edgy' for good measure. It also says use the official winehq ubuntu package. I assume that is what I've got because it came as part of my Ubuntu system.
 

 So where next??
 
[[COLOR=#000000][/COLOR]  	 	 	 	]("http://www.tatanka.com.br/ies4linux/page/Installation")

---

### Post by bchurchill on 2009-08-14
> **Jo Crawshaw said:**
> I need Internet Explorer for a professional application. I've looked in the forum and tried following instructions about installing ies4linux but I keep getting stuck. When I try to download it I keep getting messages like 'access denied', file not found' and other frustrating things.

Please can someone with some patience for Ubuntu babies talk me through it? I have Ubuntu 9.04 and Wine 1.1.26.
Thanks.

Guaranteed alternate solution: get Windows (I know, it's painful).  You may even want to go for a dual boot if you have other windows applications you want to run.

I'm not quite sure why you need Internet Explorer in particular, but you could try changing the Default User Agent in a another browser, say Firefox (there's an add-on for this) to Internet Explorer.  This would make websites think you're using Internet Explorer, even though you are not.  I don't know if this will work for you.

---

### Post by P4man on 2009-08-14
yep you have cabextract, no problem there.

IT seems though you dont have write permission in the folder where you are trying to download the script to. thats weird, as by default if you open a terminal, you are in your homefolder, to which you should have write permissions.  You didn't  type "cd /" or something before downloading ? 

show me what you get when you type:

```
ls -la /home
```

---

### Post by SuaSwe on 2009-08-14
I may well be barking up the wrong tree here but perhaps try 'sudo wget' instead of just 'wget'?

Also, do you by any chance already have ies4linux-latest.tar.gz on your machine somewhere?

---

### Post by P4man on 2009-08-14
> **SuaSwe said:**
> I may well be barking up the wrong tree here but perhaps try 'sudo wget' instead of just 'wget'?

Also, do you by any chance already have ies4linux-latest.tar.gz on your machine somewhere?

he shouldnt have to use sudo to download something to his own homefolder, unless something else is messed up and then its worth correcting that first.

also, if the file already exists, it would just be overwritten.

---

### Post by P4man on 2009-08-14
> **bchurchill said:**
> Guaranteed alternate solution: get Windows (I know, it's painful).  You may even want to go for a dual boot if you have other windows applications you want to run. I'm not quite sure why you need Internet Explorer in particular, 

Youll find many corporations that have badly written inhouse apps that rely on IE and activeX. Running IE the way he is trying is a perfect solution (until one is in a position to fire those developers and have them make something decent :)). Installing windows just to get access to that one webapp is neither practical nor desirable. Worst case would be using virtualbox to boot windows inside linux, but the OP is doing the sensible thing. IE works fine on my ubuntu,  he just seems to have a glitch that doesnt  have anything to do with IE.

---

### Post by Jo Crawshaw on 2009-08-14
P4man you hit the nail on the head!
I had typed 'cd /' before downloading because I wanted the IE folder to be tucked neatly away rather than being in my home folder. But I did it from my home folder and it worked not problem.
Thanks so much for all your help, and thanks to the other responders too.
Now to see if the application I need works after all this...

---

### Post by P4man on 2009-08-14
> **Jo Crawshaw said:**
> P4man you hit the nail on the head!
I had typed 'cd /' before downloading 

bad idea :)
You want to write as little as possible outside your homefolder on linux. Its not for no reason you dont have permission to do so. If you want to hide a folder, just put a . in front of the name. 

That said, in this case IIRC, IE will be installed in /home/yourname/.wine/drive_c/  and so you can clean up the rest after installing.

---

### Post by Jo Crawshaw on 2009-08-14
Still not quite there.

I installed ie6 no problem and an IE window opened and I was able to access the application I need for work and it seemed to work fine. Then I closed the window when I finished. But now I can't figure out how to open an IE window again. Somewhere I saw the instruction to type '/home/jo/bin/ie6', which I have tried but the cursor in the terminal just flashes on a new line and nothing happens.

Also when I installed it I got this message:
"IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com)."
How come when the version that the Wine configuration window tells me I've got version 1.1.27?

Also if you run a programme in a terminal (eg. ie6) how do you then stop it running to get back to the prompt?

Thanks again.

---

### Post by P4man on 2009-08-14
> **Jo Crawshaw said:**
> Still not quite there.

I installed ie6 no problem and an IE window opened and I was able to access the application I need for work and it seemed to work fine. Then I closed the window when I finished. But now I can't figure out how to open an IE window again.

during the install it should have asked you to create icons in the menu or on the desktp. 

If not, ies4linux installs in ~/.ies4linux. So look there. 
In case you didnt know, ~ is your homefolder (/home/yourname) and any folder or file starting with a . is hidden. in the file manager show hidden files with ctrl+h, or through the menus

For IE6, browse further to ~/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/iexplore.exe

If you want to make a launcher have it launch:

wine " ~/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/iexplore.exe"

```
Also when I installed it I got this message:
"IEs4Linux 2 is developed to be used with recent Wine versions (0.9.x). It seems that you are using an old version. It's recommended that you update your wine to the latest version (Go to: winehq.com)."
How come when the version that the Wine configuration window tells me I've got version 1.1.27?
```

Dont worry. the script probably just misreads the wine version info.

```
Also if you run a programme in a terminal (eg. ie6) how do you then stop it running to get back to the prompt?
```

control+c in the terminal. Or close the app.

---

### Post by yennik on 2009-08-14
I have installed IE using the prescibed method in these post.  I am having a different type issue.  When I use IE it will open the page and then it flashes about 7 times or ever time I move my cursor.  Acts like it is reloading or refreshing the page.  I am on a Sony Vaio Laptop VGN NR220E.  Any ideas?

---

### Post by jeb800e on 2009-08-14
Why don't you just use a Firefox add-on which lets you access IE pages?
[URL="https://addons.mozilla.org/en-US/firefox/addon/1419"]
IE Tab 1.5.2 - Mozilla Firefox[/URL]

{Edit: IE Tab 1.5.2 is not available for Linux. Try searching the Firefox Add-Ons database for similar Add-Ons}

---

### Post by P4man on 2009-08-15
> I have installed IE using the prescibed method in these post. I am having a different type issue. When I use IE it will open the page and then it flashes about 7 times or ever time I move my cursor. Acts like it is reloading or refreshing the page. I am on a Sony Vaio Laptop VGN NR220E. Any ideas?

It does that with pages which have flash. Its a known issue. It may get a bit better if you disable desktop effects, but its annoying, but then IE on linux is a hack, I would never use it as standard browser

> **jeb800e said:**
> Why don't you just use a Firefox add-on which lets you access IE pages?
[URL="https://addons.mozilla.org/en-US/firefox/addon/1419"]
IE Tab 1.5.2 - Mozilla Firefox[/URL]

{Edit: IE Tab 1.5.2 is not available for Linux. Try searching the Firefox Add-Ons database for similar Add-Ons}

actually, you can make IETab work on linux, but only after installing IES4linux ;)

---

### Post by Jo Crawshaw on 2009-08-18
Thanks P4man. It all works now. I found the launcher icon and it's all up and running. Problem solved and new things learned on the way. Result!

---

