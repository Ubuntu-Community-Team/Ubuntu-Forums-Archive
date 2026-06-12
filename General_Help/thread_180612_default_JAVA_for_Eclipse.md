---
title: "default JAVA for Eclipse?"
date: 2006-05-22
forum: General Help
---

### Post by mad_phoenix on 2006-05-22
Hi,
  I have installed Eclipse along with Sun's JDK.  I've used update-alternatives to set the sun jdk to be default for java, jar, javac, javah, javadoc, etc.

When I type java -version at command line I get Sun's java message.

However, whenever I start Eclipse, I can see through top that gij is still running it.

I can do eclipse -vm <path/to/sun/jre> and it works, but I am confused as to why it isn't doing this by default.

Any ideas?  One thing I keep reading about is a JAVA_HOME variable.  Is there an easy way to see what my JAVA_HOME system variable is set to?

Thanks!
--mad_phoenix

---

### Post by thirdmusketeer on 2006-05-22
Firstly you will need to know what is the default shell you are running, most likely it will be bash. Unless it is cshell or something else, the following can be modified slightly for your needs, the following code is at the end of my .bash_profile

In your home directory do vi .bash_profile or at least do ls ~/.bash_profile
you should see a file.

JAVA_HOME=/usr/lib/j2sdk1.5-sun
PATH=$JAVA_HOME/bin:$PATH;
ECLIPSEPATH=/usr/local/eclipse
ANT_HOME=/usr/local/apache-ant
PATH=$ANT_HOME/bin:$ECLIPSEPATH:$PATH;
CLASSPATH=/usr/share/java/java_cup.jar:/usr/share/java_cup-runtime.jar:/usr/share/jflex-1.4.1/lib/JFlex.jar:./;

once you save the file after adding the required code,
do source .bash_profile

and then echo $CLASSPATH and
echo $PATH

you should see changes.

Let me know if you have further problems.

---

