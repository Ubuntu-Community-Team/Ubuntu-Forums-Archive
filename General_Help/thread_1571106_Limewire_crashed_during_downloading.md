---
title: "Limewire crashed during downloading"
date: 2010-09-09
forum: General Help
---

### Post by z3romaster on 2010-09-09
heya guys,

I'm using Ubuntu Netbook Remix 10.04 with HP Mini 110-1006TU.

I need your opinion on my current problem with Limewire. It just crashed during my downloading. The following are the error code:-

terminate called after throwing an instance of 'std::runtime_error'
./runLime.sh: line 124: 10735 Aborted                 ${JAVA_PROGRAM_DIR}java -Xms64m -Xmx256m -ea:com.limegroup... -ea:org.limewire... -Djava.net.preferIPV6Addresses=false -Djava.net.preferIPv4Stack=true -Dorg.apache.commons.logging.Log=org.apache.commons.logging.impl.NoOpLog -Djava.library.path=. -Djna.library.path=. $EXECUTABLE -jar LimeWire.jar $ARGUMENTS

******************************************************************
Something went wrong with LimeWire.
Maybe you're using the wrong version of Java?
(LimeWire is tested against and works best with with Sun's JRE, Java 1.6+)
The version of Java in your PATH is:
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

What could be the problem? Hope you guys can help.

Thanks in advanced.

---

### Post by howefield on 2010-09-11
A better bet would be Frostwire, imho.

---

### Post by WorMzy on 2010-09-11
Isn't that the same program with different branding? That's how it was back in the day. Maybe the differences are more obvious these days.

gtk-gnutella would be a better solution, no? It's in the repos.

---

### Post by howefield on 2010-09-11
> **WorMzy said:**
> Isn't that the same program with different branding?

Well, it is a fork of Limewire, but open sourced and no nag ware. I'd still say it was better than Limewire, but yes, very similar.

> gtk-gnutella would be a better solution, no? It's in the repos.

I'm taking a look, but not a great start...

> Ancient version detected!

Warning

*This version of gtk-gnutella is pretty old. Please visit [http://gtk-gnutella.sourceforge.net/](http://gtk-gnutella.sourceforge.net/) and update your copy of gtk-gnutella.

---

### Post by borth92 on 2010-09-11
try opening the software center and just searching Limewire and clicking install.

---

### Post by Rasa1111 on 2010-09-11
lol, pretty sure limewire is not in software center. 
(a good thing)

last i knew, if one wanted limewire in ubuntu they had to download and install the limewire made for linux.
not just any limewire.

 if you went to limewires website to download it,
that's why it's not working.
 This isnt like windows where you just download and install things from the web.

---

### Post by howefield on 2010-09-12
> **WorMzy said:**
> gtk-gnutella would be a better solution, no? It's in the repos.

Too many severe and critical bug fixes in the current stable version to recommend the "repo" version unless you are using Maverick Meerkat which is the only Ubuntu version to have the current version. 

> **Rasa1111 said:**
> This isnt like windows where you just download and install things from the web.

Except, it is. Going to either the Limewire or Frostwire website and clicking on the download links will serve you the correct .deb package, the same experience that Windows users get.

Not that I'm recommending this as a good way of getting software, the official repositories should always be first choice, but there is an increasing number of sites offering packages for your Ubuntu operating systems.

---

### Post by Rasa1111 on 2010-09-12
cool, my apologies then. Thanks howefield. 

 regarding Frostwire~
I installed it from synaptic last night just to see how it was..
and it is surprisingly really good! lol
 Just like limewire, but maybe a lil better. lol

 I used to use limewire ages ago,
but havent cared about it in a long time,
but this frostwire could come in handy from time to time! 
Good stuff! 
Thanks. :)

---

