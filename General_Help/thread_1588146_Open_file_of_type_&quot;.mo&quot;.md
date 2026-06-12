---
title: "Open file of type &quot;.mo&quot;"
date: 2010-10-04
forum: General Help
---

### Post by stringkarma on 2010-10-04
One thing I have always liked about linux is that it doesn't care too much about file name extensions. However I have run into a problem. OpenModelica is a language for modeling a mathematical system and its source files (text) need an extensions ".mo". Gnome on the other hand won't open these without a fight as it is supposedly a machine readable file.

I think I know how to work around, but I am curious as to why this is an issue? If I run 
```

$ file HelloWorld.mo 
HelloWorld.mo: ASCII C++ program text

```
but if I try
```

$ gnome-open HelloWorld.mo 
Error showing url: No application is registered as handling this file

```
I thought Gnome was smarter than checking file extensions!?!

---

### Post by Topsiho on 2010-10-04
Generally speaking I think you're right when you say that extensions are not as important in Linux as in Windows. But sometimes they are. When compiling a program the extension tells the compiler what kind of program it has to compile: C, C++ or other.

.mo-files are compiled translated .po-files, and contain a number of strings, from an application, that are translated into another language, such as Dutch, or even GB-or other English. These .mo-files then are used to use the translated application in that other language.

I don't think this is of any use to you, but maybe you'll understand that sometimes extensions are important, even in Linux :)
You yourself tell us that OpenModelica needs a .mo-extension, which probably is unfortunate.

Topsiho

---

### Post by stringkarma on 2010-10-04
I certainly understand that extensions are important, especially for a compiler or a script-loader etc. The problem I have is that it is related to the clash of two such restrictions. I can understand even that the two different ".mo" files are for different and dramatically different uses. I was just surprised that Gnome didn't check the file contents (as returned from "file") as I thought that it would, notice that it was ASCII and open it with gedit.

Edit: I guess what I am asking, is how does Gnome determine what to do with a given file? I thought that it called "file" to find out, but apparently not.

---

### Post by stringkarma on 2010-10-04
To further elaborate: I found the other type of .mo file and tried
```

$ file /usr/share/ufw/messages/sl.mo
/usr/share/ufw/messages/sl.mo: GNU message catalog (little endian), revision 0, 158 messages

```

So file knows the difference between these two. Again, just a curiosity, but an interesting one to me.

---

### Post by stringkarma on 2010-11-27
This problem is irking me again, so if I may ... Bump.

To reiterate the problem is that I want Gnome/Nautilus to open my .mo files in gedit without changing the preference for "translated message (machine readable)" files.

To test 

create a file helloworld.mo and then try to open it in Nautilus (i.e. from the file browser or on the desktop).

---

### Post by luigi_mb on 2010-11-27
Try to use a different editor. nedit does open .mo files.

/luigi

---

### Post by WorMzy on 2010-11-27
What are you trying to do? You should have no need to edit system files; doing so may cause your programs to behave erratically, or to cease functioning all together.

Vim and nano can both edit mo files, but I don't see why you would ever want to.

---

### Post by stringkarma on 2010-12-06
Again, I am not editing system files, I am editing files that have what is apparently the same extension as a system file. I have Modelica Object files (.mo) that I want to be able to edit. See above.

---

### Post by impresionist on 2012-02-18
> **WorMzy said:**
> What are you trying to do? You should have no need to edit system files; doing so may cause your programs to behave erratically, or to cease functioning all together.

Vim and nano can both edit mo files, but I don't see why you would ever want to.

In my cause they are not, I'm trying to open a .mo file to edit translation strings in an application, but I can't, gnome text editor are dropping me... nano open codified text... vi the same... and I'm googling since couple of hours, but no way... can't open it...

---

### Post by Topsiho on 2012-02-18
I hope you're aware that this is a very old topic :)

In stead of editing .mo files, which are compiled .po files, you should edit the corresponding .po file, which you should search for on the internet.

After editing this, e.g. using lokalize, you can compile it using msgfmt. I copy from [http://encyclopedia.thefreedictionary.com/Msgfmt:](http://encyclopedia.thefreedictionary.com/Msgfmt:)

"msgfmt is a Unix utility that creates message object files from portable object files (filename.po), without changing the portable object files. It is included in the gettext package."

This means you'll have to install the gettext package, which is in the Ubuntu repositories.

If I remember correctly you type in the commandline (after editing the .po file):

msgfmt <filename>.po -o <filename>.mo

and put the .mo file in the apropriate directory.

This way you can also do your own translations, but better is, of course, to share this work with others, such as a translation team for your language.

Topsiho

---

### Post by oldos2er on 2012-02-18
Closed, necromancy. If there are further questions, please start a new thread.

---

