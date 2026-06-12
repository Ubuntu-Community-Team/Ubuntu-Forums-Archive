---
title: "How do I get newer software on older base OS?"
date: 2012-01-11
forum: General Help
---

### Post by 3rods on 2012-01-11
I apologize if this has been posted already, but I wasn't even sure how to phrase the issue. 

I have a server running Hardy and I need to install scala version 2.7 or greater. However, the one in the repos for Hardy is version 2.2 or 2.3. I'd like to avoid building scala from source and was wondering what the protocol would be to install the new version on my older OS. 

What's the 'Ubuntu' or 'Debian' way to handle this?  

Do I just download the deb from somewhere? Is this going to put me in to dependency hell?

---

### Post by snowpine on 2012-01-11
> **3rods said:**
> I'd like to avoid building scala from source...

Why? Linux is "open source," this is its power and freedom. :)

Don't be scared, it is a basic Linux 101 skill, and very well documented: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

(or you can go on the Scala web page and see what they recommend: [http://www.scala-lang.org/](http://www.scala-lang.org/) ;))

---

### Post by 3rods on 2012-01-11
It's looking like I'm going to have to compile it to get etherpad going. 

I tend to avoid compiling things since I will be responsible for having to update them (and rebuild newer versions) anytime there is a security update and there is a greater risk of breaking things due to untested configurations.

I guess the retro packages are called backports in ubuntu. It seems there is no backport for Scala in Hardy.

---

### Post by mick222 on 2012-01-11
You could try here there's a deb package if you don't want to compile [http://code.google.com/p/ant-deb-task/downloads/list](http://code.google.com/p/ant-deb-task/downloads/list)

---

### Post by 3rods on 2012-01-11
That's what I was looking for. Is there a place where I can go to look for deb files (I mean other than just searching google)? Somewhere more *official*?

---

### Post by snowpine on 2012-01-11
If you are feeling worried about falling behind on security updates, or untested configurations due to mixing old and new packages, then it may be time to move up to 10.04 (which will give you Scala 2.7 as well as newer kernel and everything else).

---

### Post by marin123 on 2012-01-11
I don't know what Scala is or what it does, but you can add unofficial repository and get normal updates.

Here's a link which I found by googling "scala ppa".

[https://launchpad.net/~bneijt/+archive/ppa/+build/1880200]("https://launchpad.net/%7Ebneijt/+archive/ppa/+build/1880200")

EDIT: by "unofficial" I meant that it isn't maintained by Canonical.

---

### Post by snowpine on 2012-01-11
> **3rods said:**
> Somewhere more *official*?

No place is more *official* than the Scala website; what do they recommend on their download page?

[http://www.scala-lang.org/downloads](http://www.scala-lang.org/downloads)

---

### Post by 3rods on 2012-01-11
I meant an official site to find pre-built deb packages. The scala site only provides the sources to be built. 

I got things going with the resources in this thread. Thanks

---

### Post by lykwydchykyn on 2012-01-11
My order of methods goes like this:

 - Check the official repos
 - If not there, check official backports
 - If not there, check for a PPA
 - If not there, add a src repository for the latest Ubuntu version, and use apt-src to backport it myself
 - If not there, download upstream sources and use checkinstall.

Since you've done everything up to the apt-src step, I'd suggest that next.  Install apt-src, then add a source (NOT binary) repository for whatever release has the version you need.

create a ~/src directory, cd to it, and run:
```

apt-src install scala
apt-src build -i scala

```

You'll be prompted for sudo password as necessary.


EDIT: didn't see that you'd got it going already.  Still, check out apt-src for situations like this in the future.

---

