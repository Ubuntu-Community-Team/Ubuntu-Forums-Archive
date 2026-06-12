---
title: "need help installing .rpm the EASY way"
date: 2012-07-07
forum: General Help
---

### Post by motoclaw on 2012-07-07
hello. to start off i am new at linux.
[LEFT]my goal is to install [COLOR=Blue]oracle sun java[/COLOR], the one from javas website. no i do not want to install the free jdk penguin java from the software center because that doesnt run the files i would like to run. i was sent to go install ''sun java''
[/LEFT]
i went to the website and i downloaded a small file that was packaged as a ''tarball'' ([COLOR=Blue]tar.gz[/COLOR])
i also downloaded the [COLOR=Blue].rpm [/COLOR]file aswell, why not try both.
now i have both files and i can explore them as if they were zip files but i have no clue how to install them. 
 i went to google and i must have gone to atleast a dozen web pages[COLOR=Black] that all gave me   different paragraphs to copy and paste into my terminal.
 i tried every one i came across and they all said "command not found"
 yes i did change <version> to my version #

im just looking for an easy way for a new user to install the .rpm file _without_ using terminal commands
[/COLOR]

---

### Post by motoclaw on 2012-07-07
the file name is jre-7u5-linux-x64.rpm and this is the list of commands that didnt work:
rpm -i jre-7u5-linux-x64.rpm
man rpm
rpm -ivh jre-7u5-linux-x64.rpm

---

### Post by Cheesemill on 2012-07-07
Don't install it that way, it's too complicated. RPM files are meant for Red Hat or Fedora, not for Ubuntu so they won't work.

Instead just do the following:
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

I know it uses terminal commands but as far as I know there is no way of install Oracle Java *without* using the terminal.

---

### Post by sanderj on 2012-07-07
> **motoclaw said:**
> the file name is jre-7u5-linux-x64.rpm and this is the list of commands that didnt work:
rpm -i jre-7u5-linux-x64.rpm
man rpm
rpm -ivh jre-7u5-linux-x64.rpm

What happened when you executed these commands ...? Maybe just a matter of installing rpm itself, and running it with sudo?

---

### Post by motoclaw on 2012-07-07
phew thankyou, i was halfway through getting super confused over this thing called "alien" lol
it says im about to add this ppa to my system

currently at 
gpg:                     imported:   1   (RSA:  1)

---

### Post by motoclaw on 2012-07-07
ohhh dude my minecraft works now thanks a million ily <3

---

### Post by jocko on 2012-07-07
.rpm files are for Red Hat and related linux distros. They will not install natively in Ubuntu. It is possible to install some .rpm packages using a program called "alien", but chances are the program you install that way will either not work at all or just not work properly.

It's probably better that you install from the .tar.gz file.
The instructions on [this page]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux") should do it. You will need to run some terminal commands. There just isn't any easier way to describe it. A single terminal command can do what it takes a whole page to describe how to do with mouse clicks...

Edit: I'm typing too slowly, so someone beat me to it with a much better method...

---

### Post by jocko on 2012-07-07
> **Cheesemill said:**
> I know it uses terminal commands but as far as I know there is no way of install Oracle Java *without* using the terminal.
Actually you can easily add the ppa and install the package using synaptic, but it's just so much easier to just copy+paste a few commands into a terminal...

---

