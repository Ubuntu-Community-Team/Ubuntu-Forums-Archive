---
title: "Trickle Java Problem"
date: 2009-07-30
forum: General Help
---

### Post by ViPeRaY on 2009-07-30
Hey folks,

I am having a problem with trickle. I am trying limit azureus's download speed. Azureus works fine without any problem. However when i try to run it with trickle i am getting the error below. I do have the latest version of java by the way.

```

$$$$$$   trickle -d 500 azureus
trickle: Could not reach trickled, working independently: No such file or directory
Starting Azureus...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE [java = ERROR:]
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
ls: cannot access /usr/java: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com

``````

$$$$$$   java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)

```

---

### Post by a7ndrew on 2009-07-31
hmm maybe try running 'which java' and comparing that to your PATH environment variable ('echo $PATH') to ensure that your up to date java installation is being referred to in your path.  

/usr/java looks odd to me, I would expect your java installation to have put a symbolic link in /usr/local/bin .

I have no experience using trickle.

---

### Post by ViPeRaY on 2009-07-31
I also want to add that my system is 64 bit. I first installed 64 bit java however i could not get azureus work on 64 bit java. Then i install 32 bit java without uninstalling 64 bit java. I used the command below to switch from 64 bit java to 32 bit java.

sudo update-alternatives --config java

---

### Post by ViPeRaY on 2009-08-02
Ok. I tried something to solve the problem and I found something. I tried to remove and install only 32 bit and only 64 bit java. By the way I use Jaunty x64.

Here is the process. If i only run 32 bit Java then azureus works fine. Also when i install 32 bit java the libraries goes to /usr/lib/jvm/ia32-java-6-sun in stead of /usr/lib/jvm/java-6-sun.

I realized that trickle checks /usr/lib/jvm/ia32-java-6-sun for checking the java. That is why if i switch to 64 bit java, it is because the path is correct trickle works but then azureus does not.

If i switch to 32 bit, then the system uses the other path ( /usr/lib/jvm/ia32-java-6-sun ). In this case, azureus works but trickle does not because it checks the other path.

So here is my question, how can i change trickle settings to check  /usr/lib/jvm/ia32-java-6-sun in stead of /usr/lib/jvm/java-6-sun? Or how can i completely disable java checking process of trickle? I want it to just execute the application name which is given to it, not to check anything.

Also if i try;

trickle -d 500 java -d32 | azureus

then trickle can start the azureus without a problem, however trickle does not limit the download speed. I think it limits java in stead of azureus.

Any ideas?

---

