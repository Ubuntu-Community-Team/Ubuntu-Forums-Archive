---
title: "Ubuntu software center problem."
date: 2011-06-14
forum: General Help
---

### Post by adamasd1 on 2011-06-14
Hi guys!

I am running Ubuntu 11.04 (this is the first time having ubuntu, so I am quit new to it), and I already ran into a problem. When I am trying to download from Ubuntu software center I get this error:
 "An unhandlable error occured. There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks." . 
There is a dropdown for details: 
"Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.".

I don't know how to fix this, so if you have any ideas on how to fix this problem please let me know. I hope I posted this thread in the right section, and please for give me for my silly question.;)
Thank you!

---

### Post by jerrrys on 2011-06-14
try this

open a terminal and enter

sudo apt-get update

sudo apt-get upgrade

---

### Post by adamasd1 on 2011-06-14
> **jerrrys said:**
> try this

open a terminal and enter

sudo apt-get update

sudo apt-get upgrade

Thanks for the help! 
When I do "sudo apt-get upgrade" I get this in the terminal: [http://www.microsoft.com/typography/fontpack/eula.htm](http://www.microsoft.com/typography/fontpack/eula.htm) I don't really understand what microsoft has to do with this but I cant click anywhere in the terminal, I can only exit it. Any ideas on why this might occur?

---

### Post by FormatSeize on 2011-06-14
> **adamasd1 said:**
> [http://www.microsoft.com/typography/fontpack/eula.htm](http://www.microsoft.com/typography/fontpack/eula.htm) I don't really understand what microsoft has to do with this but I cant click anywhere in the terminal, I can only exit it. Any ideas on why this might occur?
It was a bug in Ubuntu 10.10, but I am not aware of the bug still being present in your version.
[https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/678004](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/678004)
 
What is happening is that they are asking you if you agree to the license of using truetype fonts, which I think Microsoft has ownership of, and allows anyone to use it for free if they agree to that license agreement (or something like that). If you don't, then it won't install truetype fonts in your system.
 
The user agreements normally don't directly apply to most people, and no one is going to kick in your door because you are improperly using truetype fonts (I'm not even sure how one goes about doing that), so the choice is up to you if you want to agree or not.
 
As for not being able to click anywhere in the terminal, it's waiting on a keyboard input (I'm unsure what clicking on something would do). Push Control + C to escape things like that. Control + C is the escape sequence for most things in a terminal that you want to immediately terminate, that's why copy is mapped to Control + Shift + C.
 
Anyhow, once you do that, is your problem fixed?

---

### Post by jerrrys on 2011-06-14
try

sudo apt-get install ttf-mscorefonts-installer

---

### Post by Scunnered on 2011-06-14
I similarly had the microsoft EULA request.  By following jerry's instructions it worked OK.

---

