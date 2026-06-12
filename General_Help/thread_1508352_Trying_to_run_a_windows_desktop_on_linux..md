---
title: "Trying to run a windows desktop on linux."
date: 2010-06-12
forum: General Help
---

### Post by gobluewolverines on 2010-06-12
Okay, im trying to play a simple game and its an executable file. I tried running with wine, and didnt work. So a friend told me about virtualbox and ive tried to download it and my laptop crashed, and i tried again and got an error message about having a tool running when i wasnt supposed to. After i fixed that i try to i was told to try to uninstall anything that got put on, and tried that and got ''virtualbox needs to be reinstalled but cant find an archive for it''. i also get this message when i try to download it. And sometimes after i download the package from a website that has it, it says the file is either corrupt or i dont have the power.. i've been working on this all day i need some help.

---

### Post by wilee-nilee on 2010-06-12
Is this the download site?
[Sun](http://www.virtualbox.org/wiki/Downloads)

And if you want to remove what you have done look in synaptic. And after removing it there go to home hit the ctrl-h key to show hidden files and delete the virtual file and reinstall from my link.

---

### Post by gobluewolverines on 2010-06-12
it is sun. and what is that s thing you said?

---

### Post by wilee-nilee on 2010-06-12
> **gobluewolverines said:**
> it is sun. and what is that s thing you said?
Do you mean synaptic? it is where you get packages and programs loaded and removed it is in system-admin-synaptic look at the status local. Also try to be succinct when you answer to posts, we can't read your mind, nor would we want anybody to.;)

Also only install Vbox with gdebi and look at what it says for missing packages before installing there is a fake root that I forget the name of that has to be installed from synaptic, and possibly one other package. To get gdebi it should just be a automatic click, but you can also right click on the download and choose to open with gdebi.

---

### Post by gobluewolverines on 2010-06-12
aight. launched it and it said.(virtualbox) needs to be reinstalled but cant find an archive for it.
and is says internal error opening cache. please report.

---

### Post by wilee-nilee on 2010-06-12
> **gobluewolverines said:**
> aight. launched it and it said.(virtualbox) needs to be reinstalled but cant find an archive for it.
and is says internal error opening cache. please report.

I think you need to follow my 1st advice go to synaptic remove it go to home remove the hidden files.

When you say launch it I don't know I have to assume your trying to launch it from the menu-tools.

Here is a screen shot of Vbox downloaded with the missing files shown using gdebi. So slow down take a deep braeth and this will go easier if you read the posts and follow directions.
[ATTACH]160220[/ATTACH]

Your trying to by pass steps that will make it impossible to get it working, does this make sense. I can only go by what you tell me and my patience is running low already, with cryptic responses and quick fix attempts without asking questions.;) This is easy stuff if done correctly.

---

### Post by gobluewolverines on 2010-06-12
when i said launched i launched synaptic and got those error messages.

---

### Post by ibe2fly4chu on 2010-06-12
hmm..the file is missing an archive it seems. This is what i would recommend: 
First remove whatever version of vertual box and its plugins currently. 

Open terminal, and first type: sudo apt-get update.

Then after that is finished running type: sudo apt-get install virtualbox-3.2

After that you will be required to re-install w/e windows os you had on there, However this should get rid of the archive problem you have going on there.

Also, what specific game is this. Sometimes the reason why wine doesnt work out of box after you install it is because it needs a few tweaks. for example ffxi's pol will not start in windowed mode...but runs perfectly fine in fulscreen mode. anywho suggesting the game itself my help as someone who knows a trick or so might come across it.

---

### Post by gobluewolverines on 2010-06-12
did both of those commands. Second gave me the same error message as before. Stupid archive.

---

### Post by wilee-nilee on 2010-06-12
> **ibe2fly4chu said:**
> hmm..the file is missing an archive it seems. This is what i would recommend: 
First remove whatever version of vertual box and its plugins currently. 

Open terminal, and first type: sudo apt-get update.

Then after that is finished running type: sudo apt-get install virtualbox-3.2

After that you will be required to re-install w/e windows os you had on there, However this should get rid of the archive problem you have going on there.

Also, what specific game is this. Sometimes the reason why wine doesnt work out of box after you install it is because it needs a few tweaks. for example ffxi's pol will not start in windows mode...but runs perfectly fine in fulscreen mode. anywho suggesting the game itself my help as someone who knows a trick or so might come across it.

That will not provide the preferred puel version which you have to get from sun directly.

---

### Post by wilee-nilee on 2010-06-12
> **gobluewolverines said:**
> did both of those commands. Second gave me the same error message as before. Stupid archive.

Since we are having a hard time communicating, lets shut every thing down, reboot the computer, open synaptic if there are any errors take a screen shot and post them.

---

