---
title: "Launch programs in cmd in Windows and get output"
date: 2009-08-12
forum: General Help
---

### Post by MockY on 2009-08-12
I have no idea where this thread belongs, but here it goes....

I am spoiled after many years of using Linux and if a software acts up, I can simply launch it via the terminal and later see output which hints to why a software crashed. 
I have a system belonging to a coworker (running Windows XP) and he has issues with both Internet Explorer and Firefox where both these browsers crash constantly. I would like to be able to launch it via command prompt to get any hints to why they crash, because the Event Viewer does not list anything. Is this possible in any way or am I doomed in terms of easy troubleshooting?

---

### Post by y-lee on 2009-08-12
> **MockY said:**
> I have a system belonging to a coworker (running Windows XP) and he has issues with both Internet Explorer and Firefox where both these browsers crash constantly. I would like to be able to launch it via command prompt to get any hints to why they crash, because the Event Viewer does not list anything. Is this possible in any way or am I doomed in terms of easy troubleshooting?

yes you can launch programs via the windows command prompt. You can also redirect the output to a text file:

    **command >* filename.txt***

Note: You may have to cd to the location of the program you are trying to run or be sure this path is in windows path or simply include the path with the command.

However I am not sure this will be of much help debugging the problem in windows. not sure what is going on but i would recommend running a virus scan and a spyware scan using some good, well known and respected tools.  As well as  trying to do all windows updates. this will at least rule out the obvious usual cause of problems like that in windows. If this fails try [ HijackThis]("http://en.wikipedia.org/wiki/Hijack_This") if you are  advanced enough to use it.

If it is not a spyware or malware issue and you are not familiar with debugging windows errors, I would suggest posting on a windows forum like Geeks to Go or something like that. 

good luck :)

---

### Post by MockY on 2009-08-12
Launching it via cmd only launched the software and then gives me a clean prompt. So redirecting it to a file would probably result in an empty file. Will try that though. Furthermore, this is a clean install of Windows so it's completely free of malicious software, which leads me to suspect hardware issues. I tested the memory with the Ubuntu disc with no errors as a result. Ohh well, I'll continue my quest.

Thanks

---

### Post by y-lee on 2009-08-12
Hmm does sound like hardware, may also be a network problem. Do other net using programs work, other browsers like opera or chrome, or Im clients? Well whatever good luck.

---

