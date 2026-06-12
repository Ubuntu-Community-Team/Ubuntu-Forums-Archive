---
title: "java and konqueror"
date: 2006-04-21
forum: General Help
---

### Post by tikal26 on 2006-04-21
](*,) I am using konqueror more and more as my webbrowser, but I was looking at this page
[http://www.processing.org/](http://www.processing.org/)
an was not able to see the java applets on the exhibition. I know that I have java install, but how do I make it work on konqueror?
thanks for your help in advanced.

---

### Post by wanger123 on 2006-04-21
[QUOTE=tikal26]I am using konqueror more and more as my webbrowser, but I was looking at this page
[http://www.processing.org/](http://www.processing.org/)
an was not able to see the java applets on the exhibition. I know that I have java install, but how do I make it work on konqueror?
thanks for your help in advanced.[/QUOTE]

Hi tikal, go to configure Konqueror -->java javascript --> and where it says 'path to java executable or java' put this /usr/bin/java

Also check this to make sure you have everything: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

cheers
wanger

---

### Post by tikal26 on 2006-04-22
Thanks for the info, but that still doesn't work. I can't get any java applets to work inside konqueror.
Any other ideas

---

### Post by tikal26 on 2006-04-24
or maybe if I put the executable for sun's java it would work, but I have no idea where that would be. Anyone know where that is

---

### Post by bagofchickens on 2006-04-25
Have you tried Settings>Configure Konqueror>Plugins>Netscape Plugins>Scan>Scan for New Plugins? This worked for me as I had exactly the same issue after installing Sun's Java 1.5.0.06.

---

### Post by tikal26 on 2006-04-25
i did that and now when I try to load an applet I get a loading an applet message ( at leat I am moving foward), but it usually just hangs. Anyonw willing to try testing this pages out for me.
[http://www.johnhouck.com/works/morphosis_05/obj-viewer/index.php?modelID=0](http://www.johnhouck.com/works/morphosis_05/obj-viewer/index.php?modelID=0)

or 
[http://www.k2.t.u-tokyo.ac.jp/members/alvaro/Khronos/Khronos_P5/Khronos_Jefo.html](http://www.k2.t.u-tokyo.ac.jp/members/alvaro/Khronos/Khronos_P5/Khronos_Jefo.html)

for teh second page it seems to get to 89% and just stay there

---

### Post by bagofchickens on 2006-04-26
Apart from the horrible 100% CPU usage (I am running Kubuntu 5.10, KDE 3.4.3, on an average Celeron 2.4), I must say Konqueror performs quite well in both cases. Firefox 1.5.0.2 seems to have problems handling the keyboard right, though it could be a configuration problem on my behalf.

I don't know, just to be sure, try again 'sudo update-alternatives --config java'. As stated in the wiki article: 'You might want to do the same with jar, javac, javadoc, javah, javap and javaws'. In my case, it's set to the third alternative: '/usr/lib/j2re1.5-sun/bin/java'. Hopefully someone else more knowledgeable could provide you with a better clue?

---

### Post by ossi on 2006-04-27
Sorry for asking such a banal question - but have you ticked that box for Java under preferences, HTML Settings. I also do have Java installed but have to enable it anytime I want it to work. When I do so, I don't have any problems.

---

### Post by tikal26 on 2006-05-06
I repeated everything on this post and it's finally working. I don't know what was wrong but it works now. thanks

---