### Post by gobluewolverines on 2010-06-12
will do! BRB

---

### Post by ibe2fly4chu on 2010-06-12
> **wilee-nilee said:**
> That will not provide the preferred puel version which you have to get from sun directly.

hmm are you certain? because i am pretty sure that is how i installed my virtual box and i never had to pay anything for it. In regards to PUEL being :virtualBox Personal Use and Evaluation License. lol meh stick with wilee-nilee's steps on the synaptic viewer...lol cant go wrong.

---

### Post by techunit on 2010-06-12
Well First I want to know if you have a legitimate copy of Windows To Use you cannot use a OEM copy (one that you got from Dell HP ACER ASUS etc.) You must use one from directly from Windows Or Authorized retailer if you don't have there is no use going further in this. I hope you have considered this. I would try WINE again and if it is a GAME try an app called PlaysOnLinux works well on linux so long as you have decent graphics acceleration you can even run steam. I hope this helps Virtualbox works best if you get it from the Sun/Oracle. I personally love Virtualbox and it seams to work well.

---

### Post by gobluewolverines on 2010-06-12
okay guys. i have to eat. wont be long and ill have a screen shot up in about 20.

---

### Post by wilee-nilee on 2010-06-12
> **ibe2fly4chu said:**
> hmm are you certain? because i am pretty sure that is how i installed my virtual box and i never had to pay anything for it. In regards to PUEL being :virtualBox Personal Use and Evaluation License. lol meh stick with wilee-nilee's steps on the synaptic viewer...lol cant go wrong.

Yes I'm sure, you don't pay for the puel version, it has usb support.

As far as licenses this is a good point so the OP will have to measure their own situation. Fortunately all I'm trying to do is get the Vbox working after that, what is done with it is out of my hands, almost anything can be run in it if the user has enough ram to allocate.

---

### Post by gobluewolverines on 2010-06-12
lol wrong file.

---

### Post by gobluewolverines on 2010-06-12
here it is

---

### Post by wilee-nilee on 2010-06-12
The best way to use the screen shot is to use the select an area to grab.
Lets try this close everything open a terminal and run theses two commands.
```
sudo dpkg --configure -a 

```
```
sudo apt-get install -f
```

Then try synaptic again.

---

### Post by gobluewolverines on 2010-06-12
same message. need archive.

---

### Post by gobluewolverines on 2010-06-12
> **techunit said:**
> Well First I want to know if you have a legitimate copy of Windows To Use you cannot use a OEM copy (one that you got from Dell HP ACER ASUS etc.) You must use one from directly from Windows Or Authorized retailer if you don't have there is no use going further in this. I hope you have considered this. I would try WINE again and if it is a GAME try an app called PlaysOnLinux works well on linux so long as you have decent graphics acceleration you can even run steam. I hope this helps Virtualbox works best if you get it from the Sun/Oracle. I personally love Virtualbox and it seams to work well.

id love to and i just tried playes on linux, but i cant download anything till i get this first problem fixed.

---

### Post by wilee-nilee on 2010-06-12
> **gobluewolverines said:**
> same message. need archive.

So what exactly are you doing to get that error message?

---

### Post by gobluewolverines on 2010-06-12
running those commands. i get the in terminal and snyaptic

---

### Post by wilee-nilee on 2010-06-12
> **gobluewolverines said:**
> running those commands. i get the in terminal and snyaptic

Well I'm stumped in several ways so I hope somebody can help you, good luck.;)

What I would suggest though is to call this thread solved and start a thread in the virtual part of the forum, with a different name as the name I think is having people not even stopping by as it makes no sense.

---

### Post by techunit on 2010-06-12
Ok we need to purge all files relating to Virtualbox and then reinstall it.

But could you try this first...

First open the terminal and type this

```
 sudo aptitude reinstall virtualbox-ose-qt 
```

When it is finished try launching Virtualbox.

---

### Post by gobluewolverines on 2010-06-12
aight. thanks

---

### Post by gobluewolverines on 2010-06-12
> **techunit said:**
> Ok we need to purge all files relating to Virtualbox and then reinstall it.

But could you try this first...

First open the terminal and type this

```
 sudo aptitude reinstall virtualbox-ose-qt 
```

When it is finished try launching Virtualbox.

this is whati got


dale@dale-laptop:~$  sudo aptitude reinstall virtualbox-ose-qt
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
virtualbox-ose-qt is not currently installed, so it will not be reinstalled.
virtualbox-ose-qt is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download

---

### Post by techunit on 2010-06-12
> **gobluewolverines said:**
> this is whati got


dale@dale-laptop:~$  sudo aptitude reinstall virtualbox-ose-qt
[sudo] password for dale: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
virtualbox-ose-qt is not currently installed, so it will not be reinstalled.
virtualbox-ose-qt is not currently installed, so it will not be reinstalled.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download


