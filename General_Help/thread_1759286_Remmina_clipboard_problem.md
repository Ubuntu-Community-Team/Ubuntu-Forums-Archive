---
title: "Remmina clipboard problem"
date: 2011-05-15
forum: General Help
---

### Post by paxxus on 2011-05-15
Hi,

I'm using remmina as my remote desktop client. My problem is that there is no synchronization of the clipboards. The local and the remote machines seem totally isolated w.r.t. the clipboard. I have this problem both when connection to Windows using RDP and when connection to ubuntu 11.04 using VNC. My local machine is ubuntu 9.10.

I used rdesktop before when connecting to the Windows machine and the clipboard worked perfectly. I switched to remmina as I needed to also connect to ubuntu 11.04.

I feel I'm missing something stupid since it so consistently does not work.

I have NOT disabled clipboard sync in remmina (default is to sync).

---

### Post by paxxus on 2011-05-16
Anybody have an idea?

---

### Post by paxxus on 2011-05-24
I tried to install remmina on ubuntu 11.04, so a new OS compared to  before and a new remmina version (now 0.9.3) compared to before. Still  the same, not possible to copy/paste between client and server.

This is very sad. I'm now forced to abandon remmina :(

---

### Post by sefs on 2011-05-29
Do you mean that you cannot copy and paste between the computer running remmina and the computer to which remmina is connected?

I am on Ubuntu 10.04.2 and using Remmina, and was completed surprised to realize that I could copy and past between the local and remote computer.  Never knew that was possible with rdp.  I did not do anything fancy, I just installed it.

I am using Remmina directly from the remmina repos and not from the one that comes in the ubuntu repos.  I am not sure if that makes a difference though.  

```

deb http://ppa.launchpad.net/llyzs/ppa/ubuntu lucid main

```

---

### Post by paxxus on 2011-05-31
Thanks for the reply sefs. Yes I mean that I cannot copy and paste between the computer running remmina and the computer to which remmina is connected. This has always worked for me with rdesktop and it is critical for me that this works. I have tried remmina both on ubuntu 9.10 and on 11.04, with exact same behavior. On both these systems rdesktop can copy/paste no problem.

I installed remmina from the Synaptic Package Manager as I don't like hacking around. I did however try your command (on 11.04) and got:

```
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
```

---

### Post by sefs on 2011-05-31
> **paxxus said:**
> Thanks for the reply sefs. Yes I mean that I cannot copy and paste between the computer running remmina and the computer to which remmina is connected. This has always worked for me with rdesktop and it is critical for me that this works. I have tried remmina both on ubuntu 9.10 and on 11.04, with exact same behavior. On both these systems rdesktop can copy/paste no problem.

I installed remmina from the Synaptic Package Manager as I don't like hacking around. I did however try your command (on 11.04) and got:

```
No command 'deb' found, did you mean:
 Command 'debc' from package 'devscripts' (main)
 Command 'derb' from package 'libicu-dev' (main)
 Command 'dab' from package 'bsdgames' (universe)
 Command 'debi' from package 'devscripts' (main)
 Command 'xdeb' from package 'xdeb' (universe)
deb: command not found
```


That's not a command  you run.  That's a repository you add to synaptic.

See here for help on repositories [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu).

But basically this page shows you how to set up the remmina repo.

