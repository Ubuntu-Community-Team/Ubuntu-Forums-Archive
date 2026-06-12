---
title: "Some questions about KDE (and Linux in general)"
date: 2006-02-12
forum: General Help
---

### Post by UbuntuStudent on 2006-02-12
Hi, I have started to use KDE as my main GUI now and I have some questions about KDE (and Linux in general):

1. I have KDE 3.4.3, how do I change to 3.5.1?

2. Gmail chat is not compatible with Konqueror, something I can do with that?

3. How do I add mplayer to Konqueror, I have some problems with movie and audio codecs as it is now.

4. How can I tribute to the communite? I want to learn something, not only to surf, play around with Gimp, chat and play games. More like making icons, backgrounds, bug reporting/fixing and so on, but I do not know anything about coding (though I am more than willing to learn) or what is needed. So any link to any pages or book suggestion that may help me getting started would be nice:) 

5. I want to make some video tutorials, can someone give me a step by step guide to how to install and set up a program that record the desktop (and sound, though not that important)?

---

### Post by gingermark on 2006-02-12
Hey,

for the first one, add the following line to your sources.list file (located in /etc/apt).

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

then, refresh your package list in Adept or run Konsole and type
```
sudo apt-get update
```

You should then be able to upgrade to KDE 3.5.1!

1 out of 5 ain't bad :)

---

### Post by atoponce on 2006-02-12
[quote=UbuntuStudent]Hi, I have started to use KDE as my main GUI now and I have some questions about KDE (and Linux in general):

1. I have KDE 3.4.3, how do I change to 3.5.1?

2. Gmail chat is not compatible with Konqueror, something I can do with that?

3. How do I add mplayer to Konqueror, I have some problems with movie and audio codecs as it is now.

4. How can I tribute to the communite? I want to learn something, not only to surf, play around with Gimp, chat and play games. More like making icons, backgrounds, bug reporting/fixing and so on, but I do not know anything about coding (though I am more than willing to learn) or what is needed. So any link to any pages or book suggestion that may help me getting started would be nice:) 

5. I want to make some video tutorials, can someone give me a step by step guide to how to install and set up a program that record the desktop (and sound, though not that important)?[/quote] 
[LIST=1]
[*]Not sure if KDE 3.5.1 is in the repos or not.  I guess it wouldn't hurt to run sudo apt-get update, and see if it shows up.
[*]Firefox renders Gmail flawlessly.  Konqueror is good, but Firefox is better.  Opera works well too.
[*]Not sure.
[*]For me, the best place to conribute is the forums itself.  If you know something that someone has a question with, jump in.
[*]I don't know of any off hand, however, I am interseted in the same thing.  If you find something out, let us know.[/LIST]

---

### Post by UbuntuStudent on 2006-02-12
So by 1 out of 5 you are saying that I should wait for next Kubuntu?

---

### Post by gingermark on 2006-02-12
[QUOTE=UbuntuStudent]So by 1 out of 5 you are saying that I should wait for next Kubuntu?[/QUOTE]
No, I meant I'd answered 1 out 5 of your questions :) Sorry....

---

### Post by UbuntuStudent on 2006-02-12
[QUOTE=atoponce][LIST=1]
[*]Not sure if KDE 3.5.1 is in the repos or not.  I guess it wouldn't hurt to run sudo apt-get update, and see if it shows up.
[*]Firefox renders Gmail flawlessly.  Konqueror is good, but Firefox is better.  Opera works well too.
[*]Not sure.
[*]For me, the best place to conribute is the forums itself.  If you know something that someone has a question with, jump in.
[*]I don't know of any off hand, however, I am interseted in the same thing.  If you find something out, let us know.[/LIST][/QUOTE]
Yeah, I know :)
IE 5.5+ (download:Windows) 
Netscape 7.1+ (download: Windows Mac Linux) 
Mozilla 1.4+ (download: Windows Mac Linux) 
Firefox 0.8+ (download: Windows Mac Linux) 
Safari 1.2.1+ (download: Mac)
These are the fully supported browsers, although I can live with using the chat function on Firefox, I am just curious about Konqueror.

I have been doing that on a Norwegian web page for a while, seems to me that it has been an growing interst in Linux over here:D Though I wish I could do something more... but it is just so much that I does not really know where to start...:( 

I have added you to my buddie list, so I will give you a notice whenever I find something.

---

### Post by UbuntuStudent on 2006-02-12
[QUOTE=gingermark]No, I meant I'd answered 1 out 5 of your questions :) Sorry....[/QUOTE]
Ok, then I give it a try, read about some people that have run into some problems after updating so I just assumed you meant my system would end up like a mess:p

---

### Post by gingermark on 2006-02-12
I also have seen posts from people who had problems. All I can say is it works perfectly for me. So, I guess it's your choice. I haven't noticed much improvement though, I have to say. I'm sure the improvements are there though.

---

### Post by Single on 2006-02-12
3. I recommend  [KMPlayer]("http://kmplayer.kde.org/") as I find that it is the only decent media player that is both a Kde application and stable.

The Ubuntu deb link on the page is broken, and the Debian debs have dependency issues with Breezy, so I suggest you to compile from source.

As for the backends, either xine or mplayer-nogui from the repository is fine, but there is no harm to get both. 
For the codecs, download the w32codecs deb from [here]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28restrictedformat%29").

Don't hesitate to ask for help if you run into any more problem.

---

### Post by fakie_flip on 2007-05-17
If you want a KDE web browser that supports gmail chat, use Opera. [www.opera.com](www.opera.com)

---

