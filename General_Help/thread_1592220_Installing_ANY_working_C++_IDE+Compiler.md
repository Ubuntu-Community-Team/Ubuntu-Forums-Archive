---
title: "Installing ANY working C++ IDE+Compiler"
date: 2010-10-10
forum: General Help
---

### Post by nearlymagicman on 2010-10-10
Well, i guess my title is giving the topic away. I am a C++ Coder and thought it might be a clever idea to partially switch to a Linux distribution, so i did. But well i don't get any kind of C++ IDE or Compiler to work, i tried eclipse (for about 6 hours by now) and when i looked for CB (Code Blocks), well i was told i need the nightly build, but "Oh no", by the given link there are no for ubuntu or even linux.

So you are kind of my last hope.


Here a list of what i tried:
CB:
[http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu](http://wiki.codeblocks.org/index.php?title=Installing_Code::Blocks_nightly_build_on_Ubuntu) (not helpfull, i did what they told, but the link doesn't contain any nightly build for linux)

eclips:
[http://www.ibm.com/developerworks/opensource/library/os-eclipse-stlcdt/(well](http://www.ibm.com/developerworks/opensource/library/os-eclipse-stlcdt/(well) i am able to install the cdt plug-in but there aint ANY highlighting or code completion at all, it even tells me that the bibs i try to include for "Hello World" are non-existing)
[http://cplus.kompf.de/artikel/cdt.html](http://cplus.kompf.de/artikel/cdt.html)
(well here it seems the page is not even close of beeing up-to-date, the path "Help - Software Updates - Find and Install" doesn't exist in eclipse helios [it is german so don't bother to read it^^])
[http://ubuntuforums.org/showthread.php?t=420886](http://ubuntuforums.org/showthread.php?t=420886)
(well the path "sudo apt-get install eclipse-cdt" doesn't exist)
I also tried to dowload the cdt-version of eclipse, but oh well no highlighting or code completion, and i am not able to compile anything. 

So all in all i can say, i don't know what the problem is. I can just guess:
1. I am not able to install the cdt plug-in correctly. I doubt that version cause i CAN make a new C++ projekt, and it does include a bunch of librarys with C++ in it's filepath, even though i dont have any clou what they are for. But it doesn't highlight, there is no code-completion and it doesn't do anything i am used to by the java-eclipse IDE. And i cannot compile
2. I am not able to install the compiler (gcc) correctly, but well i did everything i was told to in those tutorials:
"sudo apt-get install build-essential"
"sudo apt-get install gcc"
-it tells me that it is already installed
"sudo apt-get install gbd 
-same story, already installed
So this guess is also unlikely 'cause i obvious did what i needed to and everything should be correctly installed.


I hope anybody can help me, i am working on this for the past six to seven hours and it is just starting to annoy me. I would love to start using linux-ubuntu but if it is always that complicated to get startet on something so basic, i just don't see a future here. So i hope it is just a basic understanding error on my part and not a typicall installing problem of ubuntu.

Tanks for your time and help.

---

### Post by hesed on 2010-10-10
Why don't you try NetBeans?
[http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)

You can choose between installing the C/C++ bundle (35MB), or the entire bundle (266MB).
Personnally, I prefer NetBeans to Eclipse... but that's another story.

---

### Post by Vaphell on 2010-10-10
is there any particular reason you skipped the standard installation method of software in ubuntu which is from standard repositories using synaptic? How on earth browsing dozen of websites for setup.exes (or equivalents of them) is easier than using 2 click install from a single location?

terminal equivalents of synaptic's 'mark package and apply changes' combo
sudo apt-get install codeblocks
or
sudo apt-get install anjuta
or
sudo apt-get install eclipse

i can't help with project configuration though, but pointing to headers of standard libraries is rather necessary.

---

### Post by nearlymagicman on 2010-10-10
Well it seems to run on windows as well, so i will give it a shot, just never heard of it.
I is kinda important for me that there are versions for both, linux AND widows, cause i might be forced to do smth in windows and i dont want to have thousands of different IDEs.

Well, never the less i would love to know what i did screw up!



> is there any particular reason you skipped the standard installation method of software in ubuntu which is from standard repositories using synaptic? 
-What do you wanna tell me with that sentence? I am new to ubuntu and i just googled for a tutorial, and those links are what i got.

> How on earth browsing dozen of websites for setup.exes (or equivalents of them) is easier than using 2 click install from a single location?
-Well there IS NO, 2 click install for c++ eclipse (there is not even a working C++ eclipse), i can use the Java version but that aint helping if you want to code in C++.

> terminal equivalents of synaptic's 'mark package and apply changes' combo
sudo apt-get install codeblocks
-i actually kinda dislike codeblocks so it was just my last resort to try it, and as i told u earlier, i am new and just looked for help in the internet!

> or
sudo apt-get install eclipse
(there is no c++ eclipse with a working compiler)

---

### Post by GregBrannon on 2010-10-10
I'm betting that most of your problems will be solved by the following command:

[sudo aptitude install build-essential]("sudo aptitude install build-essential")

Ubuntu doesn't come by default with everything you need to do development.  the command above should add what you need to get going in C++ programming.

There are many discussions about IDEs and setting up a development environment in the Programming Talk stickies and topics.  You might look there for more info.

I also ran across this article on IDEs the other day that you may find helpful:

[http://mashable.com/2010/10/06/ide-guide/]("http://mashable.com/2010/10/06/ide-guide/")

Your last comment, "there is no c++ eclipse with a working compiler," may be true for your system (hence the first command above), but it's not true in general.

---

### Post by nearlymagicman on 2010-10-10
Well now a question which is kinda related to the topic:
"How do i install the java6-jdk?"

-solved but thanks

---

### Post by Vaphell on 2010-10-10
in system > administration > software sources, do you have multiverse repository selected? (it's for non-opensource programs)

also
sudo apt-get install ubuntu-restricted-extras
will install a lot of goodies you want either way (tons of media codecs and other stuff)

and in all seriousness, go to Software Center of Synaptic and play with it a little. You need to understand the repo based software installation, it will save you a lot of pain and you will like it. I simply find it somewhat surprising you start to customize your development environment on a platform you know very little about.

---

### Post by nearlymagicman on 2010-10-10
> in system > administration > software sources
this path does not exist! Am i right that u mean the "system" in the taskbar above?

> , do you have multiverse repository selected? (it's for non-opensource programs)
I have no clue what your mean.

---

### Post by Vaphell on 2010-10-10
yes, i mean that system menu on top panel, goto administration subtree and find something like software sources or similar
on 1 of the tabs you have a bunch of checkboxes for different repositories
main (open source maintained by canonical), universe (community managed open source), multiverse ('troublesome' stuff: proprietary, with licenses and such).

Java may be in multiverse, so you need to enable it.

---

### Post by nearlymagicman on 2010-10-10
ok, thanks. I guess i solved the problem by installing netbeans, though.


Thanks to everybody :)

---