[http://ubuntuguide.net/remmina-free-and-open-source-remote-desktop-client-written-in-gtk](http://ubuntuguide.net/remmina-free-and-open-source-remote-desktop-client-written-in-gtk)

Note they show examples for 9.04, and 9.10.  If you are using a different version of ubuntu just change the name of ubuntu to suit from karmic or jaunty to what it is you are using.

---

### Post by paxxus on 2011-05-31
Thanks for your help sefs. I uninstalled my remmina and reinstalled as per the descriptions, I did however get the same remmina version again and there was no change in the behavior.

I give up on remmina.

I now use rdesktop when connecting to Windows, this works really well. For connecting to my ubuntu at the office I have now gone over to using screen instead. I only use terminals and emacs anyways so this is quite OK (and fast).

---

### Post by pituzik on 2012-03-13
Some Remmina users got a problem with clipboard: copy-paste operations doesnt work properly as like clipboard doesnt sync at all. The solution is to keep tsclient package installed alongside with remmina. I didnt catch what does tsclient package contains for clipboard working, but it solves the problem. Hope that would be helpful.

Thanks!

---

### Post by dcstar on 2012-03-14
> **pituzik said:**
> Some Remmina users got a problem with clipboard: copy-paste operations doesnt work properly as like clipboard doesnt sync at all. The solution is to keep tsclient package installed alongside with remmina. I didnt catch what does tsclient package contains for clipboard working, but it solves the problem. Hope that would be helpful.


Pffttt. Commenting on issues from 9 months ago has no value whatsoever.

In the current version of Remmina (0.9.3) cut and paste works fine, I just tested it.

---

### Post by thaelim on 2012-03-22
> **dcstar said:**
> Pffttt. Commenting on issues from 9 months ago has no value whatsoever.

In the current version of Remmina (0.9.3) cut and paste works fine, I just tested it.

Be nice now... it is in fact broken in Remmina 0.9.99.1 (Precise version).

---

### Post by dcstar on 2012-03-23
> **thaelim said:**
> Be nice now... it is in fact broken in Remmina 0.9.99.1 (Precise version).

Remmina 0.9.99.1 does cut and paste perfectly on the 12.04 system I just tested it on connecting to a Windows server.

---

### Post by fluffman86 on 2012-03-23
> **dcstar said:**
> Remmina 0.9.99.1 does cut and paste perfectly on the 12.04 system I just tested it on connecting to a Windows server.

I'm using the latest 64-bit Precise build with Remmina 0.9.99.1 and I cannot copy something in Ubuntu and paste into Windows. Copy/Paste inside of Windows works fine. Copying on one windows server and pasting to another does not.

Has anyone found a work-around for this?

---

### Post by Enverex on 2012-03-30
This may be an upstream issue as I'm using 0.9.99.1 on Arch Linux and have exactly the same problem. It's an absolute nightmare.

---

### Post by ergosteur on 2012-04-18
Seems tsclient was removed from the Ubuntu repos, so that doesn't work anymore.

On Kubuntu Precise here, with remmina 0.9.99.1 and no copy-paste between Linux client and remote Windows computers. Also my mouse scroll wheel doesn't seem to work.

Bug report at github: [https://github.com/FreeRDP/Remmina/issues/13](https://github.com/FreeRDP/Remmina/issues/13)

---

### Post by sefs on 2012-04-29
Just upgraded to 12.04 and remmina 0.9.99.1 is installed. But not cut and paste and no tsclient :)

---

### Post by toddr on 2012-05-01
I am running 12.04 and I also confirm that copy and paist, as well as scroll wheel operation are not functioning.  I wish that this would be fixed.

---

### Post by agarcial on 2012-05-01
This link helps for the scrolling problem:
[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/952964](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/952964)

Still nothing for the copy/paste.

---

### Post by dcstar on 2012-05-02
> **agarcial said:**
> This link helps for the scrolling problem:
[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/952964](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/952964)

Still nothing for the copy/paste.

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522)

---

### Post by toddr on 2012-05-04
After a recent update, scrolling is now working :)  Now just copy and paist and the world will be a better place.

---

### Post by susianna on 2012-05-04
comprare il ****** senza ricetta          
[ costo in farmacia del ******   ](http://www.******-it.com/ )

---

### Post by sefs on 2012-05-04
> **toddr said:**
> After a recent update, scrolling is now working :)  Now just copy and paist and the world will be a better place.

Ah yes it is. Thank you.

---

### Post by mtbeedee on 2012-05-15
Running Remmina 0.9.99.1 on Precise against a windows 7 32 bit machine and cut and paste doesn't work.

What happened to tsclient?  It worked a thousand times better than any of these newer RDP programs do...

---

### Post by Zack83 on 2012-05-24
Hallo,

browsing in several forums I've found up that a guy named Jean-Louis Dupond has already developed a patch to solve this bug.

Here you can find the patch: [https://launchpad.net/~dupondje/+archive/ppa](https://launchpad.net/~dupondje/+archive/ppa)

and here's the thread where he introduces it: 

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522)

Cheers,

Giacomo

---

### Post by dcstar on 2012-05-30
The current version of Remmina in precise-proposed seems to have fixed this issue.

---

### Post by colin.p on 2012-05-30
I am running PreciseX64 on a laptop and xubuntu lucidX386 on a server and I can copy/paste to the server just fine.

---

### Post by sefs on 2012-06-07
I just got some updates (June 7, 2012) for Ubuntu 12.04 64-bit which included an update to remmina. 

It seems this updates brings back copy & paste ... for now :) Thank the Lord.

---

### Post by carwe on 2012-08-01
Running 12.04, newest version of Remmina from the repos. Copy/paste works more or less but is buggy. Doesn't work with scandinavian characters.

---

### Post by Charybdisz on 2012-09-22
Thanks you guys saved my life lol.

Clipboard works again in RDP! I follwed this: [https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522/comments/124](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522/comments/124)

> I have found this to be a problem NOT exclusive to RDP in Linux. It is also reported as a long standing problem in all Windows OS's when running RDP. Once you have the remote session open, run the Windows task manager (right click the task bar and select task manager) and look for the process rdpclip.exe. End task on this process and then at the top of the task manager window, click on File > New Task (Run) and enter rdpclip.exe in the dialog box and run it. Now try your clipboard and see if it is working.

If that fixes it for you, then it's a Windows problem. I have created a small batch file that I leave on the Windows desktop that I can click on to quickly end and restart the rdpclip.exe.

Place the following in a file called clipboard.bat
Taskkill.exe /im rdpclip.exe
Rdpclip.exe

I actually got this info from a Windows discussion site where many people who only run Windows were having the same problem.

Turned out it was a bug in Windows Server 2008. Oh how I hate that ****** Window$ $erver nightmare! it sucks so much.

---

### Post by mwildam on 2012-11-07
> **mtbeedee said:**
> What happened to tsclient?  It worked a thousand times better than any of these newer RDP programs do...
sudo apt-get install rdesktop

and you have the same effect - remmina then can transfer clipboard again.

---

