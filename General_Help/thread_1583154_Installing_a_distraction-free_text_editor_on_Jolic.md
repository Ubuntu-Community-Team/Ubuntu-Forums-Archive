---
title: "Installing a distraction-free text editor on Jolicloud"
date: 2010-09-27
forum: General Help
---

### Post by shellpadawan on 2010-09-27
*For the sake of understanding and clarity, I will adress the Ubuntu community as if it were a god*

I come to thee at the end of my rope for I have tried to install a distraction free text editor named [focuswriter]("http://gottcode.org/focuswriter/"), but I have been temted many times, and such an endeavor proved to be more of a distraction to me than any text editor of the world.

I know that I have my flaws, for instance, I run Jolicloud on my Eee PC 1000H, and as you know, O Knowledgable One, Jolicloud is a Jaunty 9.04 based OS.

I changed the sources.list file, and added the respository needed, then I learnt what was a PPA key and fed it to my repository file as I learnt [here]("https://launchpad.net/~gottcode/+archive/gcppa/").
Do tell me now, o Father, why is it that when even after my daily update my computer still doesn't recognize the pckg focuswrite, why can it not find it ?

---

### Post by andrewthomas on 2010-09-27
> **shellpadawan said:**
> *For the sake of understanding and clarity, I will adress the Ubuntu community as if it were a god*

I come to thee at the end of my rope for I have tried to install a distraction free text editor named [focuswriter]("http://gottcode.org/focuswriter/"), but I have been temted many times, and such an endeavor proved to be more of a distraction to me than any text editor of the world.

I know that I have my flaws, for instance, I run Jolicloud on my Eee PC 1000H, and as you know, O Knowledgable One, Jolicloud is a Jaunty 9.04 based OS.

I changed the sources.list file, and added the respository needed, then I learnt what was a PPA key and fed it to my repository file as I learnt [here]("https://launchpad.net/%7Egottcode/+archive/gcppa/").
Do tell me now, o Father, why is it that when even after my daily update my computer still doesn't recognize the pckg focuswrite, why can it not find it ?
If it is based on jaunty then the ppa will not work because there are no packages published for jaunty.

---

### Post by shellpadawan on 2010-09-27
There is a section for older OS though, when you click on "technical details about this PPA".



I got the correct repository and key. And you are telling me that I can't install this program because I'm running on a Jaunty based OS ?
Is there absolutely no way for me to run it ?

---

### Post by andrewthomas on 2010-09-27
That screen is a standard pop-up that is loaded for every ppa regardless. 

 You could try and change the line referring to that ppa from jaunty to karmic and see if the program works ( although I make no promises that it will.)

---

### Post by Zill on 2010-09-27
shellpadawan:  You could take a look at [PyRoom]("http://pyroom.org/").  It's in the repos.
```
sudo apt-get install pyroom
```

---

### Post by shellpadawan on 2010-09-27
When I change the line from jaunty to karmic, I get an unsatisfied dependancy with libhunspell-1.2.0, actually, here's what it says:

```
[COLOR="Green"]Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Certains paquets ne peuvent être installés. Ceci peut signifier
que vous avez demandé l'impossible, ou bien, si vous utilisez
la distribution unstable, que certains paquets n'ont pas encore
été créés ou ne sont pas sortis d'Incoming.
L'information suivante devrait vous aider à résoudre la situation*: 

Les paquets suivants contiennent des dépendances non satisfaites*:
  focuswriter: Dépend: libhunspell-1.2-0 (>= 1.2.8) mais 1.2.6-1ubuntu2 devra être installé[/COLOR]

```

I know, it's in french, but still, libhunspell 1.2.8 can't be installed apparently...

anyway, in the meantime, I already got pyroom, which is good enough even though the text needs some editing after in Open Office.
I just wanted focuswriter to work, but I guess it's not going to be easy,if it is anything at all.

---

### Post by andrewthomas on 2010-09-28
> **andrewthomas said:**
> That screen is a standard pop-up that is loaded for every ppa regardless. 

 You could try and change the line referring to that ppa from jaunty to karmic and see if the program works ( **although I make no promises that it will**.)
I kind of thought that you would run into some dependency issues.

You could get the source and compile your own .deb

---

### Post by shellpadawan on 2010-09-28
I'm afraid in that case,I'm too much of a shell padawan to do that.
It's just very frustrating.

I have fully moved to Linux (at least a linux based OS) andI'm proud of it, but at every corner arises a new challenge. Some I can manage, and I learn from them, but most of the time the simplest thing like writing becomes a *pensum*.

Thank you andrewthomas for your kindness and availability, I move to pyroom which is doing the job nonetheless. 

I know that the beauty of a linux based environment is that you can bend it to your will, but it seems I lack the will to do so.

:(

---

### Post by tresjolie on 2010-10-12
> **shellpadawan said:**
> I'm afraid in that case,I'm too much of a shell padawan to do that.
It's just very frustrating.

I have fully moved to Linux (at least a linux based OS) andI'm proud of it, but at every corner arises a new challenge. Some I can manage, and I learn from them, but most of the time the simplest thing like writing becomes a *pensum*.

Thank you andrewthomas for your kindness and availability, I move to pyroom which is doing the job nonetheless. 

I know that the beauty of a linux based environment is that you can bend it to your will, but it seems I lack the will to do so.

:(

There is yet hope.  In the same boat as you, bemoaning the fact that I couldn't get this cross-platform program to run on my Jolicloud...it occurred to me that I didn't have to run it as a Linux app if I used WINE.  I knew from using Focuswriter on Windows that the download is just a .zip file you extract to a folder, everything the program needs in one place, double-click the executable and you're up and running.  

I added WINE through the Jolicloud apps, then downloaded and extracted the .zip into its own folder, double-clicked the executable and WINE automatically opened it.  I did find that I needed to take the program out of fullscreen (F11) in order to change the preferences and add a theme, but it works well otherwise so far.

Not exactly Linux-pure, but it works for me.  Coupled with Dropbox for document syncing...win!

---

