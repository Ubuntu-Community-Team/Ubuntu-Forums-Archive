---
title: "New to Linix"
date: 2009-09-27
forum: General Help
---

### Post by ExTruckie on 2009-09-27
Hello 
I am new to Linux and an building a file/print server.
I have installed ubuntu and when the machine boots I can't get past the logon 
I enter my user and password 
and goto mark@ubuntu:~$ 
What do I enter there and how do I automate it so if the power fails the machine reboots and restarts?

---

### Post by tuxxy on 2009-09-27
Thats your command prompt, you have already logged in.  If you installed Ubuntu server then you wont have a user interface unless you install one.  I think you need to familiarize yourself with the command line interface and also Ubuntu server before asking specific questions.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by Roasted on 2009-09-27
Did you install Ubuntu Server? Ubuntu Server does not have a GUI to it. Perhaps you should check on that before we go any further, because it's confusing that when you log in that's all you see.

---

### Post by ExTruckie on 2009-09-27
Thanks

would it be advisable to have a gui based interface over a command line one for us 
command line illiterates?

If so how would I do that?  Pardon my ignorance but I was never very good with command line OS.

I was told this was the best distro for what I wanted to do

---

### Post by ExTruckie on 2009-09-27
> **Roasted said:**
> Did you install Ubuntu Server? Ubuntu Server does not have a GUI to it. Perhaps you should check on that before we go any further, because it's confusing that when you log in that's all you see.
Yes it is ubuntu server

---

### Post by akakingess on 2009-09-27
You do not need to install the server version just to set up a machine to share files and printers.  I do this at home, I have the desktop edition installed and then share what I need to with no problems, although you may need Samba if you are sharing with some Windows machines, but that is another question.

---

### Post by ExTruckie on 2009-09-27
> **akakingess said:**
> You do not need to install the server version just to set up a machine to share files and printers.  I do this at home, I have the desktop edition installed and then share what I need to with no problems, although you may need Samba if you are sharing with some Windows machines, but that is another question.


So what your saying is that i can use the desktop version  
This machine will be on all the time without a monitor on except for maintenance.

---

### Post by gali98 on 2009-09-27
Your question about rebooting after a powerloss will be answered by your BIOS.
It is really machine specific, so just hunt around until you find the right option.
Kory

---

### Post by akakingess on 2009-09-27
> **ExTruckie said:**
> So what your saying is that i can use the desktop version  
This machine will be on all the time without a monitor on except for maintenance.

Unless you are going to be hosting a web page on the internet from this machine then there is no reason not to go with the desktop version, first of all, it installs with a GUI, so it is easier for someone new to manage, and it will do everything that you need it to, within reason...:)

---

### Post by ExTruckie on 2009-09-27
Im dling **Ubuntu 9.10**


as I type this  and will attempt an install after burning it to cd.

---

### Post by akakingess on 2009-09-27
Congrats and good luck, please let us know if you need any more assistance or have any questions!!! The computer I am posting this message from is my house's file server, I have another machine with the printer attached playing printer server.

Edit:  This is probably too late, but you may have wanted to go with 9.04 until the official release of 9.10, but it is still pretty stable, I have it on 1 of my 3 Ubuntu machines.

---

### Post by ExTruckie on 2009-09-27
> **akakingess said:**
> Congrats and good luck, please let us know if you need any more assistance or have any questions!!! The computer I am posting this message from is my house's file server, I have another machine with the printer attached playing printer server.

Edit:  This is probably too late, but you may have wanted to go with 9.04 until the official release of 9.10, but it is still pretty stable, I have it on 1 of my 3 Ubuntu machines.


I aborted the dl of 9.10 and and getting 9.04

---

### Post by Bölvaður on 2009-09-27
> **ExTruckie said:**
> So what your saying is that i can use the desktop version  
This machine will be on all the time without a monitor on except for maintenance.

No there is no need for the desktop version, it might be nice for you to try it out, but there is no need for it. It will use many much much much more RAM than you will need.

There is no need to have monitor at the computer except the first time when you install it. After that you can log into the computer through SSH from a different computer.
Normal SSH only has command line interface, which is what you should aim for. There is a way to add GUI to it so you can open GUI, but as I said, there is no need for it for you.

