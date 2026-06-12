---
title: "I need a simple logging program:"
date: 2009-11-20
forum: General Help
---

### Post by Kayone on 2009-11-20
Anyone know of a simple logging program for Linux. This is specifically going to be used for analyzing network data/traffic. Anyone have any suggestions on something that is quick and easy (or something spectacular and robust) :)

I need something that can sit on a server, multiple people can log into, queried, with some sort of tracking capability so I could search for an individual's accomplishments during a time frame.

Thanks guys and girlies for your input and advice. If there isn't something like this, do you think my best approach is MYSQL? I am pretty dumb but I am eager to learn.

---

### Post by Giblet5 on 2009-11-20
Linux has what you want. And more.

Packages to look at:
sysstat - provides iostat command and others useful for 'sar'
acct - Linux process accounting tools (you can bill users by the CPU-second)
blktrace - detailed reports about disk and ethernet I/O
iotop - Shows you the I/O hogs

---

### Post by Kayone on 2009-11-20
> **Giblet5 said:**
> Linux has what you want. And more.

Packages to look at:
sysstat - provides iostat command and others useful for 'sar'
acct - Linux process accounting tools (you can bill users by the CPU-second)
blktrace - detailed reports about disk and ethernet I/O
iotop - Shows you the I/O hogs

I appreciate your help. I am actually looking for a program that accepts human generated logs (notes). I want something that basically creates a user interface for a csv file, a search function, and allows manageability.

I could always go with the wiki approach but it almost seems like everything ends up getting cluttered and lost in the shuffle. I am basically looking for options so I can try to move away from that method.

I am trying to create something that would allow for people to monitor a small/large network and take notes on what they see. For instance, if an IDS triggers an alarm, I want them to say 1.1.1.1 talked to 2.2.2.2 over port 69. This pron.exe was transferred. The exe did bad things. 

I am not a programmer and I'm pretty newb. It would be a lot of effort to design my own tool to do exactly what I want. I am trying to see if there is something I can easily get the job done with. I mean, it would be great if I could create an output log of all the IP addresses (if I were able to create a field for IP addresses). It would also be great if I could sort my output (by field preferance) like an Open/Msoft Office spreadsheet.

I honestly don't need all of that flexibility. Something simple is fine too. I think I am going to apt-get me that Notecase Notes Manager and try it out. I guess the only way to see if I can use it is to try to use it.

Still, any suggestions would be awesome. It would be cool if something out there did what I am trying to do.

---

### Post by Giblet5 on 2009-11-20
Collaborative notes. That's very different.

A good place to browse would be Synaptic. Click the Search button and search on "collaboration". The results + a google search or two should get you something useful...

---

### Post by Kayone on 2009-11-25
I went with NoteCase. It isn't really what I wanted but it gets the job done. Who knows, the features may benefit me more than I originally needed.

---

### Post by Frogging101 on 2009-11-25
A good program is Wireshark. It is available via synaptic.

EDIT: It is just for traffic monitoring, and people can't log into it

---

### Post by Kayone on 2009-11-25
> **Frogging101 said:**
> A good program is Wireshark. It is available via synaptic.

EDIT: It is just for traffic monitoring, and people can't log into it

Thanks 101, I appreciate any and all advice. 

I am currently using Wireshark. I was actually trying to have people log their findings from PCAP dumps into a location that could easily be queried. I mean, advanced features like statistics would be fantastic but I was looking for the best tool for the job (being that the job's needs were entirely flexible). 

Every day, it just reminds me why I need to learn MYSQL and a programming language. Long story short, I need to get off my butt one of these days. Learning Ubuntu and mastering BASH is just the beginning. I need to push forward soon!

---

