---
title: "Looking Glass &amp; Squeak"
date: 2005-02-19
forum: General Help
---

### Post by telmo on 2005-02-19
Hello!

I just spend a few days away from Ubuntu, so i could try Java's Looking Glass 3D... wich seems to a very promissing 3D desktop environment... Of course i had to install a different linux distro to run it (FC3 in this case).

I was wondering if any of you managed to install Looking Glass in Ubuntu?

I've also tried to install Squeak with no luck.

Can anyone help me on this?

thx

---

### Post by mutze on 2005-03-02
Hello,
First I have to say that my english isn't very well, because I'm from Germany and my shooltime is over for 15 years. I've searched this forum for looking glass but no one was able to give a hint and so I searched via google. Finaly I was able to run looking glass, but the summary was not satisfying. It's very slow and not so far that you could work with it. Anyway here is a screen:
[[IMG]http://img208.exs.cx/img208/6162/lg3dsession4eq.th.jpg[/IMG]](http://img208.exs.cx/my.php?loc=img208&image=lg3dsession4eq.jpg)

mutze

---

### Post by crun on 2005-03-02
[Slashdot](http://slashdot.org/article.pl?sid=05/03/02/1449240) just reported that Sun has released a Live CD containing Looking Glass. At the moment their download server has ground to a halt though.

I did get the demo installed a while ago, [here's a short clip](http://www.imageafter.com/temp/lex/movies/linux/looking_glass_demo.mpg) (framerate is a bit fast)

Info on how to get the Looking Glass demo up and running [here](https://lg3d-core.dev.java.net/lg3d-getting-started.html)

---

### Post by telmo on 2005-03-02
[QUOTE=crun][Slashdot](http://slashdot.org/article.pl?sid=05/03/02/1449240) just reported that Sun has released a Live CD containing Looking Glass. At the moment their download server has ground to a halt though.

I did get the demo installed a while ago, [here's a short clip](http://www.imageafter.com/temp/lex/movies/linux/looking_glass_demo.mpg) (framerate is a bit fast)

Info on how to get the Looking Glass demo up and running [here](https://lg3d-core.dev.java.net/lg3d-getting-started.html)[/QUOTE]

But did you managed to do that in Ubuntu??? That i can't do!

I even tried the Live-cd but with no luck! I tried it in six different computers and no luck!... (as expected!)

If you got that demo working on Ubuntu, please post a how to. I'm sure people will love it. ;)

Oh... by the way... any luck with squeak?

---

### Post by p!=f on 2005-03-02
[QUOTE=telmo]
Oh... by the way... any luck with squeak?[/QUOTE]
There's a Debian package to download:
[http://www-sor.inria.fr/~piumarta/squeak/](http://www-sor.inria.fr/~piumarta/squeak/)

---

### Post by crun on 2005-03-03
I tried the Looking Glass demo it this morning and it works great with Ubuntu. I basically followed the instructions on [this page](https://lg3d-core.dev.java.net/lg3d-getting-started.html) and did a little bit of tweaking.

Here's a short howto - note that you have to register with Sun to get at the Looking Glass files themselves.

NB: the following was all done using Hoary with Universe and Multiverse active.
NB2: this is still only a TECH DEMO, not a fully functional OS

**Downloading** 

[list=1]
[*]Step 1: create a temporary folder to place all your downloaded files in (I'm using "/tmp/glass" for this howto
[*]Step 2: **Download the Java SDK**.
Go to [this page](http://java.sun.com/j2se/1.5.0/download.jsp) and choose "Download JDK for Other Platforms" under "JDK 5.0 Update 1". Read and accept the Licence Agreement, and then download the Linux self-extracting file ("jdk-1_5_0_01-linux-i586.bin").
[*]Step 3: **Download the Java 3D SDK**.
On [this page](https://j3d-core.dev.java.net/servlets/ProjectDocumentList), choose "Z-OLD-Experimental_Builds", choose the most recent build, and then download "java3d-1_3_2-build8-linux-xxxx.jar" (depending on your architecture)
[*]Step 4: **Download the Java Advanced Imaging API JDK**.
Go [here](http://java.sun.com/products/java-media/jai/downloads/download-1_1_2.html) and choose "JDKTM Install: Bundle for installation in a JDK" (should be the first one). Again, accept the LA. then download the Linux JDK Install (jai-1_1_2-lib-linux-i586-jdk.bin)
[*]Step 5: **Register with Java.net**.
Go to [http://www.java.net/](http://www.java.net/) and click on "register". You'll receive an email which you have to confirm, etc.
[*]Step 6: **Download Looking Glass**.
Now that you are registered, you have access to the [Looking Glass download page](https://lg3d-core.dev.java.net/). In the left pane, choose "Document and Files", then navigate to "lg3d-core -> stable_builds" and download the most recent version (at time of writing "lg3d-0-6-1.tar.gz").
[/list] 

**Installing** 

Go to your download directory, you'll see the following files:

[list=1]
[*]the Java 2 SDK (jdk-1_5_0_01-linux-i586.bin)
[*]the Java 3D SDK (java3d-1_3_2-build8-linux-i586.jar)
[*]the Java Advanced Imaging API (jai-1_1_2-lib-linux-i586-jdk.bin)
[*]Project Looking Glass (lg3d-0-6-1.tar.gz)
[/list]

[list=1]
[*]Step 1: **installing the Java 2 SDK**.
Make the JDK executable and run it with sudo. It will self-extract to a directory ("jdk1.5.0_01"). Move this whole directory to "/usr/java/jdk1.5.0_01/". Export the path to the Java home dir (by typing it in the console or placing it in your own and the root's .bashrc file):
```

export JAVA_HOME=/usr/java/jdk1.5.0_01
export PATH=$JAVA_HOME/bin:$PATH

```
If you've put it in your .basrc file, make sure the variables are active before you proceed.
[*]Step 2: **installing the Java 3D SDK**.
Unpack the 3D SDK files:
```

cd /tmp/glass/
$ jar xvf java3d-1_3_2-beta2-linux-i586.jar

```
Go to Java's "jre" dir:
```

$ cd /usr/java/jdk1.5.0_01/jre

```
And then unpack the 3D SDK:
```

$ sudo jar xvf /tmp/glass/java3d-1_3_2-beta2-linux-i586/j3d-132-beta2-linux-x86.jar

```
(if "jar" isn't recognized, then you need to recheck your $PATH variable)
[*]Step 3: **installing the Java Advanced Imaging API**.
```

$ cd /usr/java/jdk1.5.0_01/
$ sudo /tmp/glass/jai-1_1_2-lib-linux-i586-jdk.bin

```
[*]Step 4: **Installing Looking Glass**.
You can install the Looking Glass files wherever you want. I keep all compiled applications under the folder "progs" in my home dir, but it's up to you.
Copy and extract the Looking Glass zip-file to your prefered location:
```

$ tar -zxf /tmp/lg3d-x.y.z.tar.gz

```
[/list]

**Running and troubleshooting** 
You should now be able to run Looking Glass, by going to its folder, for instance:
```

$ cd /home/username/lg3d/bin
$ ./lg3d-dev

```

Hoever, I ran in to two problems here. The first was that csh was missing, so
```

$ sudo apt-get install csh

```
The second was that according to Java, my $OSTYPE wasn't set. I checked and $OSTYPE reported itself to be "gnu-linux". However, this default value of "gnu-linux" apparently wasn't get recognized by Looking Glass, so I gave it a new value
```

$ export OSTYPE="linux"

```

And after that, it ran fine.

---

### Post by Jesus Franco on 2005-03-03
Nice How to  :grin: 

Everything worked except the last export. It says the following...
-----------------------------------------------------------------------
bash: export: `linux-gnu=linux': not a valid identifier
-----------------------------------------------------------------------

 ](*,) 

I dont know how to fix it....

---

### Post by dreamcasting on 2005-03-04
[QUOTE=Jesus Franco]

Everything worked except the last export. It says the following...
-----------------------------------------------------------------------
bash: export: `linux-gnu=linux': not a valid identifier
-----------------------------------------------------------------------
I dont know how to fix it....[/QUOTE]

should be 

export OSTYPE="linux"

leave off the $ and the export will work.

---

### Post by Jesus Franco on 2005-03-04
[QUOTE=dreamcasting]should be 

export OSTYPE="linux"

leave off the $ and the export will work.[/QUOTE]

 #-o 

Thanks. It worked  :D

Its really neat. To bad it flickers like crazy...not to mention the 800 megs of ram it uses on full screen.  :cry: 

It is really cool though. A revolution indead. Longhorn what?  :lol:

---

### Post by telmo on 2005-03-05
YEP! But i've been searching their [forum](http://www.javadesktop.org/forums/forum.jspa?forumID=56) and i couldn't find a way to get it to work on Ubuntu... :S

Can anyone HELP!?

---

### Post by Jesus Franco on 2005-03-05
[LINK](http://www.ubuntuforums.org/showpost.php?p=83288&postcount=6) 

Full how to is already posted.  :D

---

### Post by telmo on 2005-03-05
Nop... no it's not.
That's only the demo.
I bet you still can't run lg3d-session. :)

---

### Post by Jesus Franco on 2005-03-05
Oh I see what you mean now...I dont think its possible. If it was I would like to learn how to do it.  8-) 

It is very cool.  8)

---

### Post by telmo on 2005-03-05
I sure would like to see this one in a repository.... :) but i don't believe i'll have the pleasure.

---

### Post by crun on 2005-03-06
I just noticed that lg3d-session is in the files distributed with the demo. To make it work you should stop the x-server, and 

```

$ cd /home/username/lg3d/bin
$ sudo ./lg3d-session

```

I worked for me, though too slow to really work with

---

### Post by telmo on 2005-03-06
How did you manage to stop the xserver, may i ask?

---

### Post by Jesus Franco on 2005-03-06
I feel I'm asking alot of questions...

But does that add it to the Sessions dialoge in the LogIn screen? Or does it just enable it for the time being? Thanks.

I dont know how to stop the X Server in Ubuntu either. All i find is ways to do so in other distros...I've tried it and it does not work in Ubuntu.  :(

---

### Post by crun on 2005-03-07
To stop the x server I did (may not be the most professional way of doing it though).

```

$ sudo killall gdm

```

As far as I know it doesn't get added in the sessions screen of gdm

---

### Post by telmo on 2005-03-07
hmmm... still can't get it to work.

---

### Post by jkarpago on 2005-03-19
Hi:
I install looking glass with the how to and it seems to work till the splash screen , where i see the splash image and then closes and nothing happen

I tried it with lg3d-session and just the same, splash screen and then black screen and nothing happen.

Has anybody this problem?

---

### Post by telmo on 2005-03-21
Yep! That's my big problem. I'll try it again sometime in Hoary then maybe i'll post a full howto. ;)

---

### Post by Slalomsk8er on 2005-03-31
I get a black screen too :(

After I fixed the csh and GNU/Linux things I was looking forward to a 3D desktop but found just a black screen.

---

### Post by JorisK on 2005-05-16
This is what i get when i run lg3d-dev:

root@wrkst-joris:/usr/lg3d/bin # ./lg3d-dev
/usr/lg3d/bin /usr/lg3d/bin
/usr/lg3d/bin
LG_SETTINGS -Dlg.etcdir=/usr/lg3d/bin/../etc/
rmiregistry: Command not found.
[1] 9352
[1]    Exit 1                 rmiregistry 44817

Anyone got a clue?

Edit: Fixed it... forgot to activate the export rules in my .bashrc.

Next question: How can i find out my LG3D is using Software rendering or 3D rendering? :)

---

### Post by telmo on 2005-05-16
> Next question: How can i find out my LG3D is using Software rendering or 3D rendering? 

hmmm... that's a nice question indeed! :D

---

### Post by moal on 2005-05-25
[QUOTE=JorisK]

Edit: Fixed it... forgot to activate the export rules in my .bashrc.
[/QUOTE]


how did jou do that ??? do u have to edit the bash.bashrc or dot.bashrc and what exactly do I have to edit??

thanx

---

### Post by tyze on 2005-06-03
[QUOTE=moal]how did jou do that ??? do u have to edit the bash.bashrc or dot.bashrc and what exactly do I have to edit??

thanx[/QUOTE]

--> He just has set the $JAVA_HOME and $PATH Variable right. that will fix it.

I've another question. The lg3d works fine in the window mode.Then I tried it in session mode: 

- First I stopped the x-server (/etc/init.d/gdm stop) 
- And then i ran de lg3d-session file in the lg3d folder.

Something happened (nvidia drivers will load) and then I see a white/gray screen and the mouseicon is a cross. And there it hangs. When i look into the Xorg.0.log i saw the following messages:

Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!


I think its beacause the font server is still running. Has anyone any idea how to shut down the font server. Or any other idea? 

Thanks tyze

---

### Post by rherman on 2005-08-04
Personally, I am amazed with the very similar-looking, opensource project Croquet. It is from a version of smalltalk called squeak [http://www.opencroquet.org/](http://www.opencroquet.org/)

rob

---

### Post by rherman on 2005-08-04
Sorry, double post.

---

