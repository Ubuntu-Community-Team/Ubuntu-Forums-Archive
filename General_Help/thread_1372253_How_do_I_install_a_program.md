---
title: "How do I install a program?"
date: 2010-01-04
forum: General Help
---

### Post by Coco999 on 2010-01-04
Installations are straightforward if the program is catalogued in your repository. But if I got it elsewhere, I am at a loss. I got a folder conaining the executable plus ancillary files. Clicking or double clicking are useless. What do I do?

Incidentally, this program requires JAVA. I've downloaded it but again don't know how to install it. It might be already installed. How do I check it? If necessary, how do I install it?

---

### Post by nothingspecial on 2010-01-04
What program is it?

Is it contained within a tarball. Is it a .deb?

Is there a README file contained within it?

---

### Post by Shippou on 2010-01-04
> **Coco999 said:**
> Installations are straightforward if the program is catalogued in your repository. But if I got it elsewhere, I am at a loss. I got a folder conaining the executable plus ancillary files. Clicking or double clicking are useless. What do I do?

Incidentally, this program requires JAVA. I've downloaded it but again don't know how to install it. It might be already installed. How do I check it? If necessary, how do I install it?

Did you downloaded the installer? And if so, what format?

It should be .deb, .rpm, or something like that. Not .exe.

---

### Post by MelDJ on 2010-01-04
this might help: [How to install ANYTHING in Ubuntu!]("http://amitech.50webs.com/installing/index.php.html#installing_a_package_manually")

---

### Post by Saiko Berry on 2010-01-04
> **Coco999 said:**
> Installations are straightforward if the program is catalogued in your repository. But if I got it elsewhere, I am at a loss. I got a folder conaining the executable plus ancillary files. Clicking or double clicking are useless. What do I do?

Incidentally, this program requires JAVA. I've downloaded it but again don't know how to install it. It might be already installed. How do I check it? If necessary, how do I install it?

CD to the directory it's in. Lets say you put the folder on your desktop and its called that_installer.

cd Desktop/that_installer/
./configure
make
sudo make install

---

### Post by Coco999 on 2010-01-04
> **nothingspecial said:**
> What program is it?

Is it contained within a tarball. Is it a .deb?

Is there a README file contained within it?

The name is MagnumOpus. What is a *tarball*? 
It is .jar. No **readme** file


> Did you downloaded the installer? And if so, what format?

It should be .deb, .rpm, or something like that. Not .exe. 

No downloader available. Extension is .jar, I think this is the exexutable.



> CD to the directory it's in. Lets say you put the folder on your desktop and its called that_installer.
Do you use *installer* as a fantasy name or is it supposed to imply a functionality? I have none.

---

### Post by SuperSonic4 on 2010-01-04
If the extension is jar it usually suffices to run ```
java file.jar
```

*installer* is a made up name used as an example (same as *file* above).The idea is to replace these words with the name of your file

---

### Post by 3rdalbum on 2010-01-04
I imagine there should be instructions, either with that file or on its developer's website.

There might be a shell script included (filename might end in '.sh'), that you have to drag to the terminal window to run the program.

---

### Post by Saiko Berry on 2010-01-04
....I was making an example.

.jar files are java archive files not executeables. You're trying to install something made in Javascript. Mind giving an ls on the contents of the downloaded files?

Unpack the .jar

---

### Post by Shippou on 2010-01-04
So it's a jar. Then you really need Java.

Install java by using the repository. Then you can start your app by 

```

java -jar <jar file name here>.jar

```

That should get you going.

Note: Install the Java Runtime Environment.

---

### Post by Shippou on 2010-01-04
> **Saiko Berry said:**
> ....I was making an example.

.jar files are java archive files not executeables. You're trying to install something made in Javascript. Mind giving an ls on the contents of the downloaded files?

Unpack the .jar

I think, since it is distributed as a jar file, the file is executable.

BTW, a jar file IS executable. It is just like an executable tarball (provided that it is packed correctly).

I do utilize jar files in my Java programs, and I think it is a very handy archive.

---

### Post by Saiko Berry on 2010-01-04
True, but through miscomprehension I was under the impression that clicking it did nothing for them .. while assuming they had JavaRE. JRE should already be installed. Assumptions suck. lol

They're still unpackable.

---

### Post by Shippou on 2010-01-04
> **Saiko Berry said:**
> 
They're still unpackable.

Yes. But most likely you will only get a bunch of class files, some directories containing class files again, the EULA, a README file, a HELP file, pictures, sounds, etc.

Well, I would also appreciate if it contains the source code. :p

Sorry, I am not bashing saiko berry. Just imagining if the source code was accidentally (or intentionally) included. :lolflag:

---

### Post by Saiko Berry on 2010-01-04
xD Understood.

---

### Post by Coco999 on 2010-01-04
SUCCESS!

Installing Java did the trick. Then when I click with the right button on the *.jar file it offers me to open it with Java, and so I can use the program. 

Thank you very much for your help. I'm solving my problems and learning Ubuntu on my way

---

