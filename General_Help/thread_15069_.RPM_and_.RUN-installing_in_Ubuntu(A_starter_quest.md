---
title: ".RPM and .RUN-installing in Ubuntu(A starter question)"
date: 2005-02-11
forum: General Help
---

### Post by Serial Number on 2005-02-11
I am very noob with Linux, as I started using it just a few days ago and I haven't had time to use it for these days either. However, now I have a problem as I want to install a few programs. 

The first program is a .RPM-file. On IRC, someone told me about installing it with Synaptic Package Manager(/usr/sbin/synaptic). However, this program only downloads the packs off the net and I don't see an option to scan my computer. As I tried to do "Open With..." with SPM to the file, it said I need root rights. I read the manual, but it only told how to get these rights in console. A friend of mine also told me the console command for RPM-files but the terminal seems not to like it, but rather tell me to use a "graphic program which comes with Debian"(Guess they forgot to change the message, eh?)
So, either
A. How do I install the file? With SPM, by some terminal command, or what?  ](*,) 
B. How do I get to root on the desktop? Do I need to activate it like in the manual and then login from the login that comes when I start Ubuntu or what?

The second program is a .run, and I guess it's exactly the same question for this.

Thanks already.

---

### Post by valadil on 2005-02-11
.rpm is an installer for Red Hat based linux distributions.  Making it install to a debian based distro (like ubuntu) is more trouble than it's worth.

The way synaptic works is you choose a package from synaptic, and it fetches and installs the package plus all the other apps and libraries needed to make that package run.  Ditch the .rpm and see if synaptic has the package you're looking for.  Don't include version numbers or .rpm.  Just the name will suffice.

To use synaptic with root privileges open a terminal and type the following line:
gksudo synaptic
It should ask for your password then open up synaptic running as root.

For the .bin file you will also need a terminal.
Type 'sudo su' to turn yourself into root.

Use the following command to add executable (x) access to the file for all (a) users.
chmod a+x file.bin
Where file.bin is the file in question.

Finally run the file with ./file.bin

---

### Post by Serial Number on 2005-02-11
Alright. I forgot to ask - What about .tar.gz-files? Someone told me that they're about raw packs which need to be compiled. So, how would I compile them?

---

### Post by Jad on 2005-02-11
Hi Serial number, first I would like to welcome you in your Ubuntu forum :-)  and welcome you as new linux users.

since you are a very noob in linux, then you will have to read, the power of linux desktop means you can manage mostly everything, but that doesn't mean everything has a GUI (Graphical user interface) to manage, so its user friendly Not IDIOT friendly.
so far you have installed linux, so you are a user not an idiot. I mean it in good not bad.
Now, before answering your question, I would tell you that since Ubuntu is new debian based distribution so if you couldn't find a How-to/FAQ/spotlight in ubuntuforums.org or UbuntuGuide.org then you will have search for How-to/FAQs/spotlights in debian, until now there is no difference in the architecture between Debian and Ubuntu (correct me guys if I'm wrong).

Now, about compiling software from source code.
please check this URL [http://www.aboutdebian.com/compile.htm](http://www.aboutdebian.com/compile.htm)
it has more than enough explanation and examples for your needs.

remember, offer it sometime to read and practice and it will offer you stability, reliability, and usability.
and yeah its Linux!

Welcome to Linux Community.
ah btw mostly you will not need what called antivirus, serial number under linux :-)

---

### Post by Serial Number on 2005-02-11
Yeah, I had anknowledged that GUIs, and with that that Linux is not really ran on them. Thank you both! :)

---

