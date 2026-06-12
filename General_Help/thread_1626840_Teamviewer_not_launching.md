---
title: "Teamviewer not launching"
date: 2010-11-20
forum: General Help
---

### Post by andy128 on 2010-11-20
Ubuntu 10.04  - Installed Teamviewer from Deb package.  Worked fine.  Went to connect to another machine and it said"  You are using an older version would you like to download the newer version"  I did and it shut down Teamviewer and then downloaded one to the desktop but no installation.

I uninstalled everything and started over.

Now each time I install- Teamviewer will install and appear in Applications>Internet but will not launch.  When I look at the process list it is there but listed as Zombie.  I kill the process and try again with no luck.

Any suggestions?

---

### Post by got2get on 2010-11-21
been havin` the same problem

---

### Post by andy128 on 2010-11-21
I have removed it, re-installed it.  I have gotten every bit of it I could find and deleted/removed it.

I found a remnant (even though I have removed Wine and Teamviewer) in Applications>Wine>Programs>Teamviewer5 and then am presented with License, Teamviewer5, Uninstall Teamviewer5.  Even running the Uninstall- it does not remove it.

ugh........have to call their Tech Support tomorrow if no one can assist.

---

### Post by got2get on 2010-11-21
i already reported the problem to them
but i found a temporary fix
i installed the older 4.x version on both computers and it works pretty good
i`ll edit this post if they give me a better fix

---

### Post by andy128 on 2010-11-21
In the end.........after a couple hours trying this and that- I re-installed Ubuntu and set up everything from scratch (1/2 hour).  

Now it is working flawlessly.

Cheers-

---

### Post by lvieirabr on 2010-11-23
Hi,
I have the same problem. I reisntalled Teamviewer several times. Nada.
I have wine and installed teamviewer 6 (beta) on that and it works. 
But TV 5 deb on Ubuntu no.
May be another solution but reinstalling Ubuntu itself.
Any help?

---

### Post by neic on 2010-11-26
I experience the exact same problem.

---

### Post by wyxa on 2010-11-28
Hello guys!
My TeamViewer is not running under root account (I have activated it).
On the normal user account seems to be all right.
Any gurus can help on that?

When I try to start the TeamViewer, it's not even appearing in the processes list in System Monitor.

---

### Post by piquat on 2010-11-29
10.04 on my Torrent machine and I ran into this Saturday.  Start app, nothing happens.

I tried a few things to no avail and nothing happened until I "reinstalled" it.  I didn't do an uninstall, just a reinstall in Synaptic.  After a reboot it started working.

No such horsing around in Mint 10, it just worked.

---

### Post by wyxa on 2010-12-01
> **wyxa said:**
> Hello guys!
My TeamViewer is not running under root account (I have activated it).
On the normal user account seems to be all right.
Any gurus can help on that?

When I try to start the TeamViewer, it's not even appearing in the processes list in System Monitor.
Tried to execute it in terminal and got the message:
"TeamViewer must not be executed as root!"

Pity, this is a limitation. Is there any workaround?

---

### Post by buck0182 on 2010-12-02
I ran into the same problem and I did find a solution for getting teamviewer to open agian.  
1 Go to synaptic and remove teamviewer

2.  Goto Places>Home Folder

3. Click View>Show Hidden Files

4. Locate and remove the hidden folder ".teamviewer"

Then re-install and it should open up again.

I have yet to find a way to get teamviewer to run version 6 however, every time I install it, it starts back up on version 5.0.8888

I am still pretty novice at this myself so hope this helps.  If not, I really don't know where to go from here or how to get version 6 installed.

---

### Post by endof on 2010-12-17
/usr/bin/teamviewer6  open this folder gedit or text editor

if [ $userid = 0 ]
then
        echo TeamViewer must not be executed as root!
        exit 1
fi

remove the comple this code  and  run root

---

### Post by joelang1699 on 2011-01-26
I have the same issue on a few Ubuntu systems. It starts once or twice and then simply refuses to launch anymore. I have raised a ticket with TV. I'll post their response if I get one.


Highly annoying I must say

---

### Post by joelang1699 on 2011-02-14
Just got this from the Guys at Teamviewer. Works perfectly

Dear Joe,

it seems that your graphics board or driver does not support the XF86VidModeExtension.
As a workaround, you can disable this extension in Wine. Unfortunately you need to do this by hand.
Open the registry file ~/.teamviewer/6/user.reg in an editor of your choice.
Then look if a section named [Software\\\\Wine\\\\X11 Driver] exists.
If not, create it like this: (it needs to have a number)
 [Software\\\\Wine\\\\X11 Driver] 1292497617

Below that line, add this entry:
"UseXVidMode"="N"

Save the file and start TeamViewer again. If you have any further questions about this, please don't hesitate to get back to us.

Mit freundlichen Grüßen / Best regards

Daniel Stiefelmaier

---

