---
title: "Setting up java development tools"
date: 2006-05-20
forum: General Help
---

### Post by solstice on 2006-05-20
Hi everyone! I'm giving Ubuntu a go again. The reason I didn't keep it last time was because something was messed up with my java environment, the applet viewer would not accept keyboard or mouse clicks and prevented me for testing projects I was working on.

I figured I should ask the experts the best way to install what I need, and where.

When I installed this stuff before, I downloaded the .bin file from sun's site and installed it to a folder in my home directory, and just downloaded eclipse, extracted that and used it. 

My questions are, should I be installing java in my home directory? Is there  a better place to put it? I am the only one that uses this machine, and certainly the only one using it that will be developing.

Should I get java / eclipse from repos? if so what are they called? or should I just get these from the respective sites?

I appreciate all of your help! The professionalism of the members of these forums are by far the best I have seen anywhere. Thanks again! (and sorry if this has been discussed before, a few minutes of searching didn't turn up much)

---

### Post by kaamos on 2006-05-20
Hello!

I'm not sure if this helps with your problems with applets, but here is a quick way to install the sun java 1.5 sdk. Open a terminal and:
```

sudo su
cp /etc/apt/sources.list /etc/apt/sources.list.bak
echo "deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free" >> /etc/apt/sources.list
apt-get update
apt-get install sun-j2sdk1.5
exit

```
Eclipse is available with synaptic (System->Administration->Synaptic package manager). Just search for eclipse.

---

### Post by solstice on 2006-05-20
Thanks for the reply kaamos.

I have done what you have said. Where will that install java? Will I need to set up paths to that location? typing java -version returns java 1.4.2, which I assume is from a JVM installed by default.

Also, I have installed eclipse from synaptic. When trying to run an application I have been working on I get the following error:

[COLOR="Red"]** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...[/COLOR]


Just curious if anyone knows if I am missing something or what this means, I haven't seen it before. Thank you for the help.

EDIT: I see something like this was reported as a bug but the current status claims "resolved". [http://bugzilla.ubuntu.com/show_bug.cgi?id=13942](http://bugzilla.ubuntu.com/show_bug.cgi?id=13942)

---

### Post by adamkane on 2006-05-20
Best way to install:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by kaamos on 2006-05-20
[QUOTE=solstice]Thanks for the reply kaamos.

I have done what you have said. Where will that install java? Will I need to set up paths to that location? typing java -version returns java 1.4.2, which I assume is from a JVM installed by default.[/QUOTE]

Whoops, forgot "sudo update-alternatives --config java"

---

### Post by solstice on 2006-05-20
thanks for the responses guys...any ideas on that error message I received?

---

### Post by kaamos on 2006-05-20
That should disappear with the sun version of java. At least I have ever seen it only with gnu java.

---

### Post by solstice on 2006-05-20
yes! thank you again. I removed the old version with apt-get remove and installed sun's java to my home directory. I then manually added a new runtime to eclipse and now that application I was working on executes fine.

Haven't tried any of my applets yet, but that is for a different day.

---

