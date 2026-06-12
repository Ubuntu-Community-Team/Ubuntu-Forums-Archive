---
title: "How to install Java 1.7?"
date: 2011-05-18
forum: General Help
---

### Post by cleverbubbles123 on 2011-05-18
Ok, so I downloaded Java 1.7 b142 from here: [http://download.java.net/jdk7/](http://download.java.net/jdk7/) (I got the Lunux tarball JRE 32bit). How the hell do I install it???

BTW I'm doing this because on my eeepc that I take to work I play Minecraft and have heard that Java 1.7 significantly boosts frame rate.

Thanks

---

### Post by cleverbubbles123 on 2011-05-18
bump, please help!

---

### Post by cleverbubbles123 on 2011-05-19
No-one knows how to do this?

---

### Post by gandaran on 2011-05-19
have you extracted the tar ball? any readme or install file with instructions in the package?

---

### Post by 3rdalbum on 2011-05-19
Surely there should be instructions on the Java website or inside the tarball you downloaded?

---

### Post by r-senior on 2011-05-19
What's your reason for wanting Java 7, bearing in mind it's still pre-release?

Do you want to completely replace all Java on your installation, or do you want to try out some of the new features, i.e. do controlled development with it?

---

### Post by r-senior on 2011-05-19
If it's the latter, the safest approach is probably into your home directory (don't type the '$' signs, that's your prompt):

1. Download the archive, e.g. jdk-7-ea-bin-b142-linux-x64-12_may_2011.tar.gz

2. Extract into a suitable folder:

```

$ cd ~/Downloads
$ tar -xzvf jdk-7-ea-bin-b142-linux-x64-12_may_2011.tar.gz

```

That gives you a jdk1.7.0 folder. Personally I'd move that under ~/Software but that's up to you.

3. Then set your JAVA_HOME and PATH to use it:

```

$ export JAVA_HOME=~/Software/jdk1.7.0
$ export PATH=$JAVA_HOME/bin:$PATH

```

4. Check you have it correct:

```

$ java -version
java version "1.7.0-ea"
Java(TM) SE Runtime Environment (build 1.7.0-ea-b142)
Java HotSpot(TM) 64-Bit Server VM (build 21.0-b12, mixed mode)
$ javac -version
javac 1.7.0-ea

```

5. Enjoy ...

```

$ cat Test.java
public class Test {
	public static void main(String ... args) {
		System.out.println("hello");
	}
}
$ javac Test.java
$ java Test
hello

```

6. The commands in step 3 only apply to the terminal window you are in. IDEs like Netbeans or Eclipse will allow you to add the JDK home for development. If you really want Java 7 across your whole session, add the commands in step 3 to your ~/.bashrc, log out and back in. If that breaks Java on your system, just comment those lines out, log out and back in.

---

### Post by sixteensix on 2011-07-13
If cleverbubbles123 will not say I will, many thanks r-senior! I am still working my way round linux especially as I am working with it on a day to day basis now and this was most informative.

Personal I need JDK7 for testing Open DeDupe ([www.opendedup.org](www.opendedup.org)) and the installation instructions are vague when it comes to installing the pre-requisites.

Again many thanks r-senior!!!

sixteensix

---

