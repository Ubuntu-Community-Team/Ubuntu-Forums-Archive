---
title: "Azureus and Java"
date: 2006-06-10
forum: General Help
---

### Post by mikez0r on 2006-06-10
I have followed the guide at ubuntuguide.org to install azureus and java.
I changed my java alternatives, so it uses the Sun Java Machine.
When I try installing plugins/ changing port settings etc, in azureus, the flyout window comes out from the bottom left.

My problem is that when you try to click hide or more details, nothing happens. It seems like it is disabled. Someone said something about motif or gtk is the problem, but i don't remember. Anyone else had this problem?
Whats wrong?

~mike

---

### Post by Jedeye on 2006-06-10
I dont have a tone of experence, but I used Automatix to install JRE, and azures, and no problems here. give it a try if you like [http://ubuntuforums.org/showthread.php?t=177646]("http://ubuntuforums.org/showthread.php?t=177646")

---

### Post by mikez0r on 2006-06-10
I tried your suggestion, but It does exactly the same thing :'-(
Any other ideas, anyone?

~mike

---

### Post by mlind on 2006-06-10
This issue must have been coverd like dozen times..
if you're having problems with modal dialogs that won't close, replace your current version of Azureus2.jar with latest [CVS build]("http://azureus.sourceforge.net/index_CVS.php").

---

### Post by ncaravan on 2007-06-16
I was having problems with Java and Azureus too. After uninstalling and reinstalling several different ways I noticed that there were issues with Access Denied in logs. I ran Azureus with the following command ad it seems to work fine. I think there is a security issue with Java in Ubuntu.


Bring up the Run dialog
Alt+F2

gksudo azureus 

Then click run.

Works like a charm.

I also do this for Firefox to deal with Java embedded web pages.

Not a fix, just a work around.

Neil

---

### Post by mlind on 2007-06-17
@ ncaravan
You're running azureus with root privileges which is not very smart. What 'access denied' messages do you get?

---

