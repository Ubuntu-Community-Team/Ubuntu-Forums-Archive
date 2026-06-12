---
title: "Cannot find downloaded programs"
date: 2011-09-06
forum: General Help
---

### Post by Catlike on 2011-09-06
I downloaded the statistics program 'R' and the Java GUI for R. I followed instructions and installed them via a terminal window. Cannot find them. Where do programs go when you install them in Ubuntu (Natty Narwhal)? 
You may correctly assume that I am entirely ignorant of computer languages; I have always used graphic user interfaces.
Thank you.

---

### Post by jfed on 2011-09-06
Usually under programs>applications, those are sorted by catagory and you might be able to find it in there, however sometimes you can not because that's just not how the particular program works. Try starting it threw the terminal. To start a program through the terminal you simply just type its name.

```
chromium-browser
```

Like that. Hope this helped!

---

### Post by veggen on 2011-09-06
Don't know much about this particular program, but Java apps are usually run by simply running the .jar. Do have it's .jar?

---

### Post by Catlike on 2011-09-08
> **veggen said:**
> Don't know much about this particular program, but Java apps are usually run by simply running the .jar. Do have it's .jar?

I just found a folder called "JGR.jar". Inside are these folders: "icons"; "jedit"; "META-INF"; "org"; and "rosuda". Also there is an icon of a screen which is named "jgrsplash.jpg". I cannot tell which of these has a launcher or executable file to launch the JGR program; each folder is full of cryptically-named sub-folders and/or files.

Thank you for replying. Have you any ideas on what to do next?

---

### Post by Catlike on 2011-09-08
> **jfed said:**
> Usually under programs>applications, those are sorted by catagory and you might be able to find it in there, however sometimes you can not because that's just not how the particular program works. Try starting it threw the terminal. To start a program through the terminal you simply just type its name.

```
chromium-browser
```Like that. Hope this helped!

Thank you for replying. I opened a terminal (new to me, pretty much!) and typed at the prompt [I remember that much from DOS] "JGR" (without the quotes); then I pressed the Enter key. The response was a line of text: "JGR: command not found"  . 

So maybe I need to unzip some folder or something, but I have no idea.

---

### Post by rewyllys on 2011-09-08
To start R, open a Terminal session and enter **R** at the prompt.

I don't know which GUI you installed for R, but I use "R Commander", which I installed via the Software Center; its package name is "r-cran-rcmdr".  After installation it shows up under Applications -> Science.

Another R GUI, whose package name is "rkward", is also available via the Software Center.

---

### Post by Catlike on 2011-09-08
> **rewyllys said:**
> To start R, open a Terminal session and enter **R** at the prompt.

I don't know which GUI you installed for R, but I use "R Commander", which I installed via the Software Center; its package name is "r-cran-rcmdr".  After installation it shows up under Applications -> Science.

Another R GUI, whose package name is "rkward", is also available via the Software Center.

Thank you. OK, I'll stick with R Commander. I have it, but I was just trying to use JGR because it was recommended at the CRAN site, I think.

---