Ok this looks bad but it tells me alot...

ok now try this in the terminal ok.

```
sudo apt-get install virtualbox-ose-qt
```

After that post what you get ok.

---

### Post by gobluewolverines on 2010-06-12
dale@dale-laptop:~$ sudo apt-get install virtualbox-ose-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox-3.2 needs to be reinstalled, but I can't find an archive for it.
dale@dale-laptop:~$ 

hmm...

---

### Post by techunit on 2010-06-12
If that doesn't work you need to open synaptic

under System>Administration>Synaptic Package Manager

when it loads click "custom filters" in the bottom left corner of Synaptic then click "broken" on the mid left of synaptic in the main view of synaptic you should see a list with red boxes next to them right click and remove or reinstall them.

---

### Post by gobluewolverines on 2010-06-12
> **techunit said:**
> If that doesn't work you need to open synaptic

under System>Administration>Synaptic Package Manager

when it loads click "custom filters" in the bottom left corner of Synaptic then click "broken" on the mid left of synaptic in the main view of synaptic you should see a list with red boxes next to them right click and remove or reinstall them.

it wont let me open synaptic cuz it gives me same message.

---

### Post by techunit on 2010-06-12
could you tell me exactly what that message reads?

---

### Post by gobluewolverines on 2010-06-12
screen shot....

---

### Post by techunit on 2010-06-12
Ok you need to do this disregard what I posted before I edited it. If you didn't do that in time then nothing will happen.

in the terminal type

```
sudo aptitude purge virtualbox-3.2
```

---

