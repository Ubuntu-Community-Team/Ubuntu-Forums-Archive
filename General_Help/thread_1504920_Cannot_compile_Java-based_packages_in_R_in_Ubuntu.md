---
title: "Cannot compile Java-based packages in R in Ubuntu"
date: 2010-06-08
forum: General Help
---

### Post by slowtrain on 2010-06-08
Hi folks:  I'm trying to compile JGR, rJava, etc. for use w/ my updated R.  My configuration of Ubuntu (9.10 Karmic, kernel 2.6.31-22-generic) and R (version 2.11.1; from lib.stat.cmu.edu source) shouldn't be terribly unusual.  But, all my efforts to compile Java programs for R fail, possibly because of something in my Ubuntu configuration of Java.

First, I ran: R CMD javareconf.  The output from that tells me that "JAVA_HOME is not a valid path, ignoring" and the cpp flags are set to nothing.  The javareconf fills most of the variables with references to openjdk.  JAVA_HOME, as far as I can tell, points to a properly installed copy of Sun Java.  When I run update.packages(checkBuilt=T) with this, it unsurprisingly tells me that "One or more Java configuration variables are not set" and all of my Java based programs fail to compile.

I've tried switching the default Java to the Sun version using "sudo update-alternatives --config java".  Now, javareconf fills in the cpp flag and variables point to the Sun version, though I still get the error msg that JAVA_HOME is not a valid path (though javareconf sets the home path to: /usr/lib/jvm/java-6-sun-1.6.0.20/jre).  When I try to compile rJava, I get the error: rJava, "JNI types differ from the native type."

Does anyone have any thoughts on how to fix this?  Alternatively, is there somewhere I can report these problems so they might get fixed in future versions?  I suspect I can't be the only person having these problems.

Cheers, Peter

---

### Post by slowtrain on 2010-06-10
I seem to have fixed the problem.

I used synaptic to uninstall as many version of Java as I could, though ultimately this may not have made a difference.  I could not fully uninstall Sun's Java because two applications I need depend on it: OpenOffice and JEdit.  I did eliminate Sun's jdk.  I did erase some software associated with gij.  I also uninstalled and then reinstalled openjdk.  Again, I'm not sure that mattered.

When I reran "sudo update-alternatives --config java", openjdk was the default java and its status was 'auto'.  It may have been sufficient to set these using update-alternatives, rather than erasing most versions of Java on my machine.  Next, I gave JAVA_HOME a new value:

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk/jre

I reran R CMD javareconf, ignoring the message that JAVA_HOME was not a valid path.  And then I installed the Java packages, without a hitch.  Ubuntu / Debian probably should be able to handle this w/o user intervention, but don't.

---

### Post by ubu1979 on 2010-09-20
This works like a dream! Thanks for posting this - I found it after hours of trying to install JGR and getting nowhere.

---

### Post by Soid on 2010-10-10
Big thankyou Slowtrain - it really helped me too.

---

