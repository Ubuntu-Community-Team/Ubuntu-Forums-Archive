---
title: "Limewire"
date: 2006-06-02
forum: General Help
---

### Post by Curlydave on 2006-06-02
> david@David-Computer:~$ sh /opt/LimeWire/runLime.sh
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
david@David-Computer:~$


This is the error message I get when running limewire, the "other" version. It was working previously, but I just did a clean install of Dapper, and forgot how I got past this error before. I downloaded and successfully ran the Java installer from their website, (JRE 5, revision 7) but I still can't run Limewire. Can anyone help me fix this? Thanks! (Note: I am using the "other" version of limewire, not the RPM version.)

---

### Post by meng on 2006-06-02
Have you configured the system to recognize that as the default java?

sudo update-alternatives --config java

---

### Post by eqisow on 2006-06-02
See [here]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") and [here]("https://wiki.ubuntu.com/RestrictedFormats#head-6acdf8655644645c067fb9e965a66be38681b7fb"). This should get you sorted out. If note, come back and I'll try to help. :)

---

### Post by KrazyPenguin on 2006-06-03
[QUOTE=eqisow]See [here]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") and [here]("https://wiki.ubuntu.com/RestrictedFormats#head-6acdf8655644645c067fb9e965a66be38681b7fb"). This should get you sorted out. If note, come back and I'll try to help. :)[/QUOTE]


Please try Frostwire, much, much better IMO.

I just can't understand why people are still using Limewire, but maybe they don't know about Frostwire and how it is 100% opensource??

Good luck!!

;-)

---

### Post by hibatsu on 2006-06-03
Had the same problem with frostwire. The first "fix" helped thanks :)

Oh and frostwire has got a .deb :)

---

### Post by angrykeyboarder on 2006-06-03
[quote=KrazyPenguin]Please try Frostwire, much, much better IMO.

I just can't understand why people are still using Limewire, but maybe they don't know about Frostwire and how it is 100% opensource??

Good luck!!

;-)[/quote]

Yes but it's not in the Ubuntu repositoies. 

However, giftui, giftoxic, apollon, mldonkey-gui and kmldonkey are.....

---

### Post by eqisow on 2006-06-03
KrazyPenguin, Limewire is 100% open source too. Charging for a premium version doesn't mean they're not open source. How else would Frostwire have been able to fork the code?

I do agree on the Frostwire recomendation though. It should be added to the repositories.

---

### Post by angrykeyboarder on 2006-06-03
[quote=hibatsu]Had the same problem with frostwire. The first "fix" helped thanks :)

Oh and frostwire has got a .deb :)[/quote]

giftui, giftoxic, apollon, mldonkey-gui and kmldonkey have "debs" too and are in the ubuntu repositories.  Easily installed with a simple "sudo apt-get...."

---

### Post by angrykeyboarder on 2006-06-03
No offense to Limewire fans but limewire stinks.  There are several better alternatives (none of which rely on Java) with [Gnutella]("http://en.wikipedia.org/wiki/Gnutella") network access as well. All of them are in the Ubuntu repositories.

Check out giftui, giftoxic &, mldonkey-gui for GNOME/GTK and kmldonkey apollon for KDE.

---

### Post by angrykeyboarder on 2006-06-03
[quote=eqisow]KrazyPenguin, Limewire is 100% open source too. Charging for a premium version doesn't mean they're not open source. How else would Frostwire have been able to fork the code?

I do agree on the Frostwire recommendation though. It should be added to the repositories.[/quote]

In the world of Gnutella I find [giftoxic]("http://packages.ubuntu.com/dapper/net/giftoxic"),[ giftui]("http://packages.ubuntu.com/dapper/x11/giftui"), [mldonkey]("http://packages.ubuntu.com/dapper/net/mldonkey-gui"), [kmldonkey]("http://packages.ubuntu.com/dapper/net/kmldonkey") and [apollon ]("http://packages.ubuntu.com/dapper/net/apollon")are vastly superior to Limewire and don't require Java.

And all of them are in the Ubuntu repositories.

---

### Post by eqisow on 2006-06-03
angrykeyboarder, we got it. You don't like Lime(Frost)wire. Your suggestions are appreciated, but we don't really need 3 post with the exact same content.

---

### Post by almostlinux on 2006-06-03
[QUOTE=angrykeyboarder]Yes but it's not in the Ubuntu repositoies. 

However, giftui, giftoxic, apollon, mldonkey-gui and kmldonkey are.....[/QUOTE]

thanks a lot ! never knew they even existed :D 

I for one, want to stay away from java ](*,)

---

### Post by Sukarn on 2006-06-03
[QUOTE=almostlinux]thanks a lot ! never knew they even existed :D 

I for one, want to stay away from java ](*,)[/QUOTE]
I, for one, like the java based Limewire. My full bandwidth almost always gets used in it.
And I dont find Frostwire to be much different from it.

---

### Post by ahaslam on 2006-06-03
[QUOTE=eqisow]See [here]("https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249") and [here]("https://wiki.ubuntu.com/RestrictedFormats#head-6acdf8655644645c067fb9e965a66be38681b7fb"). This should get you sorted out. If note, come back and I'll try to help. :)[/QUOTE]
That worked perfectly, cheers!
Why didn't I have to set the default Java in Breezy though?

PS. GTK-Gnutella is quite impressive & it's the repos, give it a try. It never worked on my Breezy install though.

:KS

---

### Post by Curlydave on 2006-06-03
I'm trying to install Java from the Add/Remove, but I get this message: "Sun Java is not available in any software channell. The application might not support your system architecture." Weird! Also, I can't find the package in synaptec.

It is unchecked, meanign I don't have it, so neither the add/remove program manager nor limewire/frostwire recognizes that I installed it from sun's website. Carp.

---

### Post by Sukarn on 2006-06-03
**@Curlydave:**
try **sudo update-alternatives --config java**
That should give you an option to choose the java (if its installed. You say you installed it from Sun's website.)

Also, do you have the universe and multiverse repositories enabled? I dont know which repository sun java is in, but I installed it from the repos.

Your post count suggests that you are much more experienced with Ubuntu than me, but theres nothing wrong with just checking whether the basics are fine or ignored. (I dont mean to be flaming you or anything, its just that I can't get the right words right now.)

---

### Post by Curlydave on 2006-06-03
I fixed it by using Easy Ubuntu. Sweet. Much recommended.

---

### Post by Sukarn on 2006-06-05
Easyubuntu... now why didn't I think of that? Maybe because I didn't use it and instead installed all that I needed manually.

---

