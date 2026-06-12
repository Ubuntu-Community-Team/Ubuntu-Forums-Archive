---
title: "Java in Ubuntu"
date: 2006-03-14
forum: General Help
---

### Post by sankarv on 2006-03-14
I extracted the standard JDK 1.4 from java.sun.com in ubuntu in /usr/java.
Now if i try to run applets they say no classes are found.
Is it needed to specify any PATHs for classes/libraries?
If so wat is the way of specifying it?

---

### Post by gmclachl on 2006-03-14
Try running 

 sudo update-alternatives --config java

  Then select one of the options.

 George

---

### Post by knalle on 2006-03-14
you need to install the jdk properly, here is a howto i have found that works for me:

---

### Post by knalle on 2006-03-14
Go to Sun's website [http://java.sun.com/](http://java.sun.com/) and select the java jdk or jre that you want.

This example uses J2jsdk-1.4.2 but you can use any J2sdk. Run similar commands from the terminal:

First install the required packages:

```
sudo apt-get install fakeroot java-package java-common
```

Create the Deb file for the install:

```
fakeroot make-jpkg sun-j2sdk-1.4.2_10-linux-i586.bin
```

Install The deb file

```
sudo dpkg -i sun-j2sdk-1.4.2_10_i386.deb
```

Now make Sun's java the default by running this command and selecting it.

```
sudo update-alternatives --config java
```

you can now check your java sdk with:

```
java -version
```

java version "1.4.2_10"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2_10-b03)
Java HotSpot(TM) Client VM (build 1.4.2_10-b03, mixed mode)

Happy Hacking!

---

### Post by gibson on 2006-03-14
[QUOTE=knalle]Go to Sun's website [http://java.sun.com/](http://java.sun.com/) and select the java jdk or jre that you want.

This example uses J2jsdk-1.4.2 but you can use any J2sdk. Run similar commands from the terminal:

First install the required packages:
[/QUOTE]

can we get this as a how-to?

This question is asked a LOT.

all the best

---

### Post by GolfGeek on 2006-03-16
Just a brief comment here. I couldn't get one of these techniques to work. After I download the file from Sun, and entered a terminal mode, I tried to install it

sudo apt-get install fakeroot /Home/Carl/My Downloads/jre-1_5_0_06-linux-i586.bin
it responds with 
Reading Package lists..Done
Building dependency tree..done
E:Couldn't find package

After a couple of tries at this, I went back to the Sun site [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)  and printed the installation notes
I created a directory (folder) called jre1.5.0 and downloaded to that folder
Then ran the chmod +x jre-1_5_0_06-linux-i586.bin
then typed ./jre-1_5_0_06-linux-i586.bin
note: didn't work without the ./
I got the license agreement, typed yes and it proceeded with the installation. Still don't know if everything is working perfectly but these instruction did something. 
Hope this helps someone else

---

### Post by Luke on 2006-03-16
[QUOTE=GolfGeek]sudo apt-get install fakeroot /Home/Carl/My Downloads/jre-1_5_0_06-linux-i586.bin
[/QUOTE]


you did not follow knalle's directions. look at them again. :)

---

### Post by GolfGeek on 2006-03-16
I'm confused
Knalle wrote:sudo apt-get install fakeroot java-package java-common

and I wrote:
sudo apt-get install fakeroot/Home/Carl/MyDownloads/jre-1_5_0_06-linux-i586.bin

I'm assuming I needed to include the path to the package (downloaded file)
Was I missing "java-common" and what does that refer to?

---

### Post by Ramses de Norre on 2006-03-16
```
sudo apt-get install fakeroot java-package java-common
```
Those are the names of the packages you need to install;)

---

### Post by GolfGeek on 2006-03-16
Ramses - I must really be dense because I cannot fathom what they would mean by java-common. Actually, in browsing thru these forums, I get the sense I'm not the only person this stupid.  Does java-common (jc) mean a place, a folder where "common" files would be installed? Does it refer to commonly installed elements? Probably not, because they would be bundled in the binary "package". Is there such a place as java-common by default. I used file manager to browse thru the file system and couldn't find anything like it. This is really frustrating - I've spent hours trying to install something that "should" be part of a well designed system. Given the current state of the internet, it has passed the point of a "fad that will die". It is here to say and an integral part of browsing is the need for java applets to work. I appreciate your help here. Ubuntu looks really nice. There are a number of features that are excellent but if this is what people have to go thru, it is never going to be more than  the "hot ticket" for the tecchies. I started out back with 64K CPM machines (2 eight inch floppies!) so I recognize that the power of the command line.  So many of the "help" lines (responses) remind me of an incident with my mother. During WWII my father had gone off to war and my mother moved into a house next to my grandparents. Mother always loved the fresh bread my grandmother made so one day she asked for the recipe and Gram obliged. The next day she was nearly in tears and my grandmother asked what was wrong. Mother explained that she followed the direction so carefully, had done everything the right way but the fruits of her labor was two bricks of hardened flour. Gram asked what she had put in and mother listed the ingredients. Gram said "What about the yeast? and nother replied, there was no mention of yeast in the recipe and Gram replied "Any damned fool knows you need yeast! " Just an observation

---

### Post by Luke on 2006-03-16
type exactly what knalle posted. word for word. copy and paste if you want.


edit: just read your entire post, you're over-complicating the matter.
this recipe is complete. it does not call for yeast. don't try to add yeast. :)

---

### Post by Ramses de Norre on 2006-03-16
sudo apt-get install package_names
knalle gave you the names of the packages, so java-common is a package you need to install.
I wouldn't just copy paste because of updated version numbers.

---

### Post by chadmichael on 2006-03-16
Indeed, what are the nature of the packages java-common and java-package.  I'm not exactly a newbie.  I underdstand that these are packages from ubuntu.  What I don't understand is this:

I download the jdk from java and install it.  The only thing left, in my opinion, is to get the location of this stuff onto the path.  All of the functionality of java is in the java directory where I installed sun's jdk.  What is the purpose of the java-common and java-package packages?

---

### Post by sublime on 2006-03-16
running an apt-get command downloads the packages from the ubuntu repositiories.  you dont need to download the packages before you run apt-get, it'll do that for you and then install them properly.  to get the java libraries i'd download automatix and use that.  do a search for it.  it's got a ton of usefull programs.

---

### Post by hod139 on 2006-03-16
[quote=gibson]can we get this as a how-to?

This question is asked a LOT.

all the best[/quote]

Like these?
[B][HOW-TO: Building your own Java 1.5 package]("http://ubuntuforums.org/showthread.php?t=76735")
[/B][B][Howto: Install Sun's Java (SDK/JRE) the easy way (using the plf repos)]("http://ubuntuforums.org/showthread.php?t=140769")
[/B][**HOWTO: Sun Java 1.5 and Flash in 64-bit Konqueror browser! (No chroot required)**]("http://ubuntuforums.org/showthread.php?t=90919")
[**[URL="http://ubuntuforums.org/"] Automatix: Automated Graphical Installer and Tweaker]("http://ubuntuforums.org/showthread.php?t=80295") **[/URL]

---

