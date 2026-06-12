---
title: "Reinstalling Java in Natty Narwhal 11.04"
date: 2011-09-18
forum: General Help
---

### Post by Acharn on 2011-09-18
I'm pretty sure reinstalling Java JRE would solve my problem.

I recently had HDD problems and managed to install 10.10, then upgraded to 11.04. I've been very happy with everything so far. Today I was looking for games to install, and ran across a web page called "Top Things to do after installing Ubuntu 11.04 Natty Narwhal". One of the things was to install the Java 6 JRE. Now I've been running all the programs I need for a week or so, but I figured if the JRE was already installed I wouldn't hurt anything, so I pasted the command "sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts" into my terminal and let fly. After things finished downloading I got a weird message box covering my terminal window, which said it was configuring the package and a message giving the usual ULA and what looked like a text "<Ok>" at the bottom of the visible page. The text ran off the bottom of the window, and there wasn't a scroll bar, and clicking on the "<Ok>" didn't seem to do anything. After half an hour of so nothing seemed to have changed, and I didn't think configuring should take that long, and I closed the window. The process was still running, but I managed to kill it in another terminal window. Soon after that I tried to install a game from the Ubuntu Software Center, and got an error:

"An unhandlable [sic] error occured [sic]
There seems to be a programming error in aptdaemon, the
software that allows you to install/remove software and
to perform other package management related tasks.

Details:
SystemError: E:I wasn't able to locate file for the sun-java6-jre
package. This "

Since I had used the Software Center to install programs before this with no problem I conclude my attempt to install the Sun JRE messed up the previously installed OpenJDK JRE. I think I need to reinstall the OpenJDK JRE, but I'm kind of scared now. I don't want to have to go to the trouble of reinstalling Ubuntu.

In a thread that was closed two days ago, one of the responders recommended using the command "sudo aptitude reinstall java*". So I tried that and got the message "sudo: aptitude: command not found". What should I do now?

---

### Post by Zephilinox on 2011-09-18
I'm not sure re-installing java will fix it, but I'll tell you how anyway, FYI if you are ever asked to type "aptitude" in the terminal, replace it with "apt-get install", and in the terminal you navigate to the <OK> button by pressing the [TAB] key (should be above caps lock on a normal desktop qwerty keyboard) and then [enter].

first run this command:

```
dpkg --get-selections | grep java
```you should see several lines, such as in my case:

```

java-common                    install
sun-java6-bin                    install
sun-java6-jre                    install
sun-java6-plugin                install

```now use those names on the left (java-common, etc, if you have more options put them in the following terminal line) like this:

```
sudo apt-get purge java-common sun-java6-bin sun-java6-jre sun-java6-plugin && sudo apt-get autoremove && sudo apt-get autoremove -f
```then install java like before, if you want to.

you could also try removing the java repository from your sources and updating/upgrading, like so:

```
sudo gedit /etc/apt/sources.list
```find the line "deb [http://archive.canonical.com/](http://archive.canonical.com/) natty partner" (or if you followed the outdated wiki, it should be "...lucid partner") and remove it, then do the classic ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Acharn on 2011-09-19
OK, that all looks helpful. Before I decide what I want to do, I have two more questions. It appears both Sun and OpenJDK have released Java 7, apparently since the latest upgrade listing was released. Should I try installing Java 7 over the current Java 6? And, finally, I don't think there's any reason to think OpenJDK is going to be around longer than Sun, although I think Java is in some form or other. Since the developers chose OpenJDK should I stick with it? I didn't really choose to replace it with the sun version, I was just blindly following the instructions on that web page, and the other instructions turned out to be very good for my needs.

---

### Post by Acharn on 2011-09-19
I seem to have stumbled onto the solution. I tried running 'sudo apt-get upgrade' and it downloaded the sun-jave packages and started the installation. Thanks to Zephilinox's explanation of using the <Tab> key to move in the message window, I was able to agree to the license and complete the installation. Now the Software Center seems to be working again. Using <Tab> to move in a message window? I haven't seen that since DOS 5.22! Never would have thought of it.

---