### Post by gobluewolverines on 2010-06-12
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REMOVED:
  virtualbox-3.2{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
dpkg: error processing virtualbox-3.2 (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox-3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

---

### Post by techunit on 2010-06-12
Ok try this

in the terminal type

```
sudo aptitude reinstall virtualbox-3.2
```Tell me what you get ok.

update based on what your error message said before I want you to try the above code before the bottom one...

```
sudo aptitude remove virtualbox-3.2
```

---

### Post by gobluewolverines on 2010-06-12
dale@dale-laptop:~$ sudo aptitude remove virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  virtualbox-3.2 
0 packages upgraded, 0 newly installed, 1 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
dpkg: error processing virtualbox-3.2 (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 virtualbox-3.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

---

### Post by techunit on 2010-06-12
I hope you realize your experience is not typical of the normal user and I will continue to try to help you for as long as you need it.

---

### Post by gobluewolverines on 2010-06-12
if i had money, id pay you :p

---

### Post by techunit on 2010-06-12
please try the ```
sudo aptitude reinstall virtualbox-3.2
``` and tell me what you get. If you still get an error message then you need to try this diagnostic listed below. I still want you to post what you get from the code above but If that doesn't work the I am going to need to know what you get from the code below ok. 

```
sudo aptitude show virtualbox-3.2
```

---

### Post by techunit on 2010-06-12
> **gobluewolverines said:**
> if i had money, id pay you :p

No need but thanks for the complement... If I knew where the thanks button I would tell you to do that but I don't. Don't worry if I cant help you someone will.

---

### Post by gobluewolverines on 2010-06-12
dale@dale-laptop:~$ sudo aptitude reinstall virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  virtualbox-3.2 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download
dale@dale-laptop:~$ 

from first one...

---

### Post by gobluewolverines on 2010-06-12
bottom...

dale@dale-laptop:~$ sudo aptitude reinstall virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  virtualbox-3.2 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download
dale@dale-laptop:~$ sudo aptitude show virtualbox-3.2
Package: virtualbox-3.2
State: partially installed
Automatically installed: no
Version: 3.2.4-62467~Ubuntu~karmic
Priority: optional
Section: non-free/misc
Maintainer: 
Uncompressed Size: 0
Description:

---

### Post by techunit on 2010-06-12
Ok did you install virtualbox from a file your downloaded with firefox? If you did you need to run that file. You can do so by double clicking on it. You need to use the exact file you downloaded it from though.

---

### Post by gobluewolverines on 2010-06-12
what do you mean? that confused me..

---

### Post by dcstar on 2010-06-12
Hours of wasted time when instructions for installing all VM environments are already in the Virtualization forum - bizarre.

---

### Post by techunit on 2010-06-12
> **gobluewolverines said:**
> what do you mean? that confused me..
How did you install virtual box the first time? I need to know how you did it to fix it.

---

### Post by gobluewolverines on 2010-06-12
through sun. google chrome.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by techunit on 2010-06-12
> **gobluewolverines said:**
> through sun. google chrome.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Ok the file you downloaded from the site do you still have it if not you need to download it again. When you have it open it by double clicking on it.

---

### Post by gobluewolverines on 2010-06-12
this is what happened..

---

### Post by techunit on 2010-06-12
> **gobluewolverines said:**
> this is what happened..
Did you redownload it or did you use the file that you downloaded the first time. If you did the latter then download it again from firefox.

---

### Post by gobluewolverines on 2010-06-12
i re-downloaded it. idk what the 2nd half of your message means..

---

### Post by techunit on 2010-06-12
OK Give me a few minutes.

---

### Post by gobluewolverines on 2010-06-12
aight.

---

### Post by techunit on 2010-06-12
I have had some problems downloading packages in chrome could you download it in firefox so I know chrome isn't corrupting them?

---

### Post by gobluewolverines on 2010-06-12
aight give me a min....

---

### Post by gobluewolverines on 2010-06-12
same error message. its not the browser.

---

### Post by techunit on 2010-06-12
Ok here is another though try this.

Ok I want you to try this ok.

Go System>Administration>Software sources

In software sources click the Other Software tab

Then click add

and post this line of code in the box that pops up.

```
deb http://download.virtualbox.org/virtualbox/debian karmic non-free
```

Then click add source...

In the terminal type

```
sudo apt-get update
```

after that finishes type

```
sudo aptitude reinstall virtualbox-3.2
```

This should work.

---

### Post by gobluewolverines on 2010-06-13
got this with first command. 

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

---

### Post by gobluewolverines on 2010-06-13
and second command... 


dale@dale-laptop:~$ sudo aptitude reinstall virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  virtualbox-3.2 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download

---

### Post by techunit on 2010-06-13
Ok I want you to post what you get from this diagnostic ok...

```
sudo aptitude show virtualbox-3.2
```

---

### Post by gobluewolverines on 2010-06-13
now what?



Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg [197B]
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US                                                                                        
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release [3,446B]                                                                                                
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                                                                                                           
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                                                                                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                 
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                                                                                                     
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,061B]                                                                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources                                  
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic Release.gpg                                                
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main Translation-en_US             
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic Release
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates Release
Get:6 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B]
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/universe Packages
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe Sources                                                                                            
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/multiverse Packages                                                                                         
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages                                                                                                         
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/multiverse Sources                                                                                          
Fetched 3,993B in 6s (650B/s)                                                                                                                               
Reading package lists... Done
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139

---

### Post by techunit on 2010-06-13
Wait

---

### Post by gobluewolverines on 2010-06-13
this is what i got from your edit.


dale@dale-laptop:~$ sudo aptitude show virtualbox-3.2
Package: virtualbox-3.2
State: partially installed
Automatically installed: no
Version: 3.2.4-62467~Ubuntu~karmic
Priority: optional
Section: non-free/misc
Maintainer: 
Uncompressed Size: 0
Description:

---

### Post by techunit on 2010-06-13
Now try
```
sudo aptitude reinstall virtualbox-3.2
```

---

### Post by techunit on 2010-06-13
You had to do the sudo apt-get update before the aptitude reinstall part ok. I couldn't tell if this was the case.

---

### Post by gobluewolverines on 2010-06-13
dale@dale-laptop:~$ sudo aptitude reinstall virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  virtualbox-3.2 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
Writing extended state information... Done
E: I wasn't able to locate a file for the virtualbox-3.2 package. This might mean you need to manually fix this package. (due to missing arch)
E: Internal error: couldn't generate list of packages to download
dale@dale-laptop:~$

---

### Post by techunit on 2010-06-13
Ok thanks... Ill keep trying...

---

### Post by gobluewolverines on 2010-06-13
Thank you so much for this btw. This is very helpful and i owe you big time.

---

### Post by techunit on 2010-06-13
Try this

```
sudo apt-get clean
```

---

### Post by gobluewolverines on 2010-06-13
didnt do much..

---

### Post by techunit on 2010-06-13
Yeah for got to mention that. Um now try ```
sudo apt-get autoremove
```

---

### Post by gobluewolverines on 2010-06-13
dale@dale-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-3.2
Recommended packages:
  libsdl-ttf2.0-0 dkms
The following packages will be upgraded:
  virtualbox-3.2
1 upgraded, 0 newly installed, 0 to remove and 176 not upgraded.
1 not fully installed or removed.
Need to get 49.5MB of archives.
After this operation, 97.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  virtualbox-3.2
Install these packages without verification [y/N]? y
Get:1 [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free virtualbox-3.2 3.2.4-62467~Ubuntu~karmic [49.5MB]
Fetched 49.5MB in 15s (3,127kB/s)                                                                                                                           
Preconfiguring packages ...
Selecting previously deselected package virtualbox-3.2.
(Reading database ... 85%
dpkg: warning: files list file for package `virtualbox-3.2' missing, assuming package has no files currently installed.
(Reading database ... 115321 files and directories currently installed.)
Preparing to replace virtualbox-3.2 3.2.4-62467~Ubuntu~karmic (using .../virtualbox-3.2_3.2.4-62467~Ubuntu~karmic_i386.deb) ...
Unpacking replacement virtualbox-3.2 ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Setting up virtualbox-3.2 (3.2.4-62467~Ubuntu~karmic) ...
Adding group `vboxusers' (GID 122) ...
Done.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log

---

### Post by techunit on 2010-06-13
Alright! We might be getting some where.

---

### Post by gobluewolverines on 2010-06-13
yay! (:

---

### Post by techunit on 2010-06-13
Tell me what this diagnostic tells you.

```
sudo aptitude show virtualbox-3.2
```

---

### Post by gobluewolverines on 2010-06-13
dale@dale-laptop:~$ sudo aptitude show virtualbox-3.2
Package: virtualbox-3.2
State: installed
Automatically installed: no
Version: 3.2.4-62467~Ubuntu~karmic
Priority: optional
Section: non-free/misc
Maintainer: Oracle Corporation <info@virtualbox.org>
Uncompressed Size: 97.0M
Depends: libc6 (>= 2.7), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libpng12-0 (>= 1.2.13-4), libpython2.6 (>= 2.6),
         libqt4-network (>= 4.5.1), libqt4-opengl (>= 4.5.1), libqtcore4 (>= 4.5.1), libqtgui4 (>= 4.5.1), libsdl1.2debian (>= 1.2.10-1), libssl0.9.8 (>=
         0.9.8f-5), libstdc++6 (>= 4.4.0), libx11-6, libxcursor1 (> 1.1.2), libxext6, libxinerama1, libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4),
         psmisc, adduser
PreDepends: debconf (>= 1.1) | debconf-2.0
Recommends: libasound2, libpulse0, libsdl-ttf2.0-0, dkms, linux-headers, gcc, make, binutils, libhal1 (>= 0.5), pdf-viewer, libgl1, python-central
Conflicts: virtualbox, virtualbox-ose
Replaces: virtualbox
Provides: virtualbox
Description: Oracle VM VirtualBox
 VirtualBox is a powerful PC virtualization solution allowing you to run a wide range of PC operating systems on your Linux system. This includes Windows,
 Linux, FreeBSD, DOS, OpenBSD and others. VirtualBox comes with a broad feature set and excellent performance, making it the premier virtualization software
 solution on the market.

---

### Post by techunit on 2010-06-13
Ok now look under applications for virtualbox should be under system utilities or something

---

### Post by gobluewolverines on 2010-06-13
i dont have system utilities, i have  preferences and administration under system.

---

### Post by techunit on 2010-06-13
sorry

Applications>System Tools>Virtualbox

---

### Post by gobluewolverines on 2010-06-13
lol dont have system tools under appplications.

---

### Post by techunit on 2010-06-13
Ok I am going to make this very simple go to the terminal and type

```
virtualbox-3.2
```

---

### Post by gobluewolverines on 2010-06-13
command not found..

---

### Post by techunit on 2010-06-13
ok well we were somewhere give me a minute to decide what to do next

---

### Post by gobluewolverines on 2010-06-13
yes sir.

---

### Post by techunit on 2010-06-13
In The Terminal Type:

```
sudo apt-get update
```

after that finishes type

```
sudo aptitude reinstall virtualbox-3.2
```

then

```
sudo aptitude purge virtualbox-3.2
```

then

```
sudo apt-get install virtualbox-ose-qt
```

---

### Post by gobluewolverines on 2010-06-13
t:1 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg [197B]
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US                                                                                        
Get:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                                                                      
Get:3 [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release [3,446B]                                                                                                
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]                                                                                                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                                                                                                           
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                                                                                                 
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,061B]                                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US              
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic Release.gpg                                
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main Translation-en_US                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                                           
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/restricted Translation-en_US                             
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/universe Translation-en_US         
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/multiverse Translation-en_US       
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates Release.gpg                
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/main Translation-en_US     
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe Translation-en_US 
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic Release                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                              
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release.gpg                    
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Get:6 [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic Release [1,723B]
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe Packages
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/multiverse Sources
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) karmic/main Packages
Fetched 3,993B in 1s (2,924B/s)
Reading package lists... Done
W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 54422A4B98AB5139
dale@dale-laptop:~$ sudo aptitude reinstall virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REINSTALLED:
  virtualbox-3.2 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 176 not upgraded.
Need to get 0B/49.5MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Preconfiguring packages ...
(Reading database ... 115849 files and directories currently installed.)
Preparing to replace virtualbox-3.2 3.2.4-62467~Ubuntu~karmic (using .../virtualbox-3.2_3.2.4-62467~Ubuntu~karmic_i386.deb) ...
 * Stopping VirtualBox kernel module                                                                                                                          *  done.
Unpacking replacement virtualbox-3.2 ...
Processing triggers for sreadahead ...
Processing triggers for desktop-file-utils ...
Setting up virtualbox-3.2 (3.2.4-62467~Ubuntu~karmic) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
Messages emitted during module compilation will be logged to /var/log/vbox-install.log.

Success!
 * Starting VirtualBox kernel module                                                                                                                          *  done.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

dale@dale-laptop:~$ sudo aptitude purge virtualbox-3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  virtualbox-3.2{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 176 not upgraded.
Need to get 0B of archives. After unpacking 97.0MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 115848 files and directories currently installed.)
Removing virtualbox-3.2 ...
 * Stopping VirtualBox kernel module                                                                                                                          *  done.
Purging configuration files for virtualbox-3.2 ...
Processing triggers for desktop-file-utils ...
Processing triggers for sreadahead ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

dale@dale-laptop:~$ sudo apt-get install virtualbox-ose-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch virtualbox-ose virtualbox-ose-source
Suggested packages:
  diff-doc virtualbox-guest-additions
The following NEW packages will be installed:
  dkms fakeroot patch virtualbox-ose virtualbox-ose-qt virtualbox-ose-source
0 upgraded, 6 newly installed, 0 to remove and 176 not upgraded.
Need to get 11.9MB of archives.
After this operation, 45.7MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main dkms 2.1.0.1-0ubuntu1 [62.1kB]
Get:2 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main fakeroot 1.12.4ubuntu1 [126kB]
Get:3 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic/main patch 2.5.9-5 [100kB]
Get:4 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe virtualbox-ose 3.0.8-dfsg-1ubuntu1.1 [6,331kB]
Get:5 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe virtualbox-ose-source 3.0.8-dfsg-1ubuntu1.1 [962kB]
Get:6 [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) karmic-updates/universe virtualbox-ose-qt 3.0.8-dfsg-1ubuntu1.1 [4,281kB]
Fetched 11.9MB in 5s (2,283kB/s)             
Selecting previously deselected package dkms.
(Reading database ... 115321 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.0.1-0ubuntu1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package virtualbox-ose.
Unpacking virtualbox-ose (from .../virtualbox-ose_3.0.8-dfsg-1ubuntu1.1_i386.deb) ...
Selecting previously deselected package virtualbox-ose-source.
Unpacking virtualbox-ose-source (from .../virtualbox-ose-source_3.0.8-dfsg-1ubuntu1.1_all.deb) ...
Selecting previously deselected package virtualbox-ose-qt.
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.0.8-dfsg-1ubuntu1.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for sreadahead ...
Processing triggers for desktop-file-utils ...
Setting up dkms (2.1.0.1-0ubuntu1) ...
 * Running DKMS auto installation service for kernel 2.6.31-14-generic                                                                                [ OK ] 

Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.5.9-5) ...
Setting up virtualbox-ose (3.0.8-dfsg-1ubuntu1.1) ...
 * Stopping VirtualBox kernel modules                                                                                                                 [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                                 [ OK ] 

Setting up virtualbox-ose-source (3.0.8-dfsg-1ubuntu1.1) ...
Adding modules to DKMS build system
Doing initial module builds
Installing initial modules
Done.
 * Stopping VirtualBox kernel modules                                                                                                                 [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                                 [ OK ] 

Setting up virtualbox-ose-qt (3.0.8-dfsg-1ubuntu1.1) ...

---

### Post by techunit on 2010-06-13
Great! Ok Now Go 

Applications>Accessories>Virtualbox OSE

If it starts you have sucessfully fixed the problem and you can now use a virtual machine.

---

### Post by gobluewolverines on 2010-06-13
Omg your the greatest!

---

### Post by techunit on 2010-06-13
Can I be of any more assistance?

---

### Post by gobluewolverines on 2010-06-13
haha yes. i started it and it says...

''no bootable meduim found. system halted.''

---

### Post by techunit on 2010-06-13
Alright Give Me A few Minutes I will download and install Virtualbox so I can better help you.

---

### Post by gobluewolverines on 2010-06-13
aight

---

### Post by techunit on 2010-06-13
Ok have you set up your virtual machine?

---

### Post by gobluewolverines on 2010-06-13
yeah

---

### Post by techunit on 2010-06-13
OK you need the following to set up a virtual machine...

1. A VMware such as Virtualbox

2. The operating system you wish to install as a VM (in your case windows) so you need a Windows DVD
3. Hard Drive Space for the VM

Do you have these things?

---

### Post by gobluewolverines on 2010-06-13
whats a windows dvd?

---

### Post by techunit on 2010-06-13
Ok you need a windows DVD to install windows in the virtual environment. If you don't have that please can you tell me what the app is you need to install.

Purhaps I can help...

Plus because if you hadn't gotten Virtualbox working you wouldn't have been able to install any apps so don't consider it a complete loss.

---

### Post by gobluewolverines on 2010-06-13
what do you mean the app i need to install?

---

### Post by techunit on 2010-06-13
Your original reason for posting this thread was because you couldn't get WINE to run the app you need... What is the app you need...

---

### Post by gobluewolverines on 2010-06-13
ohh its a game called odyssey online classic

---

### Post by techunit on 2010-06-13
Ok Give me five minutes I think I can get it to run with WINE but I need some time.

---

### Post by gobluewolverines on 2010-06-13
alright... did you download it?

---

### Post by techunit on 2010-06-13
OK do you have wine installed?

---

### Post by gobluewolverines on 2010-06-13
yes

---

### Post by techunit on 2010-06-13
What error did you get when you tryed to install it with wine?

---

### Post by gobluewolverines on 2010-06-13
the game? no error installing it. just when i tried to run the exe file nothing happened.

---

### Post by techunit on 2010-06-13
Oh great ok right click on the OdysseyInstall.exe file and click WINE Windows Program Loader

---

### Post by gobluewolverines on 2010-06-13
no thats not the problem. lol

i have it installed fine. but when i go to launch the actual game (ody.exe) nothing happens. even if i right click on it and select wine.

---

### Post by techunit on 2010-06-13
PlaysOnLinux Try This You can find it in the Ubuntu Software Center.

---

### Post by gobluewolverines on 2010-06-13
what section is it under?

---

### Post by JustinR on 2010-06-13
> **techunit said:**
> PlaysOnLinux Try This You can find it in the Ubuntu Software Center.

PlayOnLinux is a front-end to wine so if it doesn't work in wine the game will not work in PlayOnLinux. PlayonLinux also doesn't have a setup file for the game the original poster is wanting to install.

---

### Post by techunit on 2010-06-13
PlaysOnLinux allows you to run windows games on WINE easier but this is as far as I can help you as my experience extends in this fashion. It has been a pleasure working with you I hope you don't have anymore problems with Aptitude (The Thing that installs Apps)

---

### Post by techunit on 2010-06-13
> **JustinR said:**
> PlayOnLinux is a front-end to wine so if it doesn't work in wine the game will not work in PlayOnLinux. PlayonLinux also doesn't have a setup file for the game the original poster is wanting to install.
Ok Thanks well I don't know it appears that you have more experience in such things...

---

### Post by gobluewolverines on 2010-06-13
hahah thank you again. just one last ? where do i download it. i cant seem to find it

---

### Post by JustinR on 2010-06-13
> **gobluewolverines said:**
> hahah thank you again. just one last ? where do i download it. i cant seem to find it

Hi,

This is the latest stable version from the PlayOnLinux website:
[http://www.playonlinux.com/script_files/PlayOnLinux/3.7.6/PlayOnLinux_3.7.6.deb](http://www.playonlinux.com/script_files/PlayOnLinux/3.7.6/PlayOnLinux_3.7.6.deb)

---

### Post by gobluewolverines on 2010-06-13
On it! thank you both so much! You have been great helps.

---

### Post by gobluewolverines on 2010-06-13
nope, still need help! haha

---

### Post by JustinR on 2010-06-13
With what?

---

### Post by techunit on 2010-06-13
You should install PlaysOnLinux From the Ubuntu Software Center

---

### Post by gobluewolverines on 2010-06-13
all im trying to do is play a simple game but just cant seem to. its an exe and wont work with wine. im trying to set it up with play on linux but idk how

---

### Post by techunit on 2010-06-13
If you don't install it from the Ubuntu Software Center you may risk causing damage considering the amount of work that I went through fixing Aptitude...

---

### Post by gobluewolverines on 2010-06-13
its fine. i just want to play this game. idk how to do it through playonlinux

---

### Post by rukiaEnix on 2010-06-13
please post a snapshot of your synaptic's error or post exactly what the error says

---

### Post by gobluewolverines on 2010-06-13
im not having an error. well i am but idk what to do. ALL IM TRYING to do is launch a game. when i try nothing happens.

---

### Post by JustinR on 2010-06-13
> **rukiaEnix said:**
> please post a snapshot of your synaptic's error or post exactly what the error says

There are no errors more errors, Techunit fixed them all well.

Edit: So specifically, what are you stuck on gobluewolverines?

---

### Post by gobluewolverines on 2010-06-13
this game just wont launch. idk how to even start on playonlinux, and wine just wont do anything

---

### Post by rukiaEnix on 2010-06-13
nothing happens when launching it with playonlinux?

---

### Post by gobluewolverines on 2010-06-13
idk how to launch it on playonlinux

---

### Post by JustinR on 2010-06-13
Okay so wine doesn't appear to be working for that specific game. I suppose we could try VirtualBox.

How is Ubuntu installed on your computer? Is it just Ubuntu, or do you have Ubuntu and Windows on your computer? If its something else please say.

---

### Post by gobluewolverines on 2010-06-13
just ubuntu. the only part im stuck on on virtual box is the bootup. do i need a physical disc that has microsoft on it??

---

### Post by rukiaEnix on 2010-06-13
you need to mount the cd or iso in vb from where you will install windows

---

### Post by gobluewolverines on 2010-06-13
ummm yeah... what the heck does that mean. im sorry. im not the smartest person in the world..
haha

---

### Post by JustinR on 2010-06-13
Have you ever had Microsoft Windows installed on your computer at one point or another? It doesn't matter what version.

---

### Post by gobluewolverines on 2010-06-13
yeah, before linux

---

### Post by rukiaEnix on 2010-06-13
at virtualbox you have the option of mounting a cd or iso for installing virutalbox, virtualbox is like a pc and it needs an operative system so you have to install it with a cd or an iso in this case you want windows so you need a windows install cd or iso

---

### Post by gobluewolverines on 2010-06-13
where and how would i get that?

---

### Post by rukiaEnix on 2010-06-13
the mount option or the windows cd?

---

### Post by JustinR on 2010-06-13
Did you buy your computer new? If so it should have came with a Microsoft Windows Reinstallation Disk. Which you are able to use in VirtualBox,if the windows version is correct.

---

### Post by gobluewolverines on 2010-06-13
no. unfortunatly its my dads old work laptop. but i would just like the cd that would let me run windows xp os. how would i get one? i have another comp in the house that has xp

---

### Post by JustinR on 2010-06-13
Well if it is an old work laptop there is a possibility of of contacting the original manufacturer and you could request a free CD if you still have the original windows license key. But if you don't have the original license key the only option you would have is to buy another copy of Windows.

---

### Post by rukiaEnix on 2010-06-13
google for windows ue

---

### Post by gobluewolverines on 2010-06-13
okay i googled it. most of em are in spanish. what do i do now?

---

### Post by JustinR on 2010-06-13
> **gobluewolverines said:**
> okay i googled it. most of em are in spanish. what do i do now?

Windows UE is a hacked version of windows that bypasses activation, which is illegal so I wouldn't go that route..

---

### Post by rukiaEnix on 2010-06-13
yep i know.. go to [http://www.isohunt.com]("http://www.isohunt.com/") and look for windows

---

### Post by rukiaEnix on 2010-06-13
hacked but works grate :p

---

### Post by gobluewolverines on 2010-06-13
so these are torrent that id mount on a cd? is that what alcohol 52% is?

---

### Post by rukiaEnix on 2010-06-13
you will use torrent for download an iso, you will mount the iso

---

### Post by gobluewolverines on 2010-06-13
so download the iso mount it on a blank cd and use that?

---

### Post by JustinR on 2010-06-13
> **rukiaEnix said:**
> hacked but works grate :p

Linking to warez sites like that is grounds for a banning on the Ubuntu forums..:popcorn:

---

### Post by rukiaEnix on 2010-06-13
at vritualbox mount cd option choose it from an iso, and then you choose the iso you download

---

### Post by JustinR on 2010-06-13
Here's a screenshot of what you need to do in VirtualBox.
[http://www.virtualbox.org/manual/images/vm-settings-harddisk.png](http://www.virtualbox.org/manual/images/vm-settings-harddisk.png).

The menuitem with the CD icon thats says Empty is what you need to set to your "Windows disk"

---

### Post by gobluewolverines on 2010-06-13
not working. im goin to bed boys. continue on this tomorrow?

---

### Post by JustinR on 2010-06-13
Sure have a good night. ):P

---

### Post by rukiaEnix on 2010-06-13
ok tomorrow but you just need an iso. Remember virtualbox is like a pc and it needs an OS for make it work so you need to install it and virtualbox gives you the option of installing from your cd drive or from an iso

---

### Post by gobluewolverines on 2010-06-13
haha you too!8)

---

### Post by wilee-nilee on 2010-06-13
> **JustinR said:**
> Linking to warez sites like that is grounds for a banning on the Ubuntu forums..:popcorn:

And exposing the OP to possible virus's, malware keyloggers, worms...etc. in the downloaded cracked copy.

---

### Post by gobluewolverines on 2010-06-13
okay im back. now exactly what do i need to do? i need to download an iso file? can somebody walk me through this as if i was like... 8? haha. im only a freshman.

---

### Post by techunit on 2010-06-13
> **rukiaEnix said:**
> please post a snapshot of your synaptic's error or post exactly what the error says

I fixed that error bout 5 pages ago

---

