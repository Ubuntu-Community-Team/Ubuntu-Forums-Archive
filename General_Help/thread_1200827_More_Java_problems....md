---
title: "More Java problems..."
date: 2009-06-30
forum: General Help
---

### Post by es0tericcha0s on 2009-06-30
So I'm about ready to tear some of my hair out over this thing. I've read a half dozen tutorials and browsed the forums, etc to figure out how to upgrade to the newest Java(jre 6u14) and I've just come up empty. I'm not the most Linux savvy person but geez, I know how to read and copy and paste, but no luck. Anyway, I have all the Java stuff from Synaptics but it's not letting me open up some game applets @ games.yahoo.com and I'm addicted to a card game there so I'm going crazy wrestling with this thing. I also downloaded the jre6u14.bin file from Java and tried to get that running through the instructions I found here and at various places but nada. 
OK so when I run this:     sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts  It says I already have the newest version, yet the card game section opens but when I try to go to the table it doesn't load. Also, running this: java -version says I have 1.6.0.0 and Java.com also says I need the latest greatest update. Which I have saved onto my desktop but opening the terminal and going through mkdir/cd/chmod tutorial etc doesn't work either. At one point I did see the whole long agreement thing which I went through and said yes I agree but that didn't seem to change anything either. Let me know what other info I need to give you so you can figure out where I'm going wrong and I'll be forever grateful for the help...


DW

---

### Post by jimv on 2009-06-30
Which game in particular?  A lot of them appear to be Flash based.

EDIT

Also, what does "sudo update-java-alternatives -l" return?

---

### Post by walterp98@gmail.com on 2009-07-17
I'm unable to play Pinochle or cribbage ... they start to pop up the table list, but then show me "This game cannot be played using your current settings. Please, try the following:"

I received 
```

java-6-sun 63 /usr/lib/jvm/java-6-sun

```when I execute your command.

I'm up to date with java, I believe 
```

flashplugin-installer is already the newest version.
flashplugin-installer set to manually installed.

sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.


```Thanks in advance for your  help.

Walter

>>>> edit >>>>
I cleared cache and cookies ... now it works

---

