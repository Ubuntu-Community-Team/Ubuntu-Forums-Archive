---
title: "jdownloader wont start"
date: 2011-07-27
forum: General Help
---

### Post by raid22 on 2011-07-27
Hi all,

i run ubuntu 10.04 LTS

I used jdownloader without problems, had it on startup applications and one day noticed I could not open it. 

I cant open it selecting it in applications/internet/jdownloader

If I type jdownloader in terminal it says:

[B]10 7/27/11 10:02:05 AM - INFO [jd.Main(main)] -> existing jD instance found!
10 7/27/11 10:02:05 AM - INFO [jd.Main(main)] -> There is already a running jD instance[/B]

but I look for that instance using top command and cant see it

I have already tried updating sun java and setting it as default

any help would be appreciated, thanks in advance

---

### Post by veggen on 2011-07-27
Try this in the terminal:

ps aux | grep java

And see if it lists any process that might be JD. Try killing it and restarting JD afterwards.

---

### Post by raid22 on 2011-07-27
thanks for your help veggen, I tried this:

[B]ridar@ridar-laptop:~$ ps aux | grep jdownloader
ridar     8006  0.0  0.0   3324   824 pts/0    S+   10:46   0:00 grep --color=auto jdownloader
ridar@ridar-laptop:~$ killall 8006
8006: no process found
ridar@ridar-laptop:~$ killall jdownloader
jdownloader: no process found
[/B]

I am probably using killall incorrectly?

---

### Post by Gyokuro on 2011-07-27
you should kill java as already mentioned by veggen

ps -A | grep java

kill -9 javaprocessid

---

### Post by raid22 on 2011-07-27
hi, there is no java process, what the ps command shows is:

[B]ridar@ridar-laptop:~$ ps aux | grep java
ridar    31484  0.0  0.0   3324   828 pts/0    S+   14:25   0:00 grep --color=auto java[/B]

so it is the grep process itself what is appearing

---

### Post by Gyokuro on 2011-07-27
Ok,

that means no java is running. Are you using openjdk or sun-java6?? 

please show us:

java -version

---

### Post by raid22 on 2011-07-27
this is the terminal output:

[B]ridar@ridar-laptop:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)
[/B]

---

### Post by raid22 on 2011-07-28
also, I used **sudo update-alternatives --config java** command to set up sun java as the default java:

[B]ridar@ridar-laptop:~$ sudo update-alternatives --config java
[sudo] password for ridar: 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: ^C[/B]

??

---

### Post by raid22 on 2011-07-28
reinstalled to no avail... any ideas? how do I get java running?

---

### Post by raid22 on 2011-07-29
bump!

---

### Post by satish_j on 2011-07-29
how did you uninstall the jre?
you can try using 'purge' during uninstallation to remove it completely..
Did you check 'java -version' after removing it?

---

### Post by Gyokuro on 2011-07-29
Which release do you use - I have downloaded it to test it from jdownloader.org (multios zip), extracted it and started it via:

java -jar JDownloader.jar

and it works. OS: Ubuntu LTS 10.04.3 and 

java -version 

java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

---

### Post by raid22 on 2011-07-31
bump!

---

### Post by raid22 on 2011-07-31
sorry, I bumped this without seeing the answers (thanks for them)

to remove java:

[B]sudo aptitude purge `dpkg -l | grep java | awk '{print $2}'` -y
sudo aptitude purge `dpkg -l | grep gcj | awk '{print $2}'` -y
sudo aptitude purge `dpkg -l | grep -e ^rc | awk '{print $2}'` -y[/B]

as posted in [http://ubuntuforums.org/showthread.php?t=1550838]("http://ubuntuforums.org/showthread.php?t=1550838")

then reinstalled using:

**sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-bin**

java -version says:

[B]sun-java6-binridar@ridar-laptop:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)[/B]

but no java running: **ps -aux | grep java** shows only grep command:

[B]ridar@ridar-laptop:~$ ps aux | grep java
ridar    13484  0.0  0.0   3324   828 pts/0    S+   17:18   0:00 grep --color=auto java
[/B]

jdownloader does not run either, I tried via terminal:

[B]ridar@ridar-laptop:~/.jdownloader$ java jar JDownloader.jar
Exception in thread "main" java.lang.NoClassDefFoundError: jar
Caused by: java.lang.ClassNotFoundException: jar
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:306)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:247)
Could not find the main class: jar.  Program will exit.[/B]

I think there is something missing in the jdownloader installation as this error message is new.

---

### Post by Gyokuro on 2011-07-31
you must start it via: java -jar JDownloader.jar (you forgot - sign)

---

### Post by raid22 on 2011-07-31
true

10 7/31/11 10:20:09 PM - INFO [jd.Main(main)] -> existing jD instance found!
10 7/31/11 10:20:09 PM - INFO [jd.Main(main)] -> There is already a running jD instance

same problem as before :S

---

### Post by Gyokuro on 2011-08-01
Ok,

delete in $Home/.jdownloader the directory ($HOME is your home directory)

**.junique**

---

### Post by raid22 on 2011-08-01
done, whats next?

---

### Post by nipennem on 2011-08-01
Did you already try redownloading JDownloader ?

Is it still on your list of automatically starting applications ?

---

### Post by raid22 on 2011-08-02
I reinstalled using sudo add-apt-repository... I will try downloading and so.

It is still in the startup applications

(thanks all for your help)

---

### Post by raid22 on 2011-08-02
I reinstalled through synaptics once more. I tried to run it from the applications menu but it didnt run, after that I tried **java -jar jdownloader.jar** from terminal and it worked... Have restarted the system now and it runs from startup as expected.

Grateful as I am for all your help any idea of what happened? I want to learn, if not this is the Windows "uninstall-reinstall until it works" thing I thought I had overcome when entering ubuntu.

---

### Post by last1 on 2011-10-24
I just had this same issue and fixed it partly with the help of this thread. What I found was that reinstallation only worked after manually deleting the .jdownloader directory. Even when I selected to completely remove jdownloader using Synaptic the directory was still present. After deleting the directory and doing a reinstall it starts like normal.

If I were to guess I would say that Synaptic gives up on trying to delete when you select "completely remove" or whatever it's called, because Jdownloader writes a lot of plugins and such to that dir after install. But that's just a guess, I don't know what apt-get's policy is on removing directories that have other files in them besides the package's installed files.

---

### Post by veggen on 2011-10-25
Synaptic won't delete files and folders created after the installation, so whenever you are uninstalling stuff, look into your home folder for the remainings. updatedb + locate commands work wonders in hunting those left overs.

I found out I have to start JDownloader like this:
java -Xmx1512m -jar /path/to/JDownloader.jar
for some reason the extra memory switch is needed on this specific machine.

Probably not all that relevant to your problem, but maybe...

---

