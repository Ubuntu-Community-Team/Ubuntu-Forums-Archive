---
title: "I need an interner browser simmilar to Konqueror for gnome"
date: 2006-06-12
forum: General Help
---

### Post by medya on 2006-06-12
Firefox browsers uses an engine(  Gecko engine) that has a bug for kurdish sorany script . but the Konqueror works fine... (because it uses another engine)
but it is for KDE , and I use gnome .

is there any internet browser in gnome which uses the same engine with Konqueror ?

---

### Post by Arnaud_B on 2006-06-12
Why not just using konqueror if you like it? It will work in gnome.. just a few libs to download but should not be an problem...
A.

---

### Post by Rui Pais on 2006-06-12
hi, have you tried with opera? opera didn't use gecko.

---

### Post by medya on 2006-06-12
opera has the same problem...I think it DOES use gecko

---

### Post by bobaymon on 2006-06-12
Konqueror works fine for me - I run Gnome also.

=)

---

### Post by medya on 2006-06-12
[QUOTE=Arnaud_B]Why not just using konqueror if you like it? It will work in gnome.. just a few libs to download but should not be an problem...
A.[/QUOTE]

well those FEW LIBS are 150 mb...not easy to download.
and I want to make sure that there isnt any gnome alternative browser before downloading it...

and I want to offer this sloution to other kurds... so I want to make sure of everything , a light gnome browser that doesnt use that engine would be nice .

---

### Post by aysiu on 2006-06-12
Try this: ```
sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus
sudo ln -s /usr/bin/konqueror /usr/bin/nautilus
``` To *undo* those commands, you can use these commands: ```
sudo rm /usr/bin/nautilus
sudo dpkg-divert --rename --remove /usr/bin/nautilus
```

---

### Post by bobaymon on 2006-06-12
There is Epiphany, I don't know much about it or if it use that engine, but it is for gnome.

---

### Post by bobaymon on 2006-06-12
nvm, Epiphany use Gecko =)

---

### Post by Mr_Congeniality on 2006-06-12
Isn't firefox avaliable on KDE Desktop Enviorments?

---

### Post by tsb on 2006-06-13
yes, I use FF with KDE.  Just three or four dependencies need to run.

---

### Post by medya on 2006-06-13
it seems some of you GUYS not even read my post...

i said FIREFOX has problem in showing kurdish script... I need something simmilar to Konqueror but for gnome .

smmillar in the way that "it doenst use gech engine ...as firefox uses that"

---

### Post by Half-Left on 2006-06-13
[QUOTE=medya]it seems some of you GUYS not even read my post...

i said FIREFOX has problem in showing kurdish script... I need something simmilar to Konqueror but for gnome .

smmillar in the way that "it doenst use gech engine ...as firefox uses that"[/QUOTE]

Then use Konqueror in gnome, you can theme it like gnome(in the kontrol settings) with clearlooks like theme and tango icons for kde.

---

### Post by shakin on 2006-06-13
Just install Konqueror. I don't think any browser other than Konqueror and Safari use KHTML, so if that's the engine you like then you'll need to install it even with the 150 MB of dependencies that it needs.

---

### Post by glotz on 2006-06-13
Damn you guys! Read what he wants and what has allready been suggested.

Have you considered Galeon? It's the predecessor of the Epiphany. It's gecko based. (And Opera is not unlike somebody said)
[http://galeon.sourceforge.net/](http://galeon.sourceforge.net/)

---

### Post by Rui Pais on 2006-06-13
[QUOTE=glotz]Damn you guys! Read what he wants and what has allready been suggested.

Have you considered Galeon? It's the predecessor of the Epiphany. It's gecko based. (And Opera is not unlike somebody said)
[http://galeon.sourceforge.net/](http://galeon.sourceforge.net/)[/QUOTE]

Hi, you are one of those that are note reading ;)

medya wants a browser that ***do not*** use gecko as engine!! (and not konqueror!)

I was the one who suggest opera, but seems that in fact Opera uses Gecko.

---

### Post by glotz on 2006-06-13
Oh damn, looks like you're right and I'm wrong, sorry! :oops:

But still, Opera does not use gecko, it uses something proprietary called [presto](http://en.wikipedia.org/wiki/Presto_%28layout_engine%29).

---

### Post by medya on 2006-06-13
but opera still have the same problem with firefox...

i installed konqueror , but I would still like to a gnomre based one...
because I want to offer this to other ppl too.... they are newbie... I dont want all of those ppl download 150 mb just for konquero .
and konquero is a bit ugly for gnome and it requiers some programs on KDE that I dont have... i will install  Galeon now to see if it is working well.

---

### Post by Rui Pais on 2006-06-13
Ahh,
thanks for the info glotz, i found it strange that Opera, a close source app, used gecko, but since gecko is open source... i look at opera site but couldn't found nothing related.

btw, i look at wikipedia and they have some exhaustive lists of browsers, [here]("http://en.wikipedia.org/wiki/List_of_web_browsers") and a comparison page [here]("http://en.wikipedia.org/wiki/Comparison_of_web_browsers").

Regrettably, for medya, thats seems do not exist nothing of the kind.
Maybe checking dillo, is a very basic browser and seems that have is own engine, but it's a bit ugly and limited and i don't know if it supports kurdish...

---

### Post by zxee on 2006-06-13
Hi, You might also consider going directly to the Mozilla firefox site [http://www.mozilla.org/projects/intl/index.html](http://www.mozilla.org/projects/intl/index.html) 
and letting them know your problems with the lack of Kurdish support. They have a section that deals with language and localization. Hope that helps.

---

### Post by gkoshra on 2006-09-14
Oops. I'm new and when I typed in the code in the example above...

sudo dpkg-divert --divert /usr/bin/nautilus.old --rename /usr/bin/nautilus

I missed off the .old.  I didn't notice until i'd run the next line (sudo ln -s /usr/bin/konqueror /usr/bin/nautilus), replacing konqeror with thunar and nothing seemed to happen when I tried to open a place from the places menu.

Now I can't open places even with nautilus. Durp! Any ideas on what i've done and how I can fix it?

Thanks in advance.

---

### Post by Siyamend on 2007-10-04
I recommend this Webbrowsern 99% correctly with kurdish (sorani) except text Align: justify;.
iceweasel
[http://www.debianadmin.com/install-iceweasel-web-browser-in-debian-and-ubuntu.html](http://www.debianadmin.com/install-iceweasel-web-browser-in-debian-and-ubuntu.html)
and
iceape
[http://www.getdeb.net/app.php?name=Iceape](http://www.getdeb.net/app.php?name=Iceape)
naturly with Wine aplication.

**IEs4Linux**
[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)
[More Info in kurdish Sorani]("http://www.webchin.org/Meko/30.html")

---

