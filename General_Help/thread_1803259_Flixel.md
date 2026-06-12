---
title: "Flixel"
date: 2011-07-13
forum: General Help
---

### Post by Cabria on 2011-07-13
I'm not quite sure if this is in the right place but it's my first question so here it goes. 

Is Flixel available on Linux/Ubuntu? It's not in the package manager, but it is open-source; so it leads me to believe that it needs to be compiled. Sadly I have absolutely no idea how to do that. So is it available? Do I need to compile it? If so, how do I do that?

Thanks!

---

### Post by Hellenion on 2011-09-21
Hi Cabria,

I myself am busy trying to make flash games with flixel on ubuntu and, while I haven't been able to run what I've made, I can share with you what I've found:

flixel is indeed just the source, but that's the intended way of using it: you write your game in actionscript and include flixel's org folder in your project. this way the javascript code that you are writing can directly use flixel's functionality.

You will need your own compiler to compile your code to make it a game. And here is where the problems start, actionscript seems to be poorly supported by linux. I still find this hard to believe...

Anyway: You will need the Flex SDK to compile your code. I followed this quide:
[http://stevelove.org/2009/05/14/how-to-install-and-set-up-adobe-flex-sdk-on-ubuntu-linux/](http://stevelove.org/2009/05/14/how-to-install-and-set-up-adobe-flex-sdk-on-ubuntu-linux/)

You should write your actionscript code in plain text files as there are no IDE's available for linux, you can do this with gedit. make sure to use a text editor, ubuntu will try to open your .as files in openoffice.org spreadsheet, allowing this to happen will break your code.

from this point you should try to follow some flixel beginner's guide.

---

### Post by SavageWolf on 2011-09-21
I use Geany for my actionscript needs, and you can set the application to open the files in the Right-Click -> Properties -> Open With option.

I'm not sure if the Flixel tutorial tells you this, but you can embed assets using:
```
[Embed(source="../res/image.png")] public static const IMAGE_NAME:Class;
```

And you can also set the SWF's properties using:
```
[SWF(width=800, height=575, backgroundColor="#bbccbb", frameRate=30)]
```, but this statement must be below any imports.

Those two are a little obscure, and may be hard to find, so I'm telling you them now so you don't have to go looking.

As was said, Flixel is just a "library", pre-written code that you can use. It's not a stand-alone program on its own, you use it to make your own programs. It's like a "motor" in a car or something, it does something, but can't function without anything telling it what to do.

Flex runs fine in Linux, if a little stupid, what problems are you both having?

Hmm... I've been loosly thinking about making a Flex tutorial...

---

### Post by Hellenion on 2011-09-22
I got everything to work now. well, sort of.

Flex4 was compiling but I couldn't run the resulting .swf on ubuntu, while it played just fine on windows...
So I switched to Flex3.something, which resulted in flixel complaining. I commented out some lines of code and now it runs!

I believe there were some Flex4-only lines in the "org/flixel/system/debug" directory.

And thanks for that SWF properties line, sagewolf! but I'm not really sure what the other does :p

---

