---
title: "Lost on installing java"
date: 2009-08-22
forum: General Help
---

### Post by Sethun on 2009-08-22
I was wondering how I install java from the site. I'm pretty new, and I've read around a bit and figured out I need alien, which I have to convert the red hat format.
But after that I get lost on the rpm.bin file that I never seem to find. Any advice would be extremely helpful, also I'm running 9.04 jaunty jackalope.

---

### Post by 3rdalbum on 2009-08-22
Don't install Java from the Sun website, install it from the repositories.

Go to Synaptic Package Manager and install the "sun-java6-jre", "sun-java6-bin" and "sun-java6-plugin" packages. Easy.

---

### Post by Sethun on 2009-08-25
Thanks for the info, but my java still doesn't seem to work with chat applets. :/

---

### Post by P4man on 2009-08-25
Setting up java is drop dead easy from the repo's but I fear your attempts to convert a red hat package into a .deb and installing that way may have caused some trouble..

Anyway, what does this link give you ?

[http://www.javatester.org/](http://www.javatester.org/)

(click the test button on top).

And what happens when you type in a console:

```
java -version
```

---

### Post by chf on 2009-08-25
Hello,

you can find a bit more information about java installation and configuration her [https://help.ubuntu.com/community/JavaInstallation]("https://help.ubuntu.com/community/JavaInstallation")
and here [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

best regards

chf

---

### Post by Sethun on 2009-08-27
> **P4man said:**
> Setting up java is drop dead easy from the repo's but I fear your attempts to convert a red hat package into a .deb and installing that way may have caused some trouble..

Anyway, what does this link give you ?

[http://www.javatester.org/](http://www.javatester.org/)

(click the test button on top).

And what happens when you type in a console:

```
java -version
```

Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

---

### Post by jamesstansell on 2009-08-27
Is that also what javatester.org shows for your java plugin version?

---

### Post by dira on 2009-10-01
> **3rdalbum said:**
> Don't install Java from the Sun website, install it from the repositories.

Go to Synaptic Package Manager and install the "sun-java6-jre", "sun-java6-bin" and "sun-java6-plugin" packages. Easy.

Thank you!
I was trying to install OmegaT and could not figure out which was the best way to load java.
Luckily I found this thread.
One question though : is it possible to launch OmegaT (or any installed software) by double clicking on an icon instead of right clicking on the relevant .jar file + selecting "open with java run time"... ? A bit like in windows...

Another remark about translations (how to report typos in other languages ?)
I am using the Turkish version and I noticed minor typos here and there...

---

### Post by Sef on 2009-10-01
> One question though : is it possible to launch OmegaT (or any installed software) by double clicking on an icon instead of right clicking on the relevant .jar file + selecting "open with java run time"... ? A bit like in windows...

With Ubuntu, if it is a .deb, then usually you will be able to click on it to install it.

---

### Post by StuartN on 2009-10-01
> **dira said:**
> One question though : is it possible to launch OmegaT (or any installed software) by double clicking on an icon instead of right clicking on the relevant .jar file + selecting "open with java run time"... ? A bit like in windows...

You can create a launcher on the desktop by right-clicking any blank space, select Create launcher then give it a name and the command "java my_app.jar" where my_app is the name of your java archive file. You can add the same command to a menu from System->Preferences->Main menu

---

### Post by dira on 2009-10-01
> **StuartN said:**
> You can create a launcher on the desktop by right-clicking any blank space, select Create launcher then give it a name and the command "java my_app.jar" where my_app is the name of your java archive file. You can add the same command to a menu from System->Preferences->Main menu

Thanks.
But somehow it cannot be executed with a double click when I specify the command "java my_app.jar" with both methods you have described.
Instead I modified the properties of OmegaT.jar and selected: "Open with-> Sun Java 6 Runtime".
This way when I double click on the OmegaT.jar (where it is) it runs.
But when I drag and drop OmegaT.jar on the desktop (CTRL pressed), the dropped icon cannot be executed with a double click... why?

---

### Post by StuartN on 2009-10-01
> **dira said:**
> But somehow it cannot be executed with a double click when I specify the command "java my_app.jar"

Did you include the whole path? For instance, if my_app.jar is in your Documents folder, then the path would be ~/Documents/my_app.jar (and remember that Linux path and filenames are case sensitive).

> **dira said:**
> But when I drag and drop OmegaT.jar on the desktop (CTRL pressed), the dropped icon cannot be executed with a double click... why?

Possibly there is an associated file in the directory you copied OmegaT.jar from, such as a function library.

---

### Post by dira on 2009-10-01
[quote=StuartN;8037219]Did you include the whole path? For instance, if my_app.jar is in your Documents folder, then the path would be ~/Documents/my_app.jar (and remember that Linux path and filenames are case sensitive).

Anyway I could not see the Create Launcher option in the pop up menu after right clicking on OmegaT.jar.
From System->Preferences->Main menu I selected (Launcher) properties and selected the file OmegaT (I did not type) and this way the complete (absolute) pathname was specified; I then added "java " before the pathname. So the path should be correct.

---

### Post by StuartN on 2009-10-01
> **dira said:**
> Instead I modified the properties of OmegaT.jar and selected: "Open with-> Sun Java 6 Runtime".

I use the command java, but perhaps on your system Sun Java 6 Runtime is not invoked by the command java. You will need to find the correct command, and possibly its path.

---

### Post by dira on 2009-10-02
> **StuartN said:**
> I use the command java, but perhaps on your system Sun Java 6 Runtime is not invoked by the command java. You will need to find the correct command, and possibly its path.

OK. Thanks

---

