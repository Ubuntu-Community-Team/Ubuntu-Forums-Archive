---
title: "Wine and Cisco Apps and Tools"
date: 2010-01-02
forum: General Help
---

### Post by dogturd on 2010-01-02
Hi,

I've done some extensive searching and also on the Wine database to no avail. I would like to run the following within Wine as I don't really see the benefit in dual booting for a few MS based apps. Has anyone ever tried running these apps within Wine?

1, Cisco SDM (Secure Device Manager)for configuring Cisco Routers. And yes before the flames start,I prefer and always you CLI but when.But SDM is quite handy in some situations :)Maybe as issue with the Java client as well.

2, Self Test Software (Not brain dumps) have an installable exam prep software for testing out your Cisco Knowledge.

3, Cisco TFTP client for uploading/downloading IOS and running configs.

Gonna go for broke and try it out for myself. I am running 9.10 on an Acer 5738. I will install Wine tonight and post the results. Before I start has anyone have any good tips please?

Thanks

---

### Post by dogturd on 2010-01-02
Well mixed results.

Downloaded the Windows Java client and installed via Wine, then installed the SDM via Wine. Ran the application and I get the usual Cisco SDM login prompt for an IP. I will test against a router on Monday at work to see if the application fully works and will pick up the IE install within wine, as SDM and latest version of fireforx has issues.

Cisco TFTP client installed but will not run, saying "failed to initialize TFTP server". Not sure if I need to have TFTP running as port defitinely not running with Ubuntu - so I guess this won't work until the port is open. Not sure how to do this within Ubuntu (as linux still new to me).

Self Test Software - managed to install the test engine and exam module for Cisco - but it won't run at all! Going to re-install and try again.

So mixed results. SDM appears to be working which is a result but I won't know properly until Monday. TFTP would be nice but I may have to resort to setting this up within Ubuntu instead. Exam simulator is a pain as if I can't get this to work then I will still need Windos to run this app for my studying.

Footnote: I don't want to dual boot as I have used Windows since 1991 and to say I have had enough of crappy M$ is an understatement. I have been running Ubuntu for a while and I am fully hooked on it!

Further on.....
I think the MSVBVM60.DLL is missing causing the exam engine to fail. How do I add this DLL to the wine installation?

Nope hit a brick wall. Copied the DLL to the System32 folder within Wine, program starts to run all looks good then crashes. Looks like I'm still going to be stuck with sh*tty windows for a while longer :(

---

### Post by dogturd on 2010-01-03
There may be a light at the end of the tunnel. Looks like my googling is getting sloppy these days. One large cup of coffee and google and I stumbled across this...

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=7411](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7411)
Apparantely he has Self Test Software working with Wine.

[http://3tar.de/welcome.html?t=24](http://3tar.de/welcome.html?t=24)
To download the scripts.

I followed Christian's instructions and when I run start.sh I get a terminal pop up with no syntax error or success message and thats about it!

I've emailed Christian to see if he can help out.. Fingers crossed

---

### Post by dogturd on 2010-01-03
Sort of cheated. I decided to install VirtualBox OSE and have averything running on a virtual xp. SDM, Self Test and TFTP all working.

I have also created a share on Ubuntu for my TFTP Cisco IOS dumps, mapped the drive within virutal XP and everything works out ok :)

---

### Post by running_rabbit07 on 2010-01-03
Yeah, I have to run Windows be it standalone or in VBox just to run Cisco PacketTracer. It is too bad that Cisco doesn't write programs for Linux.

---

