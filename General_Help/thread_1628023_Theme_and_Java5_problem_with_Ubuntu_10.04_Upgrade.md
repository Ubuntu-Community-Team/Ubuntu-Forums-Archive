---
title: "Theme and Java5 problem with Ubuntu 10.04 Upgrade"
date: 2010-11-22
forum: General Help
---

### Post by SheikhAmanAlam on 2010-11-22
Hi all.
I recently upgraded my 9.10 to 10.04 via install over the Internet.
I had a 9.04 prior to this, it upgraded to 9.10 via the same method, and then upgraded to 10.04

After the install, I found out that It is throwing some errors with sun-j2sdk1.5.

Moreover, the window title bars, the background colour of captions is also not usual.
What might have gone wrong?

Please suggest a solution to both the problems.

Thanks.

---

### Post by Silent Warrior on 2010-11-22
Can you open Synaptic and verify what version of that Java development-kit you have installed? I'm running Mint 10 (Maverick-based), so my readouts might not be anything to go by, but the closest package name I can find is sun-java6-jdk.

As for the title bars, it sounds like something's up with your GTK-theme. Try setting it to one of the default themes (Ambiance or Radiance) in the Appearance-configurator. For what it's worth, I'm pretty sure you got these problems because you upgraded. Just something to be aware of in the future. Consider a clean install next time around. (Besides backing up all non-hidden folders (NOT beginning with a . - though you'll probably want to keep .themes and .icons), take care .config/ isn't carried over. Also open Synaptic and choose Save Markings as..., save all selections and not just the changes, then after you've made your clean install, either Read the file you saved before, or tick off the packages manually, consulting the list opened in Gedit.)

---

### Post by SheikhAmanAlam on 2010-11-22
Thanks man.
Changing the theme solved the issues with the UI.

I opened Synaptic and it gives me a huge list.
Searched for Java and all i can see is Java 6.
no Java 5.

I think i need to get rid of Java 5 and OpenJDK.
now, how to do that?

---

### Post by Silent Warrior on 2010-11-22
I don't know what version of OpenJDK you have, or what 10.04 has available, but just make sure they're updated. As for getting rid of Java 5 (or rather 1.5, I believe), just find the sun-j2sdk1.5-package in Synaptic and set it to be completely removed. (Make sure you have a recent Java runtime installed - sun-java6-jre or somesuch.
What program are you trying to use that gives you these Java5-prompts, by the way? Or do you get them on logging in?

---

### Post by SheikhAmanAlam on 2010-11-25
I was trying to install compiz-fusion when it returned an error like this.
although, I don't see any error messages on start up, and all my programs including Eclipse and Android SDK work fine.
I have Java 6 and OpenJDK 6 installed.

Trying to remove java 1.5 now.

Will keep you posted.

Thanks for the help so far! :-)

---

### Post by SheikhAmanAlam on 2010-11-25
Yeah..
Removed Java 5 and now I am running on Java 6.

Although, perhaps 10.04 doesn't support compiz fusion. It says that its already there when I try to install it.

Thanks a lot for the help man!

---

