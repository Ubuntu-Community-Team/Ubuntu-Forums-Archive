---
title: "Ubuntu + Java Question"
date: 2010-08-08
forum: General Help
---

### Post by T3RR0RH4WK on 2010-08-08
Hey guys, I was wondering if I could get someone's help with something.

A friend and I like to play those Yahoo! Games online and she's on a Mac and I'm on Ubuntu Linux. I tried on both Firefox and Google Chrome to get them to work, but with no luck. Apparently, from what I've read, JRE needs to be installed. I have that OpenJDK 6 thing but that was cause I installed something. As for official Sun stuff, how would I go about installing the real thing?

I'm not too good with compiling, as I don't know how to yet, and I can't find a .deb of it anywhere. Is there a command line way to install it?

Any help is much appreciated.

---

### Post by flick on 2010-08-08
This looks like a winner of a solution :

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

---

### Post by T3RR0RH4WK on 2010-08-08
> **flick said:**
> This looks like a winner of a solution :

[http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-install-sun-java-runtime-environment-jre-in-ubuntu-10-04-lucid-lynx.html)

Thank you for the quick response. Problem though... When I try to follow those commands, from the get-go, the first one gives me this error: **Error: need a repository as argument.**

What's that about? See, this is just my luck. What's simple for others is always broken or complicated for me lol.

---

### Post by flick on 2010-08-08
sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”

is what returned your error message of : 

Error: need a repository as argument

?

---

### Post by T3RR0RH4WK on 2010-08-08
> **flick said:**
> sudo add-apt-repository “deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner”

is what returned your error message of : 

Error: need a repository as argument

?

Yep. I followed the directions on the site you referred me to to the t and they threw that error at me with the first Terminal command. But I think I figured it out.

In the Software Sources, I can manually check and enable the "partner" repository. I did so, and then followed the second command (the apt-get-jre ones) and it's finally installing. Thank you for the help though, I appreciate it. I'll mark the thread as solved if it works when I try out the Yahoo! Games site.

---

### Post by flick on 2010-08-08
Not sure why the add-apt-repository command is giving fits, but we'll just fix your problem :

On your top panel, click System then click Administration then click Software Sources.

It will ask for your password, give it.

Click on the Other Software tab. You should see some entries for Lucid Partner repositories. Check their boxes. Click the close button. You'll get a message telling you to reload. Click the reload button. Wait a minute and that window will go away on its own.

Then back in a terminal window :

sudo apt-get update

Followed by 

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by T3RR0RH4WK on 2010-08-08
> **flick said:**
> Not sure why the add-apt-repository command is giving fits, but we'll just fix your problem :

On your top panel, click System then click Administration then click Software Sources.

It will ask for your password, give it.

Click on the Other Software tab. You should see some entries for Lucid Partner repositories. Check their boxes. Click the close button. You'll get a message telling you to reload. Click the reload button. Wait a minute and that window will go away on its own.

Then back in a terminal window :

sudo apt-get update

Followed by 

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

Got it. It installed them already and I'm trying it out now. Firefox still doesn't seem to want to let any of the games work though and the pop-ups still show blank, grey windows instead of the things they're supposed to show.

---

### Post by todlangweilig on 2010-08-12
I had the exact same problem as the OP and I was able to get it to work after running one additional command. This thread saved me a lot of time trying to figure out how to install Sun java, thanks!! 

You probably have already, but just in case you haven't, install the 'icedtea6-plugin' package. You'll need the package to enable Java in Firefox.
```
sudo apt-get install icedtea6-plugin
```

Try running 
```
java -version
``` 

and see if it says something like this:
> java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8 ) (6b18-1.8-4ubuntu3)
OpenJDK Server VM (build 16.0-b13, mixed mode)

If so then you're running the wrong version of java. Installing the Sun Java-6 package as described earlier doesn't seem to make Sun java the default java. I found the info for the following commands here: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") So try running this command after you have followed the previous steps to install Sun java: 
```
sudo update-java-alternatives -l
```
You should see something like this. If only the openjdk line is present, then the sun java packages didn't get installed.
> 
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

So lastly, try this:
```
sudo update-java-alternatives -s java-6-sun
```
...gives a much of messages, but doesn't seem to keep Yahoo from working.
> 
update-alternatives: error: no alternatives for HtmlConverter.
update-alternatives: error: no alternatives for java-rmi.cgi.
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/apt
...SNIP...
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-6-sun/bin/xjc


```
java -version
```
If you get this, then Yahoo should work as expected. 
> 
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)



So putting it all together from the beginning, it should be:

**HOW TO INSTALL JAVA SO IT WORKS WITH Yahoo Games**
```

$ sudo apt-get install default-jdk icedtea6-plugin
Enable 'http://archive.canonical.com/ubuntu lucid partner' in Repositories
$ sudo apt-get update
$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
$ sudo update-java-alternatives -s java-6-sun

```

Sorry for the long winded post, hope that helps you!!

---

### Post by grollsta on 2010-08-14
This thread has been a tremendous help to me.
```
sudo apt-get install icedtea6-plugin
```


I've been hassling with installing Zumo drive on my Ubuntu laptop. The GUI installer kept moaning that Java wasn't installed correctly, something about "Java6-runtime" dependancy being not satisfied. I reinstalled JRE6, and then found this post.

I ran the icetea6 command above, next ran the GUI installer within Firefox and Presto! It all works.

Thanks Guys!!

---

