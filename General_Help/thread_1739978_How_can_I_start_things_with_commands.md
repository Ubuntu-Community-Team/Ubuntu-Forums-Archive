---
title: "How can I start things with commands?"
date: 2011-04-26
forum: General Help
---

### Post by Lanuk on 2011-04-26
Yeah, I am a complete newbie who has just had his "first cup of Ubuntu". I was wondering how I could  magically start programs using commands, like my google chrome browser for example. Also, would it be possible to use commands to start things like games? I have this one game called Minecraft. It is a jar file, and I have to open it with Sun Java 6 Runtime. Could I possibly start even this from terminal? Help would be appreciated, thanks!

---

### Post by nothingspecial on 2011-04-26
Just open a terminal and type the name of the app (usually)

---

### Post by Lanuk on 2011-04-26
> **nothingspecial said:**
> Just open a terminal and type the name of the app (usually)

Ahh thanks, I tried google, chrome, google chrome, google_chrome, and many others until I finally figured it out... it was google-chrome. Opening minecraft.jar with java is a whole other thing though...

---

### Post by daweefolk on 2011-04-26
Assuming the file is named minecraft.jar and it's in the folder you're in, type ```
java -jar minecraft.jar

```

---

### Post by Lanuk on 2011-04-26
> **daweefolk said:**
> Assuming the file is named minecraft.jar and it's in the folder you're in, type ```
java -jar minecraft.jar

```

Hmm, it said unable to access jarfile

---

### Post by WorMzy on 2011-04-26
That'd be because you're not running the command from the same folder as the jar file. Use cd to navigate to the folder
e.g.
```
cd Downloads
java -jar minecraft.jar
```
or use the correct path for the jar file
e.g.
```
java -jar Downloads/minecraft.jar
```
Absolute paths work too:
```
java -jar /home/username/Downloads/minecraft.jar
```

---

### Post by Vaphell on 2011-04-26
and about apps in general - tap tab to autocomplete/show suggestions
for example:
fire[tab] will autocomplete to firefox
goo[tab] should autocomplete to google-chrome, so there is less guessing involved

you can also look for files (apps in particular) with locate
```
locate chrome
```
most probably it will return quite a few results so you can narrow it down with grep (tool searching for given text)
```
locate chrome | grep bin
```
apps usually reside in /usr/bin so bin should filter out files with chrome in name, but not having bin in their path

---

### Post by K_45 on 2011-04-26
Add an ampersand (&) to the end of the command so that you can work with that terminal when the program opens.

---

