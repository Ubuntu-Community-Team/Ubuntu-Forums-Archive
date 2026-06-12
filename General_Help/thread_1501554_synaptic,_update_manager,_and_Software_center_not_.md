---
title: "synaptic, update manager, and Software center not working"
date: 2010-06-04
forum: General Help
---

### Post by aaron_the_dude on 2010-06-04
Ok, this happened to me before, where when I try to open Software Center, Synaptic package manager, or update manager, it would freeze with the window open and I would have to force it to shut down.  I decided to re-install the OS after this happened and I just updated ubuntu and it is happening again.  Anyway to get around this or fix it?

---

### Post by aaron_the_dude on 2010-06-05
bump

---

### Post by nutsy.ben on 2010-06-09
I have a similar problem with the recent update of lucid.

When I open the GUI of the update manager or Synaptic, they freeze when I try to install something.

1) Synaptic freezes from the beginning
2) Update manager freezes when I try to install something
3) Update manager and installation correctly work from the command line. (If I did not open update or synaptic before,if I did, I need to remove the lock).

It seems that the apti registry blocks everything.
Is someone know how to fix that ???

THK U

---

### Post by Dangger on 2010-06-20
Came here with the same problem... bump

---

### Post by riesengreen on 2010-06-20
Pretty sure that I have the same problem! Please see my previous post...

> **riesengreen said:**
> Hello all and thank you, as always, for the help.

So, when I try to download and install updates, this is what happens (please see picture). The window stays this way (blank) forever. The updates are not downloaded or installed. 

[IMG]http://farm5.static.flickr.com/4011/4703637308_75f96c34dc_b.jpg[/IMG]

Any ideas? I am hoping that someone has seen this before and has a quick fix.

Following this, when I&#12288;shut down the computer, the following tells me that Ubuntu is still trying to update...

[IMG]http://farm5.static.flickr.com/4016/4703394755_8004f3dbfc.jpg[/IMG]

THANK YOU ALL!

---

### Post by Dangger on 2010-06-22
I haven't been able to replicate the issue after disabling assistive technologies. Does anyone else here has AT enabled?

---

### Post by riesengreen on 2010-07-02
> **Dangger said:**
> I haven't been able to replicate the issue after disabling assistive technologies. Does anyone else here has AT enabled?
Dangger:

I disabled assistive technologies, and was able to update! Many thanks for the advice.

I wonder if this is a known bug...

---

### Post by dhondiba on 2010-08-07
Disabling assistive technologies did the trick for me too. Thanks to this advice I still have a few strands of unpulled hair on my head.

---

### Post by CROLMAC on 2010-08-07
I have another problem, but as it concerns synaptic(never could get it to do anything anyways) and the software center, I thought I'd try.
 1. the software center tries to load, and then ..nothing. It just doesn't work, no message.
 2. Then I tried to update it or fix it with synaptic. there was an exclamation mark next to it in synaptic, I choose it to update, it says one file is needed, and I press apply(more or less in that order), it starts doing it, and then it says that it found a 404 and can't do it.
  3. I guess I did something stupid while trying to download then remove banshee (yes I created earlier a thread on not being able to rip my cds to mp3, after trying other stuff, I finally crumbled and called for help) and amarok, both of which did not work btw but I'm digressing.
  Thanks people for the patience you show this anti-geek and take care.
 ps I've been trying to download other stuff and it always fails to find the files...should I reinstall? have I so crapped up my system?

---

### Post by GroovingClockwork on 2010-08-18
Hello,

I have been having similar problems as the original poster with Assistive Technologies; for me it's in Mint 9 (see post [here]("http://forums.linuxmint.com/viewtopic.php?f=18&t=51666")) and earlier Mint 7, but I reckon most of this is not Mint-specific.

Most of the conflict between AT and other things seems password/permission related. This breaks workflow big time. Fortunately going to the terminal and sudo'ing things does not seem to suffer, but sometimes this is inconvenient (esp. as I do not usually use a non-virtual keyboard). Curiously AT also seems to be causing PyChess to hang after it identifies gnuchess as a chess engine...

Moreover mousetweaks (hold to simulate right-click) is buggy when I have AT enabled: it works for a while, then at some point it will cease to work, and sometimes it will suddenly eat up all CPU power, requiring me to kill it or sometimes go the unhappy Ctrl-Alt-Backspace route.

I'm not up to speed with bug reporting -- has this been reported?

I'm trying to use the touchscreen and no keyboard, and properly working AT is vital for this. More importantly, if AT is broken it's bad news for people with input disabilities.

---

### Post by RockStarzInc on 2010-12-04
I'v had the same problem but it has something to do with my POL(PlayOnLinux) and every time I tired to open any of these apps It would give ma a error saying "sources.list.d/playonlinux.list" I installed a bunch of Microsoft software though POL and Wine like Drect X 9.0 c etc. I will have to uninstall to see if this fixes the problem and let you know...

---