It's google time :D

---

### Post by ExTruckie on 2009-09-27
This is way to much  
All I wanted is a cheep (Free) file and print server for my network 
Ill manage somehow

---

### Post by akakingess on 2009-09-27
It's really not that bad once you get the download done, install is easy and goes fairly quickly, and this is the best system, I hope you don't/don't think you will regret it when all is said and done.

---

### Post by ExTruckie on 2009-09-27
Well I'm back after installing the desktop version 
I still can't login 
ubuntu loads to mark login: i put in the user and password and it comes up incorrect login

Am I missing something?

---

### Post by akakingess on 2009-09-27
> **ExTruckie said:**
> Well I'm back after installing the desktop version 
I still can't login 
ubuntu loads to mark login: i put in the user and password and it comes up incorrect login

Am I missing something?

Just be sure about capitalization, even on the username, because Linux is case-sensitive, even on file names and everything. So, Admin is different than admin. Other than that, as long as you are using the username and password that you entered when you were setting it up (installing), it should work. Let me know what else you try and if you are still having trouble.

---

### Post by cariboo on 2009-09-27
Type:

```
startx
```

at the prompt this may start the desktop.

---

### Post by ExTruckie on 2009-09-28
Ok  Lets assume :lolflag:(I know about assuming):lolflag: but for the sake of argument, that I got the login or password entered wrong when I set it up and don't know what it is.  How do I fix it??

Another thing is that I now have both the desktop version and the server version installed
So, how do I wipe out the server install? Or for that matter erase the whole HD and start over.. 

