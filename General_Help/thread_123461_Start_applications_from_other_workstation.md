---
title: "Start applications from other workstation"
date: 2006-01-30
forum: General Help
---

### Post by Chef666 on 2006-01-30
I have 2 pc's in my network: 1 Ubuntu (:rolleyes:) and 1 Windows workstation.

My question: can I start Windows application from my linux-pc with the commandline?? :confused:

---

### Post by drummer on 2006-01-30
Not sure about the command line... but you can access the windows pc through vnc or another remote desktop application and control the computer remotely.

---

### Post by ardchoille on 2006-01-30
Applications -> Internet -> Terminal Server Client

---

### Post by Chef666 on 2006-01-30
Thnx, but I don't use a GUI, so it must be from the command line

---

### Post by deathshadow on 2006-01-30
In theory you can set up windows as a telnet server to it's command line. The following should apply to 2k/XP/2K3

First, make sure the telnet service is set to Automatic, not disabled under services.msc. 

You can also set it from the command line via:
*sc config TlntSvr start= auto*

you might also want to set it to stream mode with 
*tlntadmn config mode=stream*

That's it... You should be able to telnet right in, just pick yourself a linux telnet client. 

Whats scary about that is that the telnet server on 2K/XP is ENABLED by default. (thankfully it's disabled by default on 2K3) It's one of the first things I disable alongside Messenger.

---

### Post by Chef666 on 2006-01-30
Thnx, good idea.

I also disable Telnet by default, but in this case I'll run some tests to see if it satisfies my needs....

---

