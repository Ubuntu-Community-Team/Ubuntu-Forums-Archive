---
title: "Move AWN ???"
date: 2009-11-04
forum: General Help
---

### Post by danill2008 on 2009-11-04
Does anybody know how I can move AWN to another position or screen? It currently stays on my other screen and I cant get it to move to my main one.

---

### Post by JugglinPhil on 2009-11-04
Do you want to move it on the screen (e.g. from the bottom to the left) or from one workspace to another? It's been a while since the last time I've used it, but I think you can change the onscreen position by simply rightclicking it and it should give you the option.

---

### Post by danill2008 on 2009-11-04
> **JugglinPhil said:**
> Do you want to move it on the screen (e.g. from the bottom to the left) or from one workspace to another? It's been a while since the last time I've used it, but I think you can change the onscreen position by simply rightclicking it and it should give you the option.

I want to move it right. I have dual-screen and now it keeps staying on the left, while my main desktop is on the right

---

### Post by JugglinPhil on 2009-11-04
Right click - 'Move' maybe?

---

### Post by danill2008 on 2009-11-04
> **JugglinPhil said:**
> Right click - 'Move' maybe?

Thnx for the info, but unfortunately that doesn't work....

---

### Post by danill2008 on 2009-11-05
Does anybody perhaps know how I move this.......its really irritating on the one screen.

---

### Post by note32 on 2009-11-05
i don't think awn can move but the cairo dock can you might want to look in to it, its just as good as awn

---

### Post by danill2008 on 2009-11-05
> **note32 said:**
> i don't think awn can move but the cairo dock can you might want to look in to it, its just as good as awn

I tried that, but for me it's not as good as AWN. Is there no way I can move it, with a command or something similar?

---

### Post by JugglinPhil on 2009-11-05
I doubt a command would work, you would only be able to switch it on or off.

---

### Post by fabounet on 2009-11-05
you could retry Cairo-Dock with the latest version (2.1.1), first you may like it now, and second you could place it anywhere you want ;-)

---

### Post by danill2008 on 2009-11-06
> **fabounet said:**
> you could retry Cairo-Dock with the latest version (2.1.1), first you may like it now, and second you could place it anywhere you want ;-)

Ok thank you, seems like ill have to do that, seeing that there is no other way to move awn. Thnx for everyones help;)

---

### Post by danill2008 on 2009-11-06
> **danill2008 said:**
> Ok thank you, seems like ill have to do that, seeing that there is no other way to move awn. Thnx for everyones help;)

I found a solution! All I had to do, was click on awn and hold alt in and at the same time drag awn to wherever I wanted to move it. Thnx for everyones help!:p

Nope, doesn't seem like a permanent solution. It keeps going back to my left screen.[URL="https://answers.launchpad.net/awn/+question/14789"]
[/URL]

---

### Post by JugglinPhil on 2009-11-06
> **fabounet said:**
> you could retry Cairo-Dock with the latest version (2.1.1), first you may like it now, and second you could place it anywhere you want ;-)
+1, I prefer Cairo as well.

---

### Post by danill2008 on 2009-11-09
> **JugglinPhil said:**
> +1, I prefer Cairo as well.

I installed and tried it...but I still prefer awn. Thnx for everyones help, looks like there's no way to move it

---

### Post by JugglinPhil on 2009-11-09
> **danill2008 said:**
> I installed and tried it...but I still prefer awn. Thnx for everyones help, looks like there's no way to move it
What is it exactly that you prefer? Not that I'm trying to convince you to use cairo, I'm just interested because I couldn't find anything about awn that I liked/found useful.

---

### Post by danill2008 on 2009-11-14
> **JugglinPhil said:**
> What is it exactly that you prefer? Not that I'm trying to convince you to use cairo, I'm just interested because I couldn't find anything about awn that I liked/found useful.

I like it's mac look and some features (This is my own personal choice)
There is nothing wrong with cairo, but I still like AWN better;)

---

### Post by JugglinPhil on 2009-11-15
Alright fair enough. Although you do get a Mac-skin with cairo as well..

---

### Post by danill2008 on 2009-11-20
> **JugglinPhil said:**
> Alright fair enough. Although you do get a Mac-skin with cairo as well..

Ok, it sounds good:)...but does it also have terminal and system monitor on it? Because thats why I prefer awn over cairo..

---

### Post by fabounet on 2009-11-20
yes to both.

---

### Post by danill2008 on 2009-11-20
Ok thnx ill try again....

---

### Post by Roasted on 2009-11-20
AWN just released a new beta version which supports horizontal positioning, which includes dual screen setups. I installed it last night. It's very solid, blows Cairo out of the water IMO (unless you're an effects junkie).

[http://ubuntuforums.org/showthread.php?t=1331413](http://ubuntuforums.org/showthread.php?t=1331413)

Since it's in Beta you have to add the PPA by doing:

System - Admin - Software Sources - Third Party Software Tab - Add - Paste this - deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) ubuntu_version main - note to replace "ubuntu_version" with jaunty, karmic, or whatever you're using.

Add it. It'll error out, something about a key. Don't worry. Then go to terminal and add the key:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5

Then at terminal run:

sudo apt-get update


If you're upgrading it from an already existent AWN install, run :

sudo apt-get update && sudo apt-get dist-upgrade



If you're installing for the first time, run :

sudo apt-get update && sudo apt-get install avant-window-navigator-trunk


Then go to preferences and adjust the horizontal positioning of the AWN dock accordingly.


By the way, have you tried Docky? Very solid and similar to AWN with only minor differences. I'm back to playing with Docky for the time being.

---

### Post by danill2008 on 2009-11-22
> **Roasted said:**
> AWN just released a new beta version which supports horizontal positioning, which includes dual screen setups. I installed it last night. It's very solid, blows Cairo out of the water IMO (unless you're an effects junkie).
 
[http://ubuntuforums.org/showthread.php?t=1331413](http://ubuntuforums.org/showthread.php?t=1331413)
 
Since it's in Beta you have to add the PPA by doing:
 
System - Admin - Software Sources - Third Party Software Tab - Add - Paste this - deb [http://ppa.launchpad.net/awn-testing/ppa/ubuntu](http://ppa.launchpad.net/awn-testing/ppa/ubuntu) ubuntu_version main - note to replace "ubuntu_version" with jaunty, karmic, or whatever you're using.
 
Add it. It'll error out, something about a key. Don't worry. Then go to terminal and add the key:
 
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
 
Then at terminal run:
 
sudo apt-get update
 
 
If you're upgrading it from an already existent AWN install, run :
 
sudo apt-get update && sudo apt-get dist-upgrade
 
 
 
If you're installing for the first time, run :
 
sudo apt-get update && sudo apt-get install avant-window-navigator-trunk
 
 
Then go to preferences and adjust the horizontal positioning of the AWN dock accordingly.
 
 
By the way, have you tried Docky? Very solid and similar to AWN with only minor differences. I'm back to playing with Docky for the time being.
 
Thank you very much....this was exactly what I was looking for!
I never heard of docky, but i'll try it;)
Thnx again for your help (and everyone else who made suggestions):)

---

