---
title: "Project: PlugComputer Automation &amp; Control Solution"
date: 2011-09-02
forum: General Help
---

### Post by CasualProgrammer47 on 2011-09-02
To all that are willing:

I am a casual programmer that has limited experience developing in a litany of languages.  However, my experience developing has always been based in Windows.  I have also done a lot of PLC (programmable logic controller) programming.  

In my opinion, the capabilities of computers have significantly outpaced those of PLCs.  PLCs often function on simplistic "logic" programming (look up ladder logic and function block logic).  Computers have graduated into the object oriented world--an extremely powerful way to accomplish complex tasks.  PLCs capable of utilizing this kind of tool are usually prohibitively expensive.  

The goal I've set for myself is to utilize a small Linux-based computer system as a brain that will link up to a device capable of controlling inputs and outputs in the real world.  I came to this goal after browsing tons of solutions for a cost-effective controls solution for the company I work with.  

I do not have a lot of experience using Linux--though I'm posting this right now from my newly configured Ubuntu Linux machine.  I have only begun to delve into this amazing operating system and it has poisoned me against Microsoft. I have configured two operating systems on this machine: Windows XP and Ubuntu Linux.  Anytime I'm forced to boot into Windows, I hate it.  Linux has spoiled me.  

I now own the following two devices: Dreamplug (globalscaletechnologies.com) and ADAM-6150EI (Advantech.com).  I'm currently trying to devise a way to create a java program (I'm using Eclipse IDE) and then run it on the Dreamplug.  Dreamplug supposedly comes with Ubuntu Linux installed, however, I don't know how to window into it aside from establishing a wireless connection to it (it's a wireless access point).  

I'm looking for any support and help from the community that I can get.  I'd like this to work and I'd like to share my findings with everyone else in the spirit of open-sourcery.  

So, here it is:

The Project
Mission: Develop a PLC with Linux and Java as its backbone.

Obstacles: 
[LIST]
[*]Learning to develop java for Linux.
[*]Finding a way to get the ADAM-6150EI to work with Linux (it seems to be a windows device now that I've obtained it and looked over its documentation).
[*]PLC functionality that's java-based rather than based on a higher level "programming environment" (think [wonderware]("http://global.wonderware.com/EN/Pages/WonderwareHMISCADA.aspx") or [c-more]("http://c-more.automationdirect.com/")).
[*]Identify the steps to creating a user interface.
[*]Implement a device solution for displaying the user interface.
[/LIST]

Technology Resources: Dreamplug with Debian or Ubuntu Linux. ADAM-6150EI. Ubuntu Linux Desktop computer.

Let me know your thoughts and advice.  My goal is to have this as quickly as is possible, so I'll be actively checking back here and updating progress assuming there is interest in the post.


Project Status:
09-02-2011: As of right now, I'm trying to find a way to get this Dreamplug onto the internet so I can download some packages like VNC to it.

---

### Post by pe7er on 2011-09-15
> **CasualProgrammer47 said:**
> Linux has spoiled me.
Well, that's the only disadvantage of Linux :D

> I now own the following two devices: Dreamplug (globalscaletechnologies.com) [..]
Dreamplug supposedly comes with Ubuntu Linux installed, however, I don't know how to window into it aside from establishing a wireless connection to it (it's a wireless access point).  

I use a wired connection (Ethernet) connected to my modem/router,
and configured the modem/router to route traffic to the IP of the Dreamplug.

To get it wireless to your modem/router, maybe you'd better visit [http://www.plugcomputer.org/plugforum/index.php](http://www.plugcomputer.org/plugforum/index.php) or
[http://plugcomputer.org/plugwiki/index.php?title=Main_Page](http://plugcomputer.org/plugwiki/index.php?title=Main_Page)

---

