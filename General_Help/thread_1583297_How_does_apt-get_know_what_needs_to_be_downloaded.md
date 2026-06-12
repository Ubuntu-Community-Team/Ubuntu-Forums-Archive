---
title: "How does apt-get know what needs to be downloaded?"
date: 2010-09-27
forum: General Help
---

### Post by sim085 on 2010-09-27
Hello, when we use the apt-get command (ex: sudo apt-get install apache2) ubuntu will first check what additional packages will need to be installed. The user is then asked if he/she wants to download the wanted software packages or not. My question is, does apt-get connect to the internet to know what extra software packages need to be downloaded? If not then from where does it get this information?

---

### Post by cj.surrusco on 2010-09-27
> **sim085 said:**
> Hello, when we use the apt-get command (ex: sudo apt-get install apache2) ubuntu will first check what additional packages will need to be installed. The user is then asked if he/she wants to download the wanted software packages or not. My question is, does apt-get connect to the internet to know what extra software packages need to be downloaded? If not then from where does it get this information?

I'm pretty sure that the dependency information is included with the package when apt-get downloads it. So to answer your question, yes you would need to access the internet to find out dependencies, unless the package is already downloaded.

---

### Post by solitaire on 2010-09-27
basically you machine stores a database of all program files installed

When you ask for something to be installed; "apt-get" first checks the local list to see if it's already installed. If not then goes out to the web to bring down a up-to-date list of files available from the repositories.

Each program has a list of what files it requires to work properly (called Prerequisites or Required) and what programs rely on it (called Dependences)

Apt-Get then checks through the local list to see if everything is there. If not it selects the prerequisites required and adds them to your install request.

it's a bit more complicated, but that's the "Dummies guide" ^_^

---

### Post by sim085 on 2010-09-27
If so then howcome my installation (installes as guestOS on VBox) is working fine up till displaying the message if I want to install or not, but then fails to download any of the required packages? 

At the moment when I do sudo apt-get install apache2 the system is checking the dependencies (which I understand as having retrieved this information from the net). Then it tells me the space the installation is going to take. Here, after I say yes, apt-get fails to download any of the packages!! How is it possible that at first apt-get manages to connect and then it does not!?

---

### Post by Dex73 on 2010-09-27
Possible bad connection? Also, if it's something that has recently been moved apt-get may think it knows the location of the dependency but is unable to grab it. 

The above are guesses. Is there anyone else out there having this problem with this specific application?

---

### Post by rhoparkour on 2010-09-27
It seems to me that apt-get checks the repositories for the solicited package.

Once found, it will download it, and any packages needed to run or maybe compile it.

But yeah, the point is that there are databases in the repositories of packages and their dependencies (the packages they need).

Try looking at this to see what I mean with your favorite editor in read-only mode:

/etc/apt/sources.list

---

### Post by WorMzy on 2010-09-27
Have a look here: [http://packages.ubuntu.com/search?keywords=bash](http://packages.ubuntu.com/search?keywords=bash)

This is basically a human-friendly view of what apt sees. Apt's config tells it what version of Ubuntu it should be looking for (e.g. [Lucid]("http://packages.ubuntu.com/lucid/bash")) and what architecture it's running (e.g. [i386]("http://packages.ubuntu.com/lucid/i386/bash/download")). It'll read the list of dependencies from the database, so that it knows that if you want to install bash, you'll need to install (or have installed) dash, libc6 (>= 2.11), libncurses5 (>= 5.6+20071006-3), base-files (>= 2.1.12), and debianutils (>= 2.15), so it'll ask dpkg whether those packages are installed, and if they aren't, it'll let you know that they'll need to be downloaded and installed too.

---

