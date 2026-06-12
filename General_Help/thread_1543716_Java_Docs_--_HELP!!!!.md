---
title: "Java Docs -- HELP!!!!"
date: 2010-08-01
forum: General Help
---

### Post by chrisyunke on 2010-08-01
I have looked ALLL Over and i cant find anything that will actually work or help me in any way.

Anytime i install ANYTHING it says that i need to install the JDK Documentation. I have tried everything i have come across.

If someone could maybe give me step by step instructions on how to fix this, even dumb it down as much as possible so i dont get confused on anything. It would be much appreciated.

You can even email me instructions to [email]chrisyunke@gmail.com[/email]

Thanks.

--Chris

---

### Post by chrisyunke on 2010-08-02
bump

---

### Post by lykeion on 2010-08-03
> **chrisyunke said:**
> I have looked ALLL Over and i cant find anything that will actually work or help me in any way.

Really??
A search in these fourum got me lots of posts:

_[Can't download,need help with Java 6 jdk...docs]("http://ubuntuforums.org/showthread.php?t=1516403")_

_[Obtaining jdk-6u10-docs.zip]("http://ubuntuforums.org/showthread.php?t=1250654")_

_[Ubuntu 9.10 How install Javadoc in Netbeans to acces realtime descriptions]("http://ubuntuforums.org/showthread.php?t=1408362")_

_[Help installing Java-6-doc.zip]("http://ubuntuforums.org/showthread.php?t=1390397")_

_[Java docs and/or update problem]("http://ubuntuforums.org/showthread.php?t=1369986")_

_[I'm having the sun-java6.doc prob]("http://ubuntuforums.org/showthread.php?t=1094082")_
[U][URL="http://ubuntuforums.org/showthread.php?t=641736"]
Installing netbeans Javadocs[/URL][/U]

---

### Post by chrisyunke on 2010-08-10
> **lykeion said:**
> Really??
A search in these fourum got me lots of posts:

_[Can't download,need help with Java 6 jdk...docs]("http://ubuntuforums.org/showthread.php?t=1516403")_

_[Obtaining jdk-6u10-docs.zip]("http://ubuntuforums.org/showthread.php?t=1250654")_

_[Ubuntu 9.10 How install Javadoc in Netbeans to acces realtime descriptions]("http://ubuntuforums.org/showthread.php?t=1408362")_

_[Help installing Java-6-doc.zip]("http://ubuntuforums.org/showthread.php?t=1390397")_

_[Java docs and/or update problem]("http://ubuntuforums.org/showthread.php?t=1369986")_

_[I'm having the sun-java6.doc prob]("http://ubuntuforums.org/showthread.php?t=1094082")_
[U][URL="http://ubuntuforums.org/showthread.php?t=641736"]
Installing netbeans Javadocs[/URL][/U]


Tried all of those, still not working.
And i never said i couldnt find any related posts. So thanks for the sarcasm. I said nothing i found worked.

---

### Post by GregBrannon on 2010-08-10
Can you be more specific about the error or problem you're having?  What exactly did you try to do?  What exactly was the error message?  Post screen shots or copies of system messages.

---

### Post by DaveLevy on 2010-09-14
I have been installing Java 5 on Ubuntu 9.00.

Using [FONT=Courier New]apt-get install sun-java5-doc [/FONT]gives the **expected **error that the documentation is not a package.  The warning message from apt-get states that you need to place jdk-1_5_0-doc.zip in /tmp owned and readable by root:root, (really?).

Unfortunately the sun url which it recommends you use has now gone as part of the Oracle aquisition, it was somewhere on java.sun.com and note that I am using V5 which is a back rev.

I googled it i.e. jdk-1_5_0-doc.zip,  and found 
[ftp://ftp.ssw.uni-linz.ac.at]("http://www.filewatcher.com/b/ftp/ftp.ssw.uni-linz.ac.at.0.0.html")/[pub]("http://www.filewatcher.com/b/ftp/ftp.ssw.uni-linz.ac.at/pub.0.0.html")/Java/ via [http://www.filewatcher.com/](http://www.filewatcher.com/) i.e. [http://www.filewatcher.com/b/ftp/ftp.ssw.uni-linz.ac.at/pub/Java.0.0.html](http://www.filewatcher.com/b/ftp/ftp.ssw.uni-linz.ac.at/pub/Java.0.0.html)

I downloaded it and reissued the apt-get install command and it now seems to behave correctly. (I believe that the Java Packages would have worked, this is just an apt-get warning.)

Full corrective feedback would involve getting Oracle to re-publicise the location of these files.

---

