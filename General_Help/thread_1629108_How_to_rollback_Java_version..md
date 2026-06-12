---
title: "How to rollback Java version."
date: 2010-11-23
forum: General Help
---

### Post by DJ-HLS on 2010-11-23
Here's the dilemma:

I play this game called Minecraft, and I'd like to run the server package as well, but the server is laggy as hell.  I did my research, and some people were saying that one of the problems was the Java version.  They recommended rolling back specifically to 1.6.0_13, but they didn't say how. So I Googled for a tutorial on how to roll back Java in Ubuntu, and got nothing.  So here I am.

I also learned that you can add some extra code into a Java run command to make it run off of a specified version, so I added this to the original command I have to run my server```
-version:1.6.0_13
``` and got "Unable to locate JRE meeting specification '1.6.0_13'".  So now I'm thinking that Ubuntu didn't retain any previous versions of Java.  My second question would be, where does Ubuntu keep it's versions of Java, cause I'd just download that version of Java, put it where Ubuntu keeps it, then run that command again and hope it works.

Any and all other ideas are welcome, and thanks in advance!

-Alex

---

### Post by DJ-HLS on 2010-11-25
Bump.

---

### Post by kanishkdudeja on 2010-11-25
ubuntu stores different parts of a program at different locations..

so it wont be possible to jus copy paste that java version and get it running..

i would advise u to uninstall that current version..

and then do a clean install for the version u want.

---

### Post by gandaran on 2010-11-25
> where does Ubuntu keep it's versions of Java, cause I'd just download that version of Java
the sun java packages are installed from archive.canonical partner repository but in older versions of ubuntu it used to be the medibuntu repository, I think the update 13 was from medibuntu but I don't see any there. 
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)
[http://archive.canonical.com/](http://archive.canonical.com/)  
the other way is to download the old sun java packages fronm [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html) remove the current one and install the update 13.bin package

---

### Post by DJ-HLS on 2010-11-26
Thanks for the responses! But how would I go about doing that?

Sorry, but I'm still an Ubuntu noob...

---

### Post by _0R10N on 2010-11-26
I guess you might try installing the specific version you need, and then setting its installation path as the $JAVA_HOME variable value. It's a long shot but at least you could give it a try.

Kind Regards!

---

### Post by DJ-HLS on 2010-11-26
> **_0R10N said:**
> I guess you might try installing the specific version you need, and then setting its installation path as the $JAVA_HOME variable value. It's a long shot but at least you could give it a try.

Kind Regards!

Thanks, but again, I don't really know how to do that, lol.  I'm just barely learning what even the "sudo" command does.  I mean its generally used for installing stuff, but I don't know what else.

I'm an extreme Ubuntu noob XD

---

### Post by kanishkdudeja on 2010-11-26
```
sudo apt-get remove sun-java6-jdk sun-java6-jre sun-java6-bin
```

and then download the version u want from the site

---

### Post by DJ-HLS on 2010-11-28
OK two things, I may just be a complete idiot, but I can't find where to download the _13 patch on [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
and how would I go about installing it? Do I just open up the .bin file?

---

### Post by gandaran on 2010-11-29
> **DJ-HLS said:**
> OK two things, I may just be a complete idiot, but I can't find where to download the _13 patch on [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
and how would I go about installing it? Do I just open up the .bin file?
found it with a 2 seconds google search!
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u13-oth-JPR@CDS-CDS_Developer](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_Developer-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=jre-6u13-oth-JPR@CDS-CDS_Developer)
download the .bin file ( not the .rpm.bin)
run the bin file with [COLOR="DarkSlateBlue"]sudo sh[/COLOR] in terminal to install but find and follow the linux install instructions in the java website, the bin file doesn't install the browser java plugin so follow the instructions on how to system link the java to firefox.

---

