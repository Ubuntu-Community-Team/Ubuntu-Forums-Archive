---
title: "Says file does not exsist, yet there it is..."
date: 2010-02-18
forum: General Help
---

### Post by kfoxx on 2010-02-18
Hello everyone.

Having this problem that is driving me mad. Just untarred splunk to use on my ubuntu machine. Installation seem simple enough, but when I go to the directory that has the installation executable (/opt/splunk/bin/splunk start) it says the executable doesnt exist, even though if I ls, it is right there! I can vi it, move it delete it...but no execute. Its not a permission issue, it simply says it doesn't exist (ive tried executing it with out the "start" command, and same thing). I may not be clear so here is an image that demonstrates what is going on:

[IMG]http://imgur.com/zD7o5.jpg[/IMG]

WTF is going on??? It seems almost everything in this directory has the same problem. Probably something stupid I overlooked, but any help would be appreciated. Thanks,

kfoxx

---

### Post by lisati on 2010-02-18
Try this to see if it makes a difference:
```
chmod +x splunk
```

---

### Post by kfoxx on 2010-02-18
lisati, thank you for the quick reply to my post...but unfortunately that does nothing because as you can see from the ls -la command, splunk is already an executable for all users...

---

### Post by jobix on 2010-02-18
I ran into this problem once with a different program (not splunk). The reason was that the executable had a bunch of ^M characters at the end of each line from being edited in Windows and then moved to Linux. I fixed it by running the "dos2unix" command on that file. I don't know what the splunk executable looks like. So, I can't say this will work for sure.

---

### Post by rnerwein on 2010-02-18
hi
the very first try you recordnised. there was a space between the call.
the second is the output is coming out of your script ( i thing it is a shell script ). the file "echo_output.txt" doesen't  exist.
the third. type "file splunk" to see whats kind of executable is.
post the output of file.
ciao

---

### Post by kfoxx on 2010-02-18
Ok figured out thanks to SwedeMike on IRC. Was using a 32-bit version on a 64-bit machine... :P

Stupid me...though seems like ubuntu could improve their error messages....

---

### Post by jobix on 2010-02-18
> **kfoxx said:**
> ..though seems like ubuntu could improve their error messages....

I think the problem is with splunk. It should've checked the architecture when you first tried to install it and complained.

---

