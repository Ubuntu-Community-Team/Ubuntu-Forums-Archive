---
title: "Jaunty creates viruses..??"
date: 2010-02-16
forum: General Help
---

### Post by Thanh-BKK on 2010-02-16
Hello.

I observed this already some time ago at my office however by then i still had one machine running Windows. Now this is no longer the case, all office is 100% Ubuntu.

And this Ubuntu appears to generate weirdly-named files in folders that are shared via Samba - files like "kbpfsg.exe" and "khw" (no file extension on that one). 

Accessing such files with Windows (when there was still a Windows machine) immediately generated a virus alert from Avast, finding some sort of trojan.

Now, as mentioned, there is no more Windows but those strange files are still being created, i delete them but next time i access such shared folder from my machine, bingo, there they are again.

This never happens at my home where i also share some folder via Samba. 

What could be the cause of this, and how can it be stopped? Even though those files can't do any harm now they still clutter the otherwise tidy folders. 

Kind regards......

Thanh

---

### Post by crlang13 on 2010-02-16
That's interesting.

I think it is possible to pick up a Windows virus on an Ubuntu machine, it just doesn't do anything until it gets to Windows.

It may not be a case of Jaunty creating, but viruses coming from one of the users at your office (through internet at work or getting brought from home on a usb).  Or they could be coming in from emails from outside the office.

---

### Post by Thanh-BKK on 2010-02-16
Hi :)

Yeah i factored all those in.... however:

- Ubuntu may pick up a Windows virus, but would not execute it - hence said virus could not propagate (none of the machines have Wine installed)

- If someone was to download stuff, it still could not propagate - Wine-less Ubuntu doesn't run .exe files even if you try

- Nobody uses USB sticks or other media from home, and the office USB sticks are clean.

- Files are being created even if i myself start up the machines, delete the files, shut down and start up again - files are there again. Without any of the machines having accessed the internet (no browser opened, updating disabled). 

- The weird files are being created exclusively in the root of Samba-shared folders, and every machine has the exact same files.

- Tomorrow they'll change names, if i don't delete them i'll have two of each (the .exe and the other) tomorrow with different names but again identical on all of the machines! 

Best regards....

Thanh

---

### Post by a cup of tea on 2010-02-16
> **Thanh-BKK said:**
> - Files are being created even if i myself start up the machines, delete the files, shut down and start up again - files are there again. Without any of the machines having accessed the internet (no browser opened, updating disabled). 

Disconnect the machine from the network (pull the ethernet cable out of the computer, or change your wireless settings to not automatically connect to any networks).  Then, get rid of the files, restart, and see if the files are recreated.

---

### Post by Thanh-BKK on 2010-02-16
Hi.

Done that - seems the files are being created the instant another machine accesses the shared folder. Regardless which machine accesses which shared folder, the folder being accessed has those files in the moment the folder is being opened.

