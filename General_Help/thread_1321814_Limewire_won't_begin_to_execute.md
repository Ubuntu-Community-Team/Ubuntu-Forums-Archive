---
title: "Limewire won't begin to execute"
date: 2009-11-10
forum: General Help
---

### Post by evesautomotive on 2009-11-10
Greetings:
I have LimeWire 5.3.6 installed.  I am using Ubuntu 9.10  I also have Java version 1.6 as well.

When clicking on the limewire icon in 'applications' nothing happens.

I then open a terminal and type limewire.  This is what I get:

Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Loading LimeWire:
java.lang.UnsatisfiedLinkError: no splashscreen in java.library.path
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1698)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:67)
	at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:47)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.SplashScreen.getSplashScreen(SplashScreen.java:111)
	at org.limewire.ui.swing.Main.main(Main.java:32)

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.6+)
The version of Java in your PATH is:
java version "1.6.0_0"
OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-1ubuntu3)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)


It appears that some sort of splash screen error is keeping this program from loading.  Googling was fruitless.

Any imput would be greatly appreciated.

Jim

---

### Post by alphaniner on 2009-11-10
> OpenJDK Runtime Environment (IcedTea6 1.6.1) (6b16-1.6.1-1ubuntu3)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)

It looks like you're using an open-source java.  You should remove it and install the official version from Sun.

---

### Post by evesautomotive on 2009-11-10
> **alphaniner said:**
> It looks like you're using an open-source java.  You should remove it and install the official version from Sun.

This did the trick although it wasn't as easy to do for this green as a gourd newbie.

I removed java and its dependencies by using synaptic package manager which coincidentally removed limewire-basic as well.

I then found suns [[COLOR="Red"]java download web page[/COLOR]]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80")  and thats where it began to show how green I really am.  Sure I could d/l the bin file but getting it to self extract was another story.  I didn't have su permission, or root permission.  I didn't know what the root password was.  Googling told me that ubuntu has it somewhat locked out.  I unlocked it, imputed a new password, logged out and back in as root and followed the instructions as stated on fore said web page.  Since I have installed it under local instead of just my account it is accessible for all users on this machine.

Cool (java) beans man.

Thank you very much.  I have a lot to learn.

---

### Post by cybiko123 on 2009-11-10
Glad to hear you have it working.

For next time, you could have avoided the hassle and just used sudo instead of su. This would have allowed you to use your normal user account password to run root commands.

---

### Post by BarisBlaq on 2009-11-10
Have you tried gtk-gnutella? It's in the synatic repos and connects to limewire as well as bearshare and a couple more networks IIRC.

Not exactly a solution to your problem, but wanted to point it out in case you haven't seen it, since there's so many apps out there..

---

### Post by trpnblies7 on 2009-11-10
Have you tried FrostWire? I find it works much better than LimeWire.

---

### Post by Jr.Muffin on 2009-11-10
I agree with this post. Installing FrostWire on Ubuntu was as simple as downloading it from the home page.

---

### Post by SlugSlug on 2009-11-10
you may also want to look at using frostwire instead on limewire

---

### Post by alphaniner on 2009-11-10
Kudos on the accomplishment.  However, enabling the root account was probably not the best idea, you should read [this]("https://wiki.ubuntu.com/RootSudo").

Also, you could have installed java through Synaptic, it's just a different group of packages than the one you had installed.

Sorry I led you so far afield, not really used to people taking so much initiative...

---

