---
title: "Frostwire will not load"
date: 2006-03-24
forum: General Help
---

### Post by cabber on 2006-03-24
I click on the icon and it will not load.  Anyone having similar issues?  Not sure what is going on??](*,)

---

### Post by taurus on 2006-03-24
Try running it from a terminal to see what's the problem?

Applications -> System Tools -> Terminal then type
```

frostwire

```

---

### Post by cabber on 2006-03-24
```
matt@ubuntu:~$ frostwire
: command not found:
: No such file or directory
: command not found:
: command not found3:
'unFrost.sh: line 24: syntax error near unexpected token `
'unFrost.sh: line 24: `look_for_java()
matt@ubuntu:~$

```

This is what I got when I typed frostwire in the terminal

---

### Post by taurus on 2006-03-24
Hmm...  I assume you already have java installed!  I don't have any problem running it, Version 4.10, on my machine at all!
```

taurus:~/:% frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.4.2-02]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.

```

---

### Post by adam.tropics on 2006-03-24
Snap.....tried both Sun and then Blackdown Java (the Frostwire site suggested this, as they only test with Sun), but no good with either....Has anyone tried Limewire, is it having the same issues??

---

### Post by jrib on 2006-03-24
it's a silly mistake in the packaging.  Seems like someone saved the file in windows and then packaged.  Easy to fix, just do this:

```
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

dos2unix is provided by the sysutils package

---

### Post by cabber on 2006-03-24
```
steve@ubuntu:~$ sudo dos2unix /usr/lib/frostwire/runFrost.sh
sudo: dos2unix: command not found
steve@ubuntu:~$

```

This is what I got when I ran your suggestion.  Still will not load.

---

### Post by Jason_25 on 2006-03-24
[QUOTE=cabber]```
steve@ubuntu:~$ sudo dos2unix /usr/lib/frostwire/runFrost.sh
sudo: dos2unix: command not found
steve@ubuntu:~$

```

This is what I got when I ran your suggestion.  Still will not load.[/QUOTE]

So did you install sysutils?

---

### Post by cabber on 2006-03-24
No.  Not sure what this is?  Where would I find sysutils?  And what will it do?

---

### Post by Jason_25 on 2006-03-24
Please read post 6 in this thread.

---

### Post by trent dillman on 2006-03-24
sudo apt-get install sysutils

---

### Post by cabber on 2006-03-24
[QUOTE=_jason]it's a silly mistake in the packaging.  Seems like someone saved the file in windows and then packaged.  Easy to fix, just do this:

```
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

dos2unix is provided by the sysutils package[/QUOTE]


Read entire post again.  Not sure what or where the sysutils package is?  From that post it says:  DO THIS:

```
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

which I did.  Per my previous post, I get somewhat confused on the sysutils package.  Thanks.

---

### Post by adam.tropics on 2006-03-24
Ok, followed post6, all good, and Sun Java is installed,

> adam@dapper:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu6)


but frostwire gives me....

> 
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)


I'm missing something here......!!!!

---

### Post by cabber on 2006-03-24
Same here.  I installed this a week ago on another system, via Automatrix, and it worked flawlessly.

---

### Post by jrib on 2006-03-24
[QUOTE=adam.tropics]Ok, followed post6, all good, and Sun Java is installed,



but frostwire gives me....



I'm missing something here......!!!![/QUOTE]
```
sudo update-alternatives --config java
```
Is Sun Java chosen?

[QUOTE=cabber]I get somewhat confused on the sysutils package. [/QUOTE]
You can do what trent dillman said above or use synaptic to install sysutils.

---

### Post by adam.tropics on 2006-03-24
> There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/jvm/java-gcj/bin/java


I'm just confusing myself now!!

It doesn't seem to matter which option I go for, none will allow frostwire to load.  It's a bit wierd because up until yesterday, I had no problems at all with this, but had to do a fresh install, and now this.

---

### Post by jrib on 2006-03-24
[QUOTE=adam.tropics]I'm just confusing myself now!!

It doesn't seem to matter which option I go for, none will allow frostwire to load.  It's a bit wierd because up until yesterday, I had no problems at all with this, but had to do a fresh install, and now this.[/QUOTE]

How did you install Sun java?

I would recommend using [https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)

---

### Post by adam.tropics on 2006-03-24
Ok, got it..

Went back to Blackdown from repos, then 'sudo update-alternatives --config java', chose Blackdown, and it works again...

Thanks for the help people.Much appreciated.

---

### Post by tor528 on 2006-04-29
(deleted)

---

### Post by Wyrm_1972 on 2006-04-30
[QUOTE=_jason]it's a silly mistake in the packaging.  Seems like someone saved the file in windows and then packaged.  Easy to fix, just do this:

```
sudo dos2unix /usr/lib/frostwire/runFrost.sh
```

dos2unix is provided by the sysutils package[/QUOTE]

Thanks mate! After removing Frostwire and Blackdown and then reinstalling and still getting the same error, this fixed it!

---

### Post by caryb on 2006-08-20
I get this 

runFrost.sh: 44: Syntax error: "(" unexpected (expecting "}")

Am running edgy with Sun Java installed


TIA Cary

---

### Post by nixternal on 2006-08-22
carb, same thing here. no matter how you install frostwire, either via the .tar.gz or the .deb file you will get this.

---

### Post by llamakc on 2006-08-30
Could it be because /bin/sh now points to dash instead of bash? I dist-upgraded to edgy this morning and then tried to fire up FrostWire and received the same error.

You can write an alias or wrapper script for /usr/lib/frostwire/runfrost.sh that calls bash explicitly.

I just did:

cd /usr/lib/frostwire && bash runfrost.sh 

or something like that. Fired right up.

---

### Post by Tanath on 2006-09-21
For me, running 'bash runFrost.sh' starts it, but the window contents are blank. Output:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.

---

### Post by warbirdsdreamer on 2006-09-30
I realize this is a week old with no new posts, but I ran 'bash runFrost.sh' like the last poster did and everything works perfectly except I can't use my ipod with it.

---

