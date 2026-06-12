---
title: "REQUEST: Step by step guide on installing Java (JRE 5) to Ubuntu"
date: 2011-01-22
forum: General Help
---

### Post by troyboy1 on 2011-01-22
Hello guys I am currently trying to a get a game called Haven and Hearth [http://www.havenandhearth.com/portal/](http://www.havenandhearth.com/portal/) to run properly on my finance's computer, after some long forum research on their forum and trouble shooting I think I have found my solution, but in that I have found another wall in my progress. I consider myself to mildly intelligent, but unfortunately being fairly new to linux I must admit I need your assistance. I have already removed that OpenJava6 whatever it called software from the software center, because it does not run the game properly, the community has suggested I run jre5, which I guess was the version right before java6, so I would like to take their advice. Instead of arguing and try to figure out if they are right or not (considering the developers of that game already said it best ran in jre 5 )can someone on this forum simply tell me step by step how to install jre 5 properly onto this system, yes I have been trying, but I just am lost.

currently on this system now, i have downloaded jre-1_5_0_22-linux-i586.bin, tell me how to install this please.

---

### Post by Nytram on 2011-01-22
Open a terminal and change directory to the one with your file in.

Make your file executable with this command:

> chmod +x jre-1_5_0_22-linux-i586.bin

And then run the file with:

> ./jre-1_5_0_22-linux-i586.bin

---

### Post by TBABill on 2011-01-22
You may have gone a bit further than necessary. I think I understand your problem and what may help. Right now your system probably uses the icetea plugin for Java, which is open source java. It's pretty good but Sun Java is much better. If this is just for your browser, just ```
sudo apt-get install sun-java6-plugin
``` and then restart your browser. You can also search for sun plugin in Synaptic and mark that file for installation. If you end up with a conflict after that (try it out on the site/app you need it to work on first), you can remove icetea6-plugin. I had to do that to get Chromium working in the past, but most recently I have not needed to. I just add the sun java plugin and all is well.

---

### Post by saty on 2011-01-22
I think you can still be able to install the package java-sun5-jre from the jaunty multiverse. Add “deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse” to your /etc/apt/sources.list, which you can do by using an editor or from System->Admin->Software Sources.

---

### Post by Irony on 2011-01-22
Instructions are here (go to contents 7.1 and 7.3 for 32 bit);

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by lykeion on 2011-01-22
Java 5 is more or less deprecated for the new Java 6, and I don't think you'll need the old version to run the game.
You'd be better off to install Sun Java 6 JRE + browser plugin. Here's how you would install it in Lucid and later:

1. start a terminal (accessories > applications > terminal)
2. enable partner repository:
```
sudo add-apt-repository  "deb http://archive.canonical.com/ $(lsb_release -cs) partner"
```
3. update the repositories
```
sudo apt-get update
```
4. remove IcedTea Java browser plugin
```
sudo apt-get remove icedtea6-plugin
```
5. install Sun Java browser plugin
```
sudo apt-get install sun-java6-plugin
```
6. install Sun Java JRE 6
```
sudo apt-get install sun-java6-jre
```
7. set java version
```
sudo update-java-alternatives -s java-6-sun
```
Restart browser and try game again (but when I checked earlier game site seems down: [http://www.downforeveryoneorjustme.com/www.havenandhearth.com](http://www.downforeveryoneorjustme.com/www.havenandhearth.com))

EDIT:
Found this page which has a Java Web Start link (jnlp) to launch the game: [http://www.lgdb.org/game/haven_and_hearth](http://www.lgdb.org/game/haven_and_hearth) 
(Note that someone commented on the page that you need to install *libjogl-java* to make it work - just install it with *sudo apt-get install libjogl-java*)

---