### Post by Joleen on 2011-06-29
hello!
I am running ubuntu **11.04**, and apart all other problems, I am facing this one too. Synaptic, Software Center and Update Manager will not work. I have to note that they used to work for more than a month and now they have crashed.Thats what i get for synaptic:
 E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-el%5fGR
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
Software Center just stays loading forever.
 -**Assistive technologies are not enabled.**
 -**To uninstall and reinstall them from the terminal does not work either, this is what I get**:
 maria@petit:~$ sudo apt-get remove update-manager
[sudo] password for maria: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-el%5fGR
**E: The package lists or status file could not be parsed or opened.**
maria@petit:~$ sudo apt-get update software center
E: The update command takes no arguments
maria@petit:~$ sudo apt-get update software-center
E: The update command takes no arguments
maria@petit:~$ sudo apt-get upgrade software-center
Reading Package Lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gr.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-el%5fGR
E: The package lists or status file could not be parsed or opened.

[SIZE=4]*_**ANY ideas??? :(**_*[/SIZE]



 

> **RockStarzInc said:**
> I'v had the same problem but it has something to do with my POL(PlayOnLinux) and every time I tired to open any of these apps It would give ma a error saying "sources.list.d/playonlinux.list" I installed a bunch of Microsoft software though POL and Wine like Drect X 9.0 c etc. I will have to uninstall to see if this fixes the problem and let you know...

---

### Post by guzjd on 2011-06-29
I see you have you tried using:
 
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
 
Try to get everything patched from the shell and try again. Also verify that you are using the right arguments and package names as I see a lot of errors in your pasted output from syntax.
 
Also could have some permissions or file problems with the APT cache.

---

### Post by Joleen on 2011-06-29
get everything pached from the shell means...?
can you tell me the errors you noticed to fix them?
I forgot to mention that when I try to install something from terminal I get again the good old "The *package lists* or *status file* could not be *parsed* or opened'...
> **guzjd said:**
> I see you have you tried using:
 
```
sudo apt-get update
``````
sudo apt-get upgrade
```Try to get everything patched from the shell and try again. Also verify that you are using the right arguments and package names as I see a lot of errors in your pasted output from syntax.
 
Also could have some permissions or file problems with the APT cache.

---

### Post by guzjd on 2011-06-29
> **Joleen said:**
> get everything pached from the shell means...?
can you tell me the errors you noticed to fix them?
I forgot to mention that when I try to install something from terminal I get again the good old "The *package lists* or *status file* could not be *parsed* or opened'...
 
 
The commands I supplied were for patching from the shell. The reason I suspected cache issue was because of the error you mentioned "The *package lists* or *status file* could not be *parsed* or opened"
 
Try the command ```
sudo apt-cache clean
```
 
Also before trying to update again, verify you have IP & DNS configured properly```
sudo ifconfig -a
``` ```
cat /etc/resolv.conf
```
 
---Unless you are using the machine to get to the forums :)
 
The error I noticed was in the output of apt-get udpate (as you can read from the message update doesn't take any arguments).

---

### Post by Joleen on 2011-06-29
Try the command ```
sudo apt-cache clean
```

I cant do that either.Terminal says the function clean is not valid. (I actually made the big mistake to install ubuntu in my language, no idea why i did this, and now I am translating)

---

### Post by guzjd on 2011-06-29
My mistake. I was on the wrong instance :) 
 
Let me try this once more with what I believe is the correct command(s).
 
```
sudo apt-get clean
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

---

### Post by Joleen on 2011-06-30
No...its not working. Should I remove and reinstall ubuntu?

---

### Post by wildmanne39 on 2011-07-01
> **Joleen said:**
> No...its not working. Should I remove and reinstall ubuntu?Hi, run these two commands in a terminal and it should fix your problem.
```
sudo rm /var/lib/apt/lists/* -vf
```
Please use this command exactly as it is written, and do not use with other files or you could wipe out your system. It will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by Joleen on 2011-07-01
Wildmanne39, that one absolutely worked. Everything swell now. You know what caused that list problem?
Thanks everybody for the responses. I appreciate your help.

---

### Post by wildmanne39 on 2011-07-01
> **Joleen said:**
> Wildmanne39, that one absolutely worked. Everything swell now. You know what caused that list problem?
Thanks everybody for the responses. I appreciate your help.Hi, not for sure but is has been happening quite a bit. It was some kind of corruption of the list might be because of an added ppa but not for sure, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by fishcadet on 2011-07-02
Wildmanne39: Just wanted to say a quick thanks.  You solution totally fixed my issues.

---

### Post by wildmanne39 on 2011-07-02
> **fishcadet said:**
> Wildmanne39: Just wanted to say a quick thanks.  You solution totally fixed my issues.
Hi, your welcome.

---

### Post by guzjd on 2011-07-06
This was my next move :) Thanks for posting.  I just like to use the APT util first.

---

### Post by wildmanne39 on 2011-07-07
> **guzjd said:**
> This was my next move :) Thanks for posting.  I just like to use the APT util first.Hi, your welcome.

---

