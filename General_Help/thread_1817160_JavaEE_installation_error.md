---
title: "JavaEE installation error"
date: 2011-08-03
forum: General Help
---

### Post by Tony_Harrison on 2011-08-03
I'm trying to install JavaEE on 11.04

I run this command: ```
./java_ee_sdk-6u3-jdk7-linux.sh -j /usr/lib/jvm/java-6-openjdk/
```

The wizard starts up fine. After the I click Next on the second step (Installation Type) this output appears in the calling terminal:

// Error: Exception in runnable:Attempt to resolve method: get() on undefined variable or class name: Msg : at Line: 21 : in file: inline evaluation of: ``       run() {        wizard.enableCancel(true);         wizard.enableHelp(true) . . . '' : Msg .get ( "INSTALL_TOP_TEXT" , null )

However, the wizard continues to the next screen, Installation Directory. I keep the default /home/user/glassfish3. The next screen asks whether I want to use the Update Tool and after that I get this:

SEVERE: Error
Beanshell script not invokable Component=ONLOAD Caused by: Attempt to resolve method: getInterpreter() on undefined variable or class name: Scripting

I have not been able to move beyond this point. An error pops up and the wizard crashes.Please let me know if there is anything I have missed. I have been using the Java SE SDK for awhile now and am only just learning the language. While I don't understand it well, I wonder if I should not have something particular in my CLASSPATH?

Any help is appreciated, thanks.

---

### Post by Tony_Harrison on 2011-08-04
[IMG]https://lh6.googleusercontent.com/-UIUYfGBKcCA/TjrRJgNddzI/AAAAAAAAABY/W0WlP4agzO4/Screenshot-Error.png[/IMG]

The popup error I receive. :D

---

