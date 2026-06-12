---
title: "java error?"
date: 2012-04-24
forum: General Help
---

### Post by cindylo on 2012-04-24
I get this error for a lot of java related stuff like can you run it or Intel drive scanner. java.lang.UnsatisfiedLinkError: SRLProxy.start()J.

---

### Post by techsupport on 2012-04-24
> **cindylo said:**
> I get this error for a lot of java related stuff like can you run it or Intel drive scanner. java.lang.UnsatisfiedLinkError: SRLProxy.start()J.

Hi Cindy. How did you originally install it?  You can reinstall it from a guide like this and see if that makes any difference:

[http://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](http://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

---

### Post by cindylo on 2012-04-24
I installed it using Yumi created USB(Ubuntu 11.04).

---

### Post by techsupport on 2012-04-24
> **cindylo said:**
> I installed it using Yumi created USB(Ubuntu 11.04).

I would try installing it from the link I posted.  Uninstall whatever you did, and try using the instructions in that link instead. That worked for me when I did it.

:guitar:

cheer! :)

---

### Post by ph4nt0m117 on 2012-04-24
Yumi is normally for server applications if I remember correctly.

sudo apt-get update java  should fix it.  If not, then

sudo apt-get uninstall JDK10  or whatever you installed for java and then reinstalling it should fix any issues.

---

### Post by cindylo on 2012-04-24
Well it works but now I just sits there and does nothing. Like if I use can you run it never changed from "Gathering Information"

---

### Post by imachavel on 2012-04-24
I'm very confused about what you are trying to do, are you trying to develop in Java? this isn't exactly the code language forum. I figured you had an adobe flash problem but that link is to a development and install page, I want the java virtual machine library installed as well, so let me try from the link:

triggers being processed.... etc. etc. etc.

it worked most of the way for me up until THIS point:

--2012-04-24 14:18:08--  [http://oab-java6.sh/](http://oab-java6.sh/)
Resolving oab-java6.sh... failed: Name or service not known.
wget: unable to resolve host address `oab-java6.sh'
FINISHED --2012-04-24 14:18:08--
Downloaded: 1 files, 16K in 0s (49.1 MB/s)
danel@danel-Dimension-4700:~$ sudo ./oab-java6.sh
sudo: ./oab-java6.sh: command not found
danel@danel-Dimension-4700:~$ ./oab-java6.sh
bash: ./oab-java6.sh: No such file or directory
danel@danel-Dimension-4700:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jre' has no installation candidate
danel@danel-Dimension-4700:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package sun-java6-plugin

Maybe I'll try the download link then re use the command that failed in this link:

[http://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/](http://debianhelp.wordpress.com/2011/11/13/how-to-install-sun-java-se-1-7/)

---

### Post by cindylo on 2012-04-24
trying to run things like this [http://www.systemrequirementslab.com/cyri/intro.aspx](http://www.systemrequirementslab.com/cyri/intro.aspx)

---

### Post by imachavel on 2012-04-24
dude this:

[http://www.systemrequirementslab.com/cyri/intro.aspx](http://www.systemrequirementslab.com/cyri/intro.aspx)

helps you figure out if your pc has high enough directx or open gl or the right gpu and driver to run a video game. Hardly anything to do with a java plug in or language writing environment. It's like:

"If I just bought a brand new HP, then can it run modern warfare 3 for highest possible graphic compatibility? does my pc running windows 7 have right drivers, video library direct x format able to run the game, good nvidia gpu with over a gig of video ram, hard core intel processor and mobo socket? Help me out, thanks"

See the difference?

---

### Post by cindylo on 2012-04-24
Well aware of what it does but trying to get it to work as well as the Intel driver scanner(same company who does the plugin for canyourunit).

---

### Post by imachavel on 2012-04-24
I'd recommend downloading the driver manually(I've got family at intel and I've told them 8 billion times that driver scanner is garbage), first open a terminal:

ctrl+alt+t

as we all are well aware. Now let's try:

lspci

to see if the intel driver exists in the first place. I am very very confused by OP btw. Intel driver scanner and java not working sounds like OP is confusing gpu and java run time being associated together with a driver, the two never meet. If OP has good screen resolution then driver is probably installed.

On the other hand now we are discussing java sdk virtual language writing environments, troubleshooting java version, etc. I'm confused as to whether OP is having youtube trouble or is actually trying to write a java library and compile a .class file. 

Video game can you run it web site may be helpful in some scenarios, but I get the feeling that web site won't work for a computer with ubuntu formatted and installed as the operating system. Let's be realistic, your model of computer unless you build it from the main board and psu up is going to be made by a company like dell or lenovo or what not, and if it's not made by mac will have windows OS installed. So the web site to match your computer with whether the OS has compatibility with a game won't help much. As for java version, is it a plug for a youtube run time problem? Or is this question a valid sdk library install problem?

If so updating java and uninstalling and reinstalling the sdk packages might help, but this thread is confusing me. I'll be back on tomorrow, if I survive shooting myself.

---

### Post by techsupport on 2012-04-24
> **cindylo said:**
> trying to run things like this [http://www.systemrequirementslab.com/cyri/intro.aspx](http://www.systemrequirementslab.com/cyri/intro.aspx)

With something like that you would want to completely uninstall any openjdk java packages you have on your computer.  And I would install Java 6 manually. Including the plugin for mozilla.

---

