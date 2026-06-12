---
title: "Malformed line in /etc/apt/sources.list ?"
date: 2010-04-15
forum: General Help
---

### Post by Rocket J Squirrel on 2010-04-15
I'm trying to get the latest version of remastersys

At [http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html) the author says to add the following to /etc/apt/sources.list
```

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic
```Synaptic, on load, reports an error:[INDENT]E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
[/INDENT]```
sudo apt-get update
```generates the same error. 

Line 56 is 

```
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic
```Is this line malformed? I don't see how.

---

### Post by mcduck on 2010-04-15
In the link you posted the instructions actually say that the line should be this:

```
deb http://www.geekconnection.org/remastersys/repository  karmic/
```
(Note the slash in the end...)

---

