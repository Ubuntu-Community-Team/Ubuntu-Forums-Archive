---
title: "Why..."
date: 2006-04-28
forum: General Help
---

### Post by Caligula on 2006-04-28
have half the original packages got ZERO integration with gnome?
A screenshot attached...

It's really weird.. I mean, that's what's coming with it! isn't it supposed to work?:confused: ](*,) 

thanks,
josh:)

---

### Post by echo $USER on 2006-04-28
Can you elaborate more, I don't know what you are trying to get accross.  Trouble with your login screen?

---

### Post by Qrk on 2006-04-28
Apps run with sudo don't look for the themes you have installed in your home directory. You should install themes to /usr/share/themes so that they can be accessible to all users. You can simply copy the them from ~./themes

---

### Post by Jagot on 2006-04-28
Take a look at point 4 on this guide:

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by Caligula on 2006-04-28
ah!
that's what I meant...
sorry if I wasn't clear...

I copied it to /usr/share/themes, but it didn't make any difference, even after restarting Gnome, am I doing something wrong?

thanks

---

### Post by Ramses de Norre on 2006-04-28
```
sudo ln -s /home/<insert your username here>/.themes /root/.themes && sudo ln -s /home/<insert your username here>/.icons /root/.icons && sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```(this was already mentioned by a previous poster)

---

### Post by sinkxdie on 2006-04-28
How did you get the powerpuff girls onto your ubuntu icon in the forums?
Sorry, lol it justs looks cool...Is it a hebrew thing only?

---

### Post by Qrk on 2006-04-28
[QUOTE=Caligula]ah!
that's what I meant...
sorry if I wasn't clear...

I copied it to /usr/share/themes, but it didn't make any difference, even after restarting Gnome, am I doing something wrong?

thanks[/QUOTE]

You have to go into System->Preferences->Themes and reselect whichever theme you want.

---

### Post by Ramses de Norre on 2006-04-28
[QUOTE=sinkxdie]How did you get the powerpuff girls onto your ubuntu icon in the forums?
Sorry, lol it justs looks cool...Is it a hebrew thing only?[/QUOTE]

That was the look of the forums on april the first.

---

### Post by Caligula on 2006-04-28
> How did you get the powerpuff girls onto your ubuntu icon in the forums?
Sorry, lol it justs looks cool...Is it a hebrew thing only?

The april fools' theme...

about the rest, thanks everybody, it's great now...
I followed that HOWTO there, and got quite a nice CPU eating desktop...lol](*,) :D 

here's a screenshot of the result...

---

### Post by OffHand on 2006-04-28
[QUOTE=Caligula]The april fools' theme...

about the rest, thanks everybody, it's great now...
I followed that HOWTO there, and got quite a nice CPU eating desktop...lol](*,) :D 

here's a screenshot of the result...[/QUOTE]eeeeewww... Elton John :-#

---

### Post by Caligula on 2006-04-28
lol...
some good music never hurt anybody....

---