All machines on the network run Ubuntu Jaunty, all sharing is done with Samba (NO such problem if FTP is used! But i don't want to run FTP servers on all of them all the time). Each machine has a fixed, real IP on a leased line system.

Kind regards.....

Thanh

---

### Post by amsterdamharu on 2010-02-16
> Done that - seems the files are being created the instant another machine accesses the shared folder.

I am confused, how could you unplug the network cable/wireless and have another machine access the share? 
Is the file not created as long as no **other** machine accesses it? 
Could you try the following (sorry might take some time but it will show what is creating the files). Unplugged machine.
Is it created when you start samba service?
Is it created when you access the share when the share is read only?
Is it created when you access the share when the share is read write?

I cannot find anything on samba virus as in Samba being infected by a virus. But this seems to be an interesting development (be it not a good one).
Should report it to the samba dev team so they can investigate.

---

### Post by scottuss on 2010-02-16
See this thread:

[http://ubuntuforums.org/showthread.php?t=1384255](http://ubuntuforums.org/showthread.php?t=1384255)

It's likely to be something similar

(Check if anyone is using DC++)

---

### Post by Thanh-BKK on 2010-02-16
Hi :)

Unfortunately this is a working environment and these shares are in use so i can't start messing with them now.

However what i did was starting the computer, deleting the files, shutting that computer down. Then starting it again - no files. Then access the shared folder from another machine and BAM there were those two files. 

Which is why i am thinking that Samba must somehow HOWEVER at my home and my private computers (two desktops and two laptops, one of which runs Windows) this does NOT happen despite it being the same Ubuntu 9.04 Jaunty and probably (didn't check...) the same Samba version. 

The only difference is that at home each machine has a static LAN IP (i.e. they are all connected to my router, the laptops wirelessly, the desktops with ethernet cables) while here at the office they are all on static real IP's from the ISP, connected to a switch via ethernet cables and online via leased line with 32 IP's. 

And, as mentioned, if i use ftp instead of Samba to access those folders then no strange files are being created, only via Samba. 

Best regards.......

Thanh

---

### Post by scottuss on 2010-02-16
> **Thanh-BKK said:**
> Hi :)

Unfortunately this is a working environment and these shares are in use so i can't start messing with them now.

However what i did was starting the computer, deleting the files, shutting that computer down. Then starting it again - no files. Then access the shared folder from another machine and BAM there were those two files. 

Which is why i am thinking that Samba must somehow HOWEVER at my home and my private computers (two desktops and two laptops, one of which runs Windows) this does NOT happen despite it being the same Ubuntu 9.04 Jaunty and probably (didn't check...) the same Samba version. 

The only difference is that at home each machine has a static LAN IP (i.e. they are all connected to my router, the laptops wirelessly, the desktops with ethernet cables) while here at the office they are all on static real IP's from the ISP, connected to a switch via ethernet cables and online via leased line with 32 IP's. 

And, as mentioned, if i use ftp instead of Samba to access those folders then no strange files are being created, only via Samba. 

Best regards.......

Thanh

Um, OK but did you read the thread that I suggested? It's pretty much exactly what you're describing.

Files don't just appear magically!

---

### Post by Thanh-BKK on 2010-02-16
> **scottuss said:**
> See this thread:

[http://ubuntuforums.org/showthread.php?t=1384255](http://ubuntuforums.org/showthread.php?t=1384255)

It's likely to be something similar

(Check if anyone is using DC++)

Hi :)

Yes that is exactly the same issue. Just that i am positive that there is no DC++ or any file sharing software (apart from the default Transmission) on any of the machines here.

Changing shared folders is no remedy in my case because that has been done multiple times, first they were flash drives, then folders on the actual machines. 

As soon as a shared folder is accessed the two files (empty text type file with no extension and named kh-something (this changes) plus one weirdly named .exe with some 791.5 kb in size. 

I tried actually executing these .exe files in a Windows VM and they wouldn't execute, the VM was also NOT infected by anything in that process so the virus warning may well be a false positive..... 

Kind regards.....

Thanh

---

### Post by KeLa on 2010-02-16
> **Thanh-BKK said:**
>  while here at the office they are all on static real IP's from the ISP, connected to a switch via ethernet cables and online via leased line with 32 IP's. 


So in office all your computers are connected to internet without any firewall boxes?
Are the server also accessible from internet?

---

### Post by Thanh-BKK on 2010-02-16
Hi.

That is correct, no firewalls. But no servers either, they are just ordinary desktop PC's that run office-type applications. And the files being shared are mostly .doc and .pdf type files. 

Hmm wait a minute... actually i think that thing from the ISP here contains a firewall.... there are three boxes here, the modem, one big one-port router and the switch. I think that "router" thing (doesn't look anything like my router at home!) has a lot of connectors on the back and i guess there's more in it than just a router.

Kind regards.....

Thanh

---

### Post by KeLa on 2010-02-16
Best thing to do now is to check that all access rights are in order on those shares and there is no access from internet to those shares.
Those files are distributed by some infected windows computer that scans network for accessible shares.

---

### Post by Thanh-BKK on 2010-02-16
Hi.

Nobody can access those shares without entering the username and password for the corresponding machine (all machines are single-user). 

And it also happens when the internet is offline, that was the last thing i tested - network on but leased line unplugged (share happens via workgroup/computer names, not based on IP). 

Best regards......

Thanh

---

### Post by amsterdamharu on 2010-02-16
To make sure what makes that file appear you have to take that computer offline for tests.

I can jump at 6:30 and conclude that me jumping makes the sun come up but that would be a bad assessment.

It is unlikely that binaries are infected. Make sure the file appears there when you access the share from it's own machine.
Is it created when you start samba service?
Maybe samba service creates the file when started.
Is it created when you access the share when the share is read only?
Maybe samba service creates the file.
Is it created when you access the share when the share is read write?
Maybe samba client creates the file.

Again it is unlikely the binaries put those files there, that would mean you found a virus in linux software. This cannot be called a bug since it looks like this is something that someone deliberately programmed samba to do.

If users have write permission to each others home dirs there might be bash script going around that puts the file there but then the file would not be created on a samba event would it?

Here is a thought, nautilus scripts can be installed in user home dir and can be event driven.
[http://library.gnome.org/users/user-guide/unstable/gosnautilus-444.html.en](http://library.gnome.org/users/user-guide/unstable/gosnautilus-444.html.en)
[http://library.gnome.org/users/user-guide/unstable/nautilus-extensions.html.en](http://library.gnome.org/users/user-guide/unstable/nautilus-extensions.html.en)
Scripts can be found in nautilus menu under file -> scripts
Or in the folder:
~/.gnome/nautilus-scripts or ~/.gnome2/nautilus(-scripts) or ~/.nautilus/scripts (they all have something called scripts

---

### Post by scottuss on 2010-02-18
Wow. Don't wanna sound like I'm going in circles here but lets look at the facts.

Files that were similar / identical to ones being created in the same way on another person's machine are appearing here. DC++ was to blame in the other case, it's very likely to be the same thing here. If not, look for other file sharing software. One clue is that it's creating .EXE files, so whatever the software is, it's likely that there's a popular version for Windows too.

It happens when the Internet is disconnected. Therefore we can conclude that it isn't something outside the network that is doing these things. It's an application, installed on one (it could be ANY) of the machines on the network. If it is a Linux machine, it is likely a file sharing application that is targetting a Windows machine (clearly the "threat" won't work because it's on a Linux machine)

This isn't really that difficult, if you go through everything you know and use deduction to eliminate all possible culprits.

---

### Post by Thanh-BKK on 2010-02-18
Hi.

The only thing i know is that i have a bunch of machines, all run Ubuntu Jaunty, NONE has DC++ or other file sharing applications installed (apart from Transmission however that is not being used) and all of them has each one shared folder to which all the others have access via Samba, access is read-write and a username and password for that specific machine has to be entered to access the share. 

The files are being created even without internet access (LAN only) and there is no Windows machine anywhere near.

I have given up on the issue and simply ignore those files now, deleting them when they get too many.

Best regards......

Thanh

---

### Post by scottuss on 2010-02-18
"The files are being created even without internet access (LAN only) and there is no Windows machine anywhere near."

But that's the point: clearly one of the Ubuntu machines IS creating the files, it's not that hard to believe. It's not malware (at least not malware that can affect Linux machines).

I don't see how Samba running on a Linux server would create these files. Especially .exe ones.

You absolutely *must* have something running on your machines that is attempting to target Windows hosts. Perhaps it isn't file sharing software, but something is not right. Are you using any Windows software in WINE on any of the desktops?

It's your network, but if I were your manager / employer or even employee, I certainly wouldn't be impressed if you ignored the problem and "just deleted the files" when their numbers grow.

---

### Post by Solethara on 2010-02-20
Well, we can be certain that some process is creating files. So you can try to kill processes one by one and check after that to see which process is creating those files. After that, you can remove whatever process was making those files. If you need that process for something else, you can try to reinstall it.

In other words, aim for "try and eliminate" technique for a solution, since understanding the problem itself is pretty hard.

---

### Post by Thanh-BKK on 2010-02-20
Hi.

Well i mentioned previously that none of the machines have Wine even installed. So that can be ruled out. 

The "problem" is present ever since the first of the machines started using shared folders, at the time there were still Windows machines so i thought it was from there however got suspicious as it continued even as Windows was eliminated from the office.

However this "stop processes one-by-one" would keep me occupied for weeks as there are a number of machines, it could be from any one of them and from any process running on any of them, they are in four rooms and i don't have the time available for such measure.

As i can't find a definite answer WITHOUT such time-consuming elimination trial i have to ignore the problem - after all it can't do any harm, it is just slightly annoying. 

Best regards.....

Thanh

---

### Post by scottuss on 2010-02-20
> **Thanh-BKK said:**
> Hi.

Well i mentioned previously that none of the machines have Wine even installed. So that can be ruled out. 

The "problem" is present ever since the first of the machines started using shared folders, at the time there were still Windows machines so i thought it was from there however got suspicious as it continued even as Windows was eliminated from the office.

However this "stop processes one-by-one" would keep me occupied for weeks as there are a number of machines, it could be from any one of them and from any process running on any of them, they are in four rooms and i don't have the time available for such measure.

As i can't find a definite answer WITHOUT such time-consuming elimination trial i have to ignore the problem - after all it can't do any harm, it is just slightly annoying. 

Best regards.....

Thanh

Fair enough. If you're going to bury your head in the sand, mark the thread as solved.

---