I am too use to windows and how to do it there.  :(

---

### Post by akakingess on 2009-09-28
If you are going to wipe out the HD and start over anyway, then don't worry about the username/password issue.  I would just start from scratch, boot from the CD and format the drive and partition it accordingly, 1 for Swap, 1 for root ( / ) , and 1 for home, if you would like a seperate partition for your home directory, which is a good idea so that if you need to reinstall Ubuntu in the future, your documents and such will be saved on that partition and remain untouched as only the root or / partition will be affected when installing just the operating system. Sorry if I rambled on a little.  Good luck.

Edit: Also, as far as sizing of partitions, let's say you have a 100 GB drive, I would use 20 GB for root or / (where Ubuntu is actually installed) and maybe 2 or 3 GBs for the Swap partition, and then the rest for the home partition. That is just a preference and everyone does it differently, but that was just to show you an example of how to break up the drive.

---

### Post by ExTruckie on 2009-09-28
Well I reinstalled and now I can at least login, however thats all I can do,

I can't even get the gui to come up all I get after entering my login and password. 
I get this  
mark@mark:~$ 


I'm about to give up. 
There has to be an easier way????:confused:

---

### Post by akakingess on 2009-09-28
you should be able to type in startx and that should bring up the gui, but someone else will have to answer as to why it's not coming up automatically.

---

### Post by ExTruckie on 2009-09-29
Well I am stumped!!

I should mention that I am doing this install **_without_** an network card or internet connection.  Could this be an issue since ubuntu cannot do automatic updates?

Thanks for all the help so far.

---

### Post by 3rdalbum on 2009-09-29
Merely typing "startx" will NOT work. X needs to be started as root.

A better way of doing it is this:

```
sudo gdm
```

No idea why it isn't automatically coming up though.

---

### Post by ExTruckie on 2009-09-29
I typed in sudo gdm and  after retyping my password it said gdm already running aborting.

and goes back to this below: 

mark@mark:~$

---

### Post by oldos2er on 2009-09-29
What are the hardware specs of your computer?

---

### Post by ExTruckie on 2009-09-29
My machine is  put together with spare parts I have lying around. 
K6-500 cpu 
128M ram
30Gb hd 
DVD Burner for optical drive 
an old isa video card 
no network card yet

mobo can support an older pci  or agp card 

This is why I went with the server version initially. :popcorn:

---

### Post by Yvan300 on 2009-09-29
Wow those specs are really poor, maybe it just doesn't have the power to run the GUI. I 'm not an expert in servers but your would just have to learn the commands of the CLI.

---

### Post by ExTruckie on 2009-09-29
> **Yvan300 said:**
> Wow those specs are really poor, maybe it just doesn't have the power to run the GUI. I 'm not an expert in servers but your would just have to learn the commands of the CLI.
I was beginning to realize that as I went along

---

### Post by JigglyWiggly_ on 2009-09-29
In all honesty if you are new to a *nix system, without a gui it's going to be a pain. Sure you can do it in cli, and I like people who do so, but (i am going to get scolded for this), I would just run Windows. Since gnome won't start, Windows XP or server 2k3 will rum on those specs with a gui. 

You could try debian, but I am pretty sure it will do the same thing, what will probably work is freebsd. Though it is less user fun than Ubuntu/Debian, infact it's not linux at all, it's freebsd, but if you know how to use one, you pretty much how to use the other.

So here is what I would do:
1.Try freebsd if that doesn't work, even though it should
2. Try debian
3. If those both don't work go with Windows. (Or learn how to become handy with the CMI)

---

### Post by orange-wedge on 2009-09-29
youre probably going to hate this recommendation since you just got finished installing the desktop version of ubuntu.  judging from your specifications you may be better off with xubuntu or configuring a low memory gui version of ubuntu from the server install, but you will need a connection to the internet for the pc to do the latter.  personally i would recommend configuring the gui from the server installation (i really like fluxbox).

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

also you could easily remote login to the gui either by setting up a vnc-server or xdmcp.  since gdm is already running all you need to do is setup remote login through xdmcp and then export your desktop to a remote machine.  a very nice windows x-server is xming.  you will need to setup an ssh server on the linux machine and also install putty on your windows box so you can export the x application via ssh to your windows box.

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

personally i would recommend sticking with the linux install.  since this is a remote server, linux is perfect for this application.  if you do a low memory install you will have machine that at out perform xp.  it may take you a few days of searching the web for the answers and staying on the forums to get everything tweaked just right, but it will be worth it.  head to the irc ubuntu channel if you need some one-on-one support.

good luck!

---

### Post by oldos2er on 2009-09-30
> **ExTruckie said:**
> My machine is  put together with spare parts I have lying around. 
K6-500 cpu 
128M ram
30Gb hd 
DVD Burner for optical drive 
an old isa video card 
no network card yet

mobo can support an older pci  or agp card 

This is why I went with the server version initially. :popcorn:

 With those specs, I'd try something like Puppy Linux. The 'buntus are going to be too heavy.

---

### Post by JUDOHAWK on 2009-09-30
> **oldos2er said:**
> With those specs, I'd try something like Puppy Linux. The 'buntus are going to be too heavy.

TC this is a good idea, Puppy is a pretty fun distro to work with aswell.  Try it out.

---

### Post by ExTruckie on 2009-10-24
Hello I'm back 
I picked up some more ram , nic, and an agp vid card so now my sys specs are and I can still get 512M more ram by removing the 2 64 M sticks
AMD K6-500 cpu
384M ram
30Gb hd 
DVD Burner for optical drive 
Nvidia Geforce2 agp vid card
10/100 nic
I am in the process of installing ubuntu desktop.
I tried puppy linux until i got the extra ram, now it seems a bit limited.

So far all is well. I like the feel of ubuntu. 
updated all programs and just did video drivers. 
I can see my windows box on the ubuntu machine, now all I have to do is get the windows box to see the ubuntu box.

---

### Post by ExTruckie on 2010-10-30
I was going through my post and realized I left this one hanging out there.

An update, a year later...  

After my last post I got everything working and was a happy camper. 
Recently I got a pc from a person at work who replaced theirs after the HD died.
I pulled the HD out of my previous server and threw it in the cast off, powered it up ad discovered it was a P4 2.8 Ghz dual core, w 2.5Gb of ram with a max of 4Gb. These are better than the specs of my current windows box.. (I know buzz off!!):P  

I will be in the near future switching machine roles and be putting a raid 1 into the reconfigured server for additional storage and redundancy, while keeping the existing HD for the os. The mobo  supports raid on the sata drives. I am looking into raid on Linux and see that software raid is preferred to hardware raid. Also should I upgrade to Maverick Meerkat since I am using 9.04
Any suggestions??

Thanks

---

