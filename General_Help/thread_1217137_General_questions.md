---
title: "General questions"
date: 2009-07-19
forum: General Help
---

### Post by greenspeed on 2009-07-19
I didn't really see a sticky about some general n00b questions and was wondering if there is one?

I know some of the basic commands, but not too much. I can run updates and installs, but that is about it.  I was wondering how to get to my registry of downloadable programs (i read it in a thread)

plus is there program that will interface with your Ipod?  I can't get a single driver to install and I have a tantrix cable along with my Ipod I'd like to interface.  I tried to read through the tantrix cable install on the open source tuning website, but it was impossible for me to understand.

thanks mates

---

### Post by celticbhoy on 2009-07-19
Under the applications menu select add/remove and you download away.
if you search for hipo you can use your ipod from there.

---

### Post by celticbhoy on 2009-07-19
Beginers guide 

[http://ubuntuforums.org/showthread.php?t=95139](http://ubuntuforums.org/showthread.php?t=95139)

---

### Post by TuckLive on 2009-07-19
> **greenspeed said:**
> I was wondering how to get to my registry of downloadable programs (i read it in a thread)

By saying downladable do you mean the package manager?  If that's what your looking for it's   System > Administration > Synaptic Package Manager

---

### Post by hetx on 2009-07-19
Most music players have some kind of iPod support, Rythmbox, Banshee, Exaile. I also remember using something called gtkpod, pretty simple but useful (was a while ago though)

---

### Post by greenspeed on 2009-07-19
this is the thread for the tactrix cable i was refering to

[http://forums.openecu.org/viewtopic.php?f=2&t=2422&hilit=linux](http://forums.openecu.org/viewtopic.php?f=2&t=2422&hilit=linux)

---

### Post by greenspeed on 2009-07-19
> **TuckLive said:**
> By saying downladable do you mean the package manager?  If that's what your looking for it's   System > Administration > Synaptic Package Manager


downloadable i was refering to this term "universe repositories" figured that would be my directory?

---

### Post by greenspeed on 2009-07-19
well i got bittorrent downloaded then read to run this command to get it to install actually.

btdownloadgui.bittorrent


but i am having a weird error pop up saying I've reached my dl limit?

arguments are -
--max_uploads <arg>
          the maximum number of uploads to allow at once. (defaults to 7)

--keepalive_interval <arg>
          number of seconds to pause between sending keepalives (defaults to 120.0)

--download_slice_size <arg>
          How many bytes to query for per request. (defaults to 16384)

--request_backlog <arg>
          how many requests to keep in a single pipe at once. (defaults to 5)

--max_message_length <arg>
          maximum length prefix encoding you'll accept over the wire - larger values get the
          connection dropped. (defaults to 8388608)

--ip <arg>
          ip to report you have to the tracker. (defaults to '')

--minport <arg>
          minimum port to listen on, counts up if unavailable (defaults to 6881)

--maxport <arg>
          maximum port to listen on (defaults to 6999)

---

### Post by CatKiller on 2009-07-19
> **greenspeed said:**
> i was refering to this term "universe repositories" figured that would be my directory?

No.

System &#8594; Administration &#8594; Software Sources.

The repositories are the places that the software packages are stored so that they can be downloaded and installed by package managers like Synaptic or apt-get. The names of the repositories vary by distribution, but the default Ubuntu repositories are split into main, restricted, universe and multiverse, where each of these refer to groups of packages separated by support or licence.

---

### Post by greenspeed on 2009-07-19
alright since everything is basically solved...anyone know about how to install the tactrix's driver?

---

