---
title: "Compiling from source: how to add the path to wx-config (wxGTK) to my PATH"
date: 2009-10-03
forum: General Help
---

### Post by faiyez on 2009-10-03
I are Linux nub.

I am trying to compile a program that requires wxwidgets (wxGTK) for my program to be able to ./configure and then compile (make) itself.

wxGTK is correctly installed on my system, but trying to compile my program doesn't work because when you attempt to do that, the compiler is not able to find wxwidgets.

This means that I first need to add the path to wx-config file to my PATH. I need someone to provide me with a step by step guide on how to do this correctly for this particular case.

What I'm trying to compile is here: home/user/Compile/myProgram

And wx-config is in its default directory: usr/local/bin

Now, I'm following the guide on the program's support site on how to compile it, but I don't understand the information it gave me for this particular troubleshooting issue.

> **Errors?** If it complains about not finding wxGTK, you need one additional step. See the instructions above about how to add the path to wx-config to your PATH. You need to do the same, except you need to add the lib directory to your LD_LIBRARY_PATH. In other words, if you installed wxGTK to /usr/local, then you need to add /usr/local/lib to your LD_LIBRARY_PATH.

The "instructions above" were the following:

> To add a directory to your path just requires one simple line - if you installed wxGTK in /usr/local (the default), the line is:

 csh/tcsh: setenv PATH "${PATH}:/usr/local/bin"
 bash/ksh: export PATH="${PATH}:/usr/local/bin"

(Substitute /home/username/install/bin if you installed wxGTK in /home/username/install) 

(I'm on bash) I'm hoping someone can shed me some light on this...

---

### Post by mc4man on 2009-10-03
> wxGTK is correctly installed on my system

While I'm not doubting that wxgtk (libwxgtk) is installed I wouldn't agree that it is properly because of this

> And wx-config is in its default directory: usr/local/bin

Normally wx-config (which is a link to /etc/alternatives/wx-config) would be in /usr/bin

So if it's in /usr/local/bin then either continue to follow the instructions your following or post how you installed "wxGTK"

Normally you'd install libwxgtk and libwxgtk-dev from synaptic ( **the -dev is what's needed for compiling**

Because there are multiple versions available and the fact that some sources need a specific version, wx-config (the version which you want currently used) is set from update-alternatives

Here's an example from hardy where all 6 versions are installed (installed from synaptic
The * is the system default, the + indicates current selection ( in this ex. the same

> doug@doug-laptop:~$ sudo update-alternatives --config wx-config
[sudo] password for doug: 

There are 6 alternatives which provide `wx-config'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/wx/config/base-unicode-release-2.6
          2    /usr/lib/wx/config/gtk2-unicode-release-2.6
          3    /usr/lib/wx/config/base-unicode-release-2.8
*+        4    /usr/lib/wx/config/gtk2-unicode-release-2.8
          5    /usr/bin/wxgtk-2.4-config
          6    /usr/bin/wxbase-2.4-config

Press enter to keep the default[*], or type selection number: 



So maybe clear up where wx-config is, is it a link or actual file, and if in /usr/local how did it get there

( not saying it's not usable from /usr/local, only that if in /usr things would be easier for you

---

### Post by faiyez on 2009-10-03
> **mc4man said:**
> 
Normally wx-config (which is a link to /etc/alternatives/wx-config) would be in /usr/bin

So if it's in /usr/local/bin then either continue to follow the instructions your following or post how you installed "wxGTK"

I installed it as follows:

> Enter the wxGTK-2.4.2 directory using the "cd" (change directory) command:

cd wxGTK-2.4.2

Compiling wxGTK is totally automatic and takes just two steps: "configure" and "make" - but there are some options you can give it. To be safe, here are the options that we recommend for best results with Audacity;

 ./configure --disable-gtk2 --disable-unicode

This assumes that you want to install wxGTK into the /usr/local directory on your system, which is a great place to put it if you are the system administrator and want wxGTK to be available for everyone using your computer.

Anyway, once you're done configuring (which can take a couple of minutes, depending on how fast your computer is) it's time to compile - this is done with a single command:

 make

If compiling wxGTK succeeded, you're almost done - all you need to do is copy wxGTK to some location where other programs (like Audacity) will be able to find it. If you're going to install it somewhere that anyone on the system could find and you're not currently logged in as the root user, run "sudo":

 sudo make install

You're almost done with wxGTK! Type:

 sudo ldconfig

(If you were logged in as root, you can log out now and do the rest as a normal user.)

You just need to make sure that it's installed properly. To do this, type "rehash" in case you're using csh or tcsh (it won't hurt if you're not), and then try to run wx-config:

 rehash
 wx-config --version


It said version 2.8 which is the one I need. Everything was going well for me up until this point, when the guide moved on to configuring and compiling Audacity. After that part of the guide comes the part from the second quote of my first post. And after that comes the first quote from my first post.

> **mc4man said:**
> 
Normally you'd install libwxgtk and libwxgtk-dev from synaptic ( **the -dev is what's needed for compiling**

Okay, the version of wxGTK that I needed was 2.8. It's the only one I've put in. I went to Synaptic to check both libwxgtk 2.8 and libwxgtk-dev 2.8, and I noticed that the latter was missing. So I installed it.

> **mc4man said:**
> 
So maybe clear up where wx-config is, is it a link or actual file, and if in /usr/local how did it get there

wx-config is a file located in usr/local/bin, along with 2 more things: wxrc and wxrc-2.8

wx-config is a 'link to shell script', wxrc is a 'link to executable', and wxrc-2.8 is an 'executable'

I'm hoping this extra information helps you guys to tell me what to do, because I'm still confused about the whole thing.

---

### Post by faiyez on 2009-10-04
I'm hoping I've made it clear enough...

---

### Post by mc4man on 2009-10-04
Try removing the wxgtk you built, maybe the source has an uninstall routine
If you still have the source folder cd to it ( like you did before) and run

```
sudo make uninstall
```

Other wise you can remove the files/folders that were installed in /usr/local as root ( use gksu nautilus and browse to usr/local... and delete them all

It certainly **appears **from what you've posted that you compiled wxgtk-2.4.2 which isn't what you wanted anyway, so this indicates the current version is the one from synaptic (2.8

> It said version 2.8 which is the one I need.

Now that you've installed the -dev for 2.8 maybe try your compile again, whatever it was you're trying to build.
> I am trying to compile a program that requires wxwidgets ( the update-alternatives,,,, is only used when you have different versions installled and want to change

---

