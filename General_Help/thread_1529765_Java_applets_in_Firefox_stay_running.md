---
title: "Java applets in Firefox stay running?"
date: 2010-07-12
forum: General Help
---

### Post by Exp HP on 2010-07-12
All day today, my laptop has been absurdly hot.  The core temperatures were exceeding 70.0°C even though it was on a cooling pad and I had disabled wireless, lowered the screen brightness, and put the CPU on Powersave.  (For comparison, the temp usually stays at 45.0°C if I do all this)

Finally, I decided to check htop, and I found **IcedTea Plugin** at the top with 99% CPU usage.  This is used to run embedded Java applets (Java, not Javascript).  Curiously, no Java applets were running at that time.

Now skip ahead an hour to when I finally discover that the IcedTea Plugin was left over from earlier because it didn't stop running when it was supposed to.  Looking online, I see several complaints about Java being very taxing on the CPU in Ubuntu, but I don't see anything about Java applets continuing to run after they're gone.

Can anyone who has Java installed confirm that this happens on their system?

1. Open **htop**. Search for "icedtea" to make sure it isn't already running.  Then click on "CPU%" to sort the list.
2. Open this page in Firefox: [www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")
3. Check htop.  Is IcedTea climbing to the top? (if you have Java, it likely will, because this is a common issue)
4. Navigate off of the Java.com page by closing the tab or clicking Back.
_5. _*_Here's what I want to know._ Check htop again*.  *_Is IcedTea still there?_*
6. Restart Firefox to get rid of IcedTea.

---

### Post by Exp HP on 2010-07-12
BUMP the First.

---

### Post by akakingess on 2010-07-12
I am not trying to be rude, but is there a reason that you are choosing to use the "IcedTea Plugin" rather that the JRE itself, I know it can be a little confusing to setup, but I have had much better luck with it once up and running?

---

### Post by Exp HP on 2010-07-12
It's been a while since I installed Java, but I certainly don't remember *c**hoosing* IcedTea.  I didn't recognize the name when I saw it in htop.  I figured it was the plugin I got from installing the JRE

So are you saying that IcedTea isn't Sun's plugin for Java in Firefox in Linux?
**Edit:** Indeed, [it's certainly not by Sun]("http://en.wikipedia.org/wiki/IcedTea").

I guess my memory's dodgy and I installed IcedTea as an alternative to the JRE...

...Well, this is embarrassing.

---

### Post by akakingess on 2010-07-12
No, IcedTea is the 'opensource' replacement (for lack of a better term) for Java, you should be able to uninstall Iced Tea and just use the JRE or any Java stuff, just try to download and follow the instructions to the 't' (no pun intended) from Sun's site.  Good luck and let us know if that doesn't work for you.

---

### Post by Exp HP on 2010-07-18
This post is a little late because I decided to take some screenshots, and that took me long enough that I eventually lost interest and never posted the reply.  But I'm back now.

Anyways, history repeated itself.  I followed the directions to a T (or at least *tried* to, since the instructions are so outdated).  What I was left with was a working Java Console extension, *but no plugin*, which I now remember is exactly what happened last time.  Sun.com still says I don't have Java.

The place I installed it to was /usr/local/java.  Of course, this meant I had to install it as root.

I took some screenshots.  They are, in order:
-A listing of the files in the Firefox extensions and plugins folders.  Though **dir** does not make this clear, libjavaplugin_oji.so file is a symbolic link.
-My list of extensions in Firefox.
-My list of plugins in Firefox.
-The Sun Java test page.

I'll also state that I've tried both the ns7 and ns7-gcc29 versions of the plugin and neither worked.  Also, the permissions and ownership of both libjavaplugin_oji.so files from the java folder are as follows (from ls -l):
**-rwxr-xr-x 1 root root**

---

### Post by Exp HP on 2010-07-18
BUMP the Second.

---

### Post by QIII on 2010-07-18
Java is in the Partner repository in Lucid and there is no need to  manually install it.  It will be updated as Oracle updates it and the  new version will be in the repo.  That way, when Java is updated yours  will be as you do your normal updates.

At this point, I would use whatever uninstallation instructions were  provided and undo what you have done.

Also, it may be worth it to use Synaptic to uninstall OpenJDK and the  IcedTea plugin.  Although there is some debate about this, the two can  be reinstalled so it won't hurt to uninstall them.  The world at large does not universally accept OpenJDK or the IcedTea plugin as Java, so some websites will not work with them.

Activate the Lucid Partner repository by going to System |  Administration | Software Sources.  Click on the "Other Software" tab  and check Lucid Partner.

When your sources have updated, you can install the java6-sun packages via Synaptic.  The plugin is one of them.

Please remember that when you bump, you push another member's question down.  So be judicious.  The forum policy is 24 hours, I believe.

---

### Post by jasmineaura on 2010-09-24
> **Exp HP said:**
> I'll also state that I've tried both the ns7 and ns7-gcc29 versions of the plugin and neither worked.  Also, the permissions and ownership of both libjavaplugin_oji.so files from the java folder are as follows (from ls -l):
**-rwxr-xr-x 1 root root**

Though this is from galeon, it applies to xulrunner-1.9.2:
[https://lists.ubuntu.com/archives/lucid-changes/2010-March/009286.html](https://lists.ubuntu.com/archives/lucid-changes/2010-March/009286.html)
> Drop code that uses the Java Console as xulrunner 1.9.2 doesn't support OJI
    plugins


perhaps that might explain why you couldn't get it working.

2nd what QIII said :)

---

