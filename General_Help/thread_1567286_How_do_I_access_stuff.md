---
title: "How do I access stuff?"
date: 2010-09-03
forum: General Help
---

### Post by 3.14159265... on 2010-09-03
Hi,

I have coasted all my life on my brothers' computer knowledge. I am a math major and have now taken an interest in computers. I recently learned latex, and my brother just installed Ubuntu for me.

I have 2 questions.

First, how do I run latex (texlive) on ubuntu.

I opened the terminal and wrote "apt-cache search texlive", and a bunch of things came up. I still can't access it though :(

The second question is that in the process of learning to type "apt-cache search texlive", I downloaded something called "sphinxsearch", how do I remove that?

Thanks

---

### Post by hwttdz on 2010-09-03
Downloaded?  A good rule of thumb is that unless you are sure you know what you're doing only get things from the repositories.  There was some brew-ha-ha over there being a linux virus a while ago, which was really just a bunch of people installing a script from outside any trusted repository.  

So moving on.  Generally you can do "sudo apt-get purge packagename" where packagename might be sphinxsearch.  You can also open up synaptic and see if you have any packages with status local or obsolete and see if those contain this sphinxsearch and remove from there.

Finally you can install texlive from synaptic, it has a pretty search function and everything.  And in the future when you want something and you know the package name and don't want to deal with checking boxes and dialogue options
sudo apt-get install packagename
and if you're really lazy you can
sudo apt-get install -y packagename
which assumes you answer yes to all the "do you want to install" questions.

---

### Post by 3Miro on 2010-09-03
Go to the Ubuntu Software Center and install Texmaker, it is the best LaTeX editor I have seen. I don't remember if it will come with latex or not, but if doesn't install it automatically or you need extra latex packages, then go to Synaptic Package Manager and search for texlive. Install texlive (with no names after that) for the minimum. The rest is fonts, styles and other goodies, install them if you need them.

Simplest way is to go to terminal and type:

```
sudo apt-get install texlive
```

BTW: never download random apps from the Internet, stick to the repos. I make exception only for Skype and VirtualBox.

---

### Post by QIII on 2010-09-03
Welcome to Ubuntu!

Math major, CS minor.  This is sounding familiar.

Soon it will be graduate degrees in CS.

Don't do it man!  You'll grow a CAT5 cable from your navel and have an umbilical cord tied to your machine!  Get a degree in Journalism or History!

On a serious note...

I'd like to play off of hwttdz's post a bit with regard to untrusted repos.  For the time being, I'd work only with the standard Ubuntu repos if something you want is found there.  If you want something else from an untrusted repo or site, ask here first.  You're probably OK with the "big names" (Java, etc) if you can sort out their instructions.  But be careful.

Actual viruses are not an issue in general, but social engineering can lead you to install malware.

Happy Ubuntuing.

---

