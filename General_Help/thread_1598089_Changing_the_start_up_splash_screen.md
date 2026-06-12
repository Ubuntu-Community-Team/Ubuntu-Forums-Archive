---
title: "Changing the start up splash screen"
date: 2010-10-16
forum: General Help
---

### Post by Jonny87 on 2010-10-16
I know its not a major issue but is there a way of changing the startup splash screen?

What ever way people recommend, I'd like to know if theres a user friendly way i.e an app that will do it, so that I can tell my Dad how to do it on his machine as he's not to technically inclined.

---

### Post by dcstar on 2010-10-16
> **Jonny87 said:**
> I know its not a major issue but is there a way of changing the startup splash screen?

What ever way people recommend, I'd like to know if theres a user friendly way i.e an app that will do it, so that I can tell my Dad how to do it on his machine as he's not to technically inclined.

[http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by sirrab on 2010-10-16
I used Ubuntu Tweak to do it. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Easy as :)

---

### Post by Jonny87 on 2010-10-16
> **dcstar said:**
> [http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/quick-tipplymouth-themes-in-ubuntu-10-04-lucid-lynx.html)

That link helped. Thanks.

> **sirrab said:**
> 	I used Ubuntu Tweak to do it. 

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Where in Ubuntu tweak? I have that installed and seem to find that option.

---

### Post by brickkiln on 2010-10-16
HELP. I am new at this and just joined the ubuntu forums. I have a a question - but where do I  pose it where do I type it in. I apologise to the readers of this thread but I could find no other place. Am I stupid? All I want to do is to find out how to uninstall iBario from my mozilla firefox browser. I would have thought that would be easy... having written this I have no idea where I might receieve any answer given.  HELP

---

### Post by garvinrick4 on 2010-10-16
> **Jonny87 said:**
> I know its not a major issue but is there a way of changing the startup splash screen?

What ever way people recommend, I'd like to know if theres a user friendly way i.e an app that will do it, so that I can tell my Dad how to do it on his machine as he's not to technically inclined.
go into synaptics or Software center and choose what plymouth graphic themes you want (that is an app), install them.
Open a terminal and.
```
sudo update-alternatives --config default.plymouth
```then choose which one by number: then run this to update:
```
sudo update-initramfs -u
``````
sudo apt-get shutdown -r now

```You have installed new graphic splash screens
you have made a selection
you have updated initramfs
you have rebooted;

---

### Post by dcstar on 2010-10-16
> **Jonny87 said:**
> 
...........
Where in Ubuntu tweak? I have that installed and seem to find that option.

Nowhere at all in Ubuntu Tweak, some people just do not understand the difference between the **boot Splash** screen and the** Login** screen.

---

### Post by Jonny87 on 2010-10-17
> **dcstar said:**
> Nowhere at all in Ubuntu Tweak, some people just do not understand the difference between the **boot Splash** screen and the** Login** screen.

Yea thats what I thought. Tweak was the 1st place I looked for a user friendly app to do the job. So I thought I'd ask here in the forums.

---

### Post by Megaptera on 2010-10-17
Is Plymouth Manager any help?

[http://en.wikipedia.org/wiki/Plymouth_(software](http://en.wikipedia.org/wiki/Plymouth_(software))

---

### Post by krishnandu.sarkar on 2010-10-17
> **brickkiln said:**
> HELP. I am new at this and just joined the ubuntu forums. I have a a question - but where do I  pose it where do I type it in. I apologise to the readers of this thread but I could find no other place. Am I stupid? All I want to do is to find out how to uninstall iBario from my mozilla firefox browser. I would have thought that would be easy... having written this I have no idea where I might receieve any answer given.  HELP

Go to [http://ubuntuforums.org/index.php](http://ubuntuforums.org/index.php)
Find the appropriate catagory and go to the catagory
Select New Post
Enter an appropriate subject and write the query in editor.
Submit.

---

### Post by Jonny87 on 2010-10-17
Ok, I had it going, I really liked the solar plymouth screen, and now I've just done an upgrade to 10.10 and it's gone. I try to reset it again using the same method, it shows the extra themes there but when I reboot it's still on the default splash. 

So whats different?

---

### Post by Megaptera on 2010-10-17
The author of the app has a thread here  [http://ubuntuforums.org/showthread.php?t=1595812](http://ubuntuforums.org/showthread.php?t=1595812) and I'm sure you can get help there as all I can guess is it doesn't like 10.10 - but I don't know!!

---

### Post by Jonny87 on 2010-10-17
> **Megaptera said:**
> The author of the app has a thread here  [http://ubuntuforums.org/showthread.php?t=1595812](http://ubuntuforums.org/showthread.php?t=1595812) and I'm sure you can get help there as all I can guess is it doesn't like 10.10 - but I don't know!!

I was doing it at the command line, it still wouldn't work. However when the command line didn't work, I tried that app but that didn't work either. So if the command line won't do the job when it did it earlier today on 10.04, whats changed in 10.10?

*I'd like to point out though that this seems to be only issue I've had so far with 10.10, not that the plymouth splash is very important, I just like to make my system customized.*

---

