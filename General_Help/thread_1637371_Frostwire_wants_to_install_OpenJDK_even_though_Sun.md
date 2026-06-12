---
title: "Frostwire wants to install OpenJDK even though Sun Java is installed"
date: 2010-12-04
forum: General Help
---

### Post by new2linux411 on 2010-12-04
First off, hello to all, and thanks in advance for any help figuring this out. I have been running Lucid with java installed and frostwire working fine since Lucid was released. I usually just ignore the alerts I get when opening frostwire that say a new version is available for download. A few days ago I decided to update my frostwire to the newest version. I went to synaptic and removed frostwire from there. I then went to the frostwire website and downloaded the current version for Ubuntu. When trying to install it, the package manager said that 6 additional packages needed to be installed. I clicked to see the details of these additional packages and they were OpenJDK, icedtea, and some other dependencies. My question is what is going on to where frostwire wants me to install OpenJDK when I have had Sun Java installed on the machine for quite some time, and previous versions of frostwire have installed and worked just fine. I'm stumped, any help would be appreciated. Thanks.

---

### Post by tredegar on 2010-12-04
I would just let it install OpenJDK, and whatever else it wants, and then 
if **java --version** doesn't report Sun's, then make it so with
```
sudo update-alternatives --config java
```
You can have several javas installed, but the above will set which one you wish to be used by default. You can still invoke the others if you give the /full/path/to/the_other_java

Hope this helps.

---

### Post by new2linux411 on 2010-12-05
To tredegar, that does help, and thanks. I'm still wondering why it does that though. It almost makes me feel like this newest version of frostwire requires OpenJDK, or Ubuntu is pushing people to use OpenJDK. The requirements say to have a minimum of java 1.5 or above, and I have Sun Java 1.6 installed. Just for kicks I did a fresh install of Lucid on a spare machine, installed Sun Java and went to install frostwire. The same thing happened on that machine, frostwire wanted to install OpenJDK. I know OpenJDK is an open source alternative to Sun Java, but, is it lacking anything in comparison to Sun Java? What are the benefits of Sun compared to OpenJDK? Just trying to figure this all out. It's not a real big deal, I just found it odd that it does this. I've used Ubuntu for quite a while and have updated frostwire with no problems on other versions of Ubuntu and even with Lucid prior to this last time. I just wanted to know the reason it does that even though Sun Java is already insalled. I see no reason to have two Javas installed. I'll have to check my laptop to see what happened there. I did a clean install of Lucid 10.04.1 on that a few weeks ago, installed frostwire, and I'm pretty sure it didn't ask me to install OpenJDK. If it didn't, I'll check to see what version of frostwire is installed on my laptop to see if it's different. Maybe the new ubuntu version looks to use OpenJDK. Anyone else seen this issue? Any thoughts or ideas? Thanks

---

### Post by tredegar on 2010-12-06
I don't know for sure, but it is likely that the developers wrote and tested  frostwire using the OpenJDK version of java. Therefore it would seem sensible to run it using OpenJDK.

"java is java", and the version (Sun /Oracle / OpenJDK) *should* not matter, but it might do.

Years ago, open-source java had a few problems, so I used to install Sun's and use that, but I am now using **java-6-openjdk** without any problems, so I don't need any other implementation. 

If there is an open-source application that *works*, as OpenJDK certainly seems to, then I would rather use that than a closed-source alternative.

Just my preference.

---

