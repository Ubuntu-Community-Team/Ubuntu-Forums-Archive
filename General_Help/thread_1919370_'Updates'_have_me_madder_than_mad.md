---
title: "'Updates' have me madder than mad"
date: 2012-02-02
forum: General Help
---

### Post by LandisTwo on 2012-02-02
I am new or re-new to gnome and ubuntu.
been a Novell, Mandrake, SuSE, openSuSE (KDE) user since NetWare 286... : )

the 'update manager' has me ready to throw this system in the street.
the UM says I have 68 updates to install.
It KEEPS Stopping on "Requires installation of untrusted packages".... OK.. 
Install the packages, give me a choice to review, add, tell me what's calling for this (in this case: 'accountsservices evince evince-common.... blah, blah'..)
What's calling it. 
I figured it's 'query and manipulate user account information ' stuff so I UN-CHECK that stuff... 
Click 'install updates' ... IT puts the check back and gives me the same error... 
Why is there NO SU or option to run the updates as sudo or just allow the 'default' user to click OK, INSTALL anyways... What to do?

Thank you in advance and SORRY for my domineer... It's been a long 2 days, setting up Linux as Routers and DNS... good news, that went wonderfully!

Landis.
p.s., as to gnome, I thought it would be a good 'production workstation' for those who don't need to touch anything other than the browser, mail and 'office'... for me, I like to 'touch' Everything... I'm calm now.

---

### Post by MG&amp;TL on 2012-02-02
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Output of:

```
sudo apt-get update && sudo apt-get upgrade
```

Please.

---

### Post by Dennis N on 2012-02-02
I've seen the same problem. The way around it is to install the untrusted packages update manager would not process by using the terminal:

```
sudo apt-get upgrade
```

This time, you will get the option to install each untrusted package. Type y to go ahead with the install.

This did not happen in previous Update Manager versions. It should give you the option to continue, but doesn't. A bug, or by design, I don't know.

---

### Post by LandisTwo on 2012-02-02
MG&TL - thank you... Is there anything that can be done, administratively from a gnome desktop? Not being able to 'login as root' makes the GUI Useless for anything besides web browsing, listening to music and letter writing??
It seems Everything I've wanted, tried to do or have done, I've had to do in a console.. I don't mind, even like working on console, but the GUI is misleading and makes me think things can and should be able to be done from it... I couldn't even change the default gw in network settings... 'Save' would not engage leading me to believe it was something only 'root' which doesn't exist can do it, so why even have the applet there? The whole thing seems 'half ***'... 

Anyways, thanks, seems to be installing everything, it only notified me of the additional space it would be using... , um, ok...

&#1057;&#1087;&#1072;&#1089;&#1080;&#1073;&#1086;,
Landis.

---

### Post by LandisTwo on 2012-02-02
> **Dennis N said:**
> I've seen the same problem. The way around it is to install the untrusted package update manager would not process by using the terminal:

thank you Dennis N.

the console thing seems to be the best and in most cases, the only way to do it.
Landis.

---

### Post by LandisTwo on 2012-02-02
OK, thanks. 
I used the console get commands you shared with me and all seems installed.
I ran the system> update> check and there is nothing needed.. 

Thanks Again, 
Landis.

---

### Post by dFlyer on 2012-02-02
Usually the untrusted warning comes from a ppa that you didn't import the key for the site. If you can figure out what ppa it is that you can either import the key or just remove that ppa. Yet if you remove that ppa you will not get the update you may need for what ever program your running.

---

### Post by MG&amp;TL on 2012-02-03
About the root desktop-please read the link I gave in my first post-that gives a lot of details.

If you just want to run a single app as administrator, press Alt-F2, then type:

```
gksu <appname>
```

So if I wanted to run nautilus as root:

```
gksu nautilus
```

Or if wanted to run blender(!) as root:

```
gksu blender
```


Hope that helps.

---

### Post by Zill on 2012-02-03
> **LandisTwo said:**
> I am new or re-new to gnome and ubuntu.
been a Novell, Mandrake, SuSE, openSuSE (KDE) user since NetWare 286... : )...
I also started off with Mandrake many years ago, initially with KDE, before moving to Ubuntu and Gnome.  The urpmi (RPM) system was (is!) very good but is *different* to the apt-get (DEB) system used by Ubuntu.  Similarly, the use of sudo, rather than su, with Ubuntu is *different*.

However, if you accept that you will have to learn to work differently then you may come to appreciate that these Ubuntu systems actually work quite well and may even have advantages. ;-)

So, my advice is simply to read-up on "the Ubuntu way of doing things" on these forums and elsewhere and, if you still have any questions then post here and I am sure you will receive good help.

Although it is often simpler to give advice here with terminal commands, most things *can* be done with a GUI.  It just takes a lot longer to write out verbatim instructions for the different versions of GUIs than to write a few simple terminal commands.

When a terminal application requires "root" access, just prefix the command with sudo.  Similarly, to start a GUI application with "root" access simply prefix the command with gksudo.

The link given by MG&TL in post #2 above explains this more clearly.

---

