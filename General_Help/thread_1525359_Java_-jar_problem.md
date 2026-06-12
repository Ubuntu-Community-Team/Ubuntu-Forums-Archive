---
title: "Java -jar problem"
date: 2010-07-06
forum: General Help
---

### Post by dlrocket89 on 2010-07-06
Hello,

I'm attempting to play a game I just downloaded, slam soccer 2006 (inspired by the world cup I guess, :D).

I can't get it to run.  What I've done so far:

1) Extract the .tar.gz into directory /home/dustin/Games/Soccer/bolzplatz2006/

In that directory there is a "game.jar" file.  I run that through terminal via:

cd /home/dustin/Games/Soccer/bolzplatz2006/
java -jar game.jar


It replies "Unable to access jarfile game/jar"

If I navigate to the directory in the desktop, I right click on the jar file, click "open with" and then OpenJDK Java 6 Runtime.  The Java icon appears next to the cursor, bounces for a few seconds, and then disappears with nothing happening.

I suspect something is up with my java install...I installed jarwrapper, that didn't fix it (obviously), and for all I know I just screwed things up more.

Help anyone?  Thanks!

Dustin
Rockford, IL

---

### Post by dlrocket89 on 2010-07-06
I should also note that there is a "bolzplatz2006.sh" and "setup.sh" file in the main game directory.  The bolzplatz2006.sh file contains a bunch of information related to the java files included...

Does that help any?

---

### Post by dlrocket89 on 2010-07-06
Latest attempt yields:

Failed to load Main-Class manifest attribute from
game.jar

---

### Post by BikeHelmet on 2010-07-06
Did you try running setup.sh?
```
bash setup.sh
```

It might do something. (or maybe not)

---

### Post by dlrocket89 on 2010-07-06
there is no setup.sh

I ran settings.sh, gave me a dialog box that let me set video resolution, etc.

Then ran bolzplatz2006.sh, a window popped up and then closed right away, leaving the display resolution changed...

](*,)

---

### Post by luigi_mb on 2010-07-06
> **dlrocket89 said:**
> Latest attempt yields:

Failed to load Main-Class manifest attribute from
game.jar

Uninstall OpenJDK Java 6.

Install sun-java6-jre from the repos.


/luigi

---

### Post by dlrocket89 on 2010-07-06
can't find sun-java6-jre in the repos (at least in Synaptic)...try apt-get in the terminal?

---

### Post by dlrocket89 on 2010-07-06
I deleted the OpenJDK as instructed.  I downloaded the binary of the sun JRE from Sun's website, installed it as they said.  I also reinstalled jarwrapper.  I then try to run the game.jar file and I get a listing of the places where I can download and install various JREs from...so, apparently, my installation of the java binary didn't work out (although, I may have been installing the firefox plugin, I don't know).  

In any case, Sun-java6 isn't in the listing of stuff available in the repositories.  Anyone know where I can get the sun version, seeing as how I'm apparently inept when it comes to binaries?  Thanks a lot of the replies so far, and thanks in advance for any in the future!!!

Dustin

---

### Post by luigi_mb on 2010-07-07
> **dlrocket89 said:**
> I deleted the OpenJDK as instructed.  I downloaded the binary of the sun JRE from Sun's website, installed it as they said.  I also reinstalled jarwrapper.  I then try to run the game.jar file and I get a listing of the places where I can download and install various JREs from...so, apparently, my installation of the java binary didn't work out (although, I may have been installing the firefox plugin, I don't know).  

In any case, Sun-java6 isn't in the listing of stuff available in the repositories.  Anyone know where I can get the sun version, seeing as how I'm apparently inept when it comes to binaries?  Thanks a lot of the replies so far, and thanks in advance for any in the future!!!

Dustin

Make sure the list of repositories includes Medibuntu. 

/luigi

---

### Post by Queue29 on 2010-07-07
> **dlrocket89 said:**
> I deleted the OpenJDK as instructed.  I downloaded the binary of the sun JRE from Sun's website, installed it as they said.  I also reinstalled jarwrapper.  I then try to run the game.jar file and I get a listing of the places where I can download and install various JREs from...so, apparently, my installation of the java binary didn't work out (although, I may have been installing the firefox plugin, I don't know).  

In any case, Sun-java6 isn't in the listing of stuff available in the repositories.  Anyone know where I can get the sun version, seeing as how I'm apparently inept when it comes to binaries?  Thanks a lot of the replies so far, and thanks in advance for any in the future!!!

Dustin

You need to enable the Partner Repositories before sun-java will show up. There's no need to install it manually (which gets messy fast).

---

