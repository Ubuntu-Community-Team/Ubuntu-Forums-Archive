---
title: "Which Remote Desktop (RDP) Client?"
date: 2012-08-20
forum: General Help
---

### Post by Jack Waugh on 2012-08-20
I want to look at my Microsoft Windows XP box (so I can test web sites with Microsoft Internet Exploder 8).  I want to do this from one of my boxes that is running Lubuntu (which is no different from Ubuntu in this regard, I'm sure).  When I look in Synaptic at the packages that seem to address this, there seem to be several alternatives.  What package have you had success with?

---

### Post by ferrisxb9r on 2012-08-21
I've had GREAT success using Remmina, it provided all the options I required for corporate users to connect to stuff via RDP.

---

### Post by d4m1r on 2012-08-21
Popular options:

1) Remmina
2) Remote Desktop Viewer
3)KVnc

Unfortunately, all 3 above are heavily bugged when connecting to a Windows XP machine from Ubuntu so I hope you have better luck....

---

### Post by SteveDee on 2012-08-22
> **Jack Waugh said:**
> ...so I can test web sites with Microsoft Internet Exploder 8...

You may also be interested in this website tester: [http://browsershots.org/](http://browsershots.org/)

---

### Post by dcstar on 2012-08-23
> **d4m1r said:**
> Popular options:

1) Remmina
2) Remote Desktop Viewer
3)KVnc
[B]
Unfortunately, all 3 above are heavily bugged when connecting to a Windows XP machine[/B] from Ubuntu so I hope you have better luck....

Rubbish.

I regularly use Remmina to connect to XP, Vista, Windows 7, Server 2003, Server 2008 and Server 2010 machines.

I do this a part of being an IT professional, which is obviously not the situation that a lot of people posting their "opinions" are in.

---

### Post by SteveDee on 2012-08-23
> **dcstar said:**
> Rubbish....I regularly use Remmina to connect to XP...I do this a part of being an IT professional....

I also get paid ridiculus amounts to play 3 days a week on Windows 2003/xp & 2008/7, but I'd draw the line at anyone calling me "professional".

I've setup 60-70 thin clients running Lubuntu and using rdesktop to provide a Windows desktop (RDP) experience from a Win2008 server. They seem to run without problem, although currently without RemoteFX.

Remmina is also a great app and {in my experience} very stable.

But you can have bad experiences working on any computer stuff, and if you never find the reason, it can colour your view on an app or an operating system, when maybe the blame lies somewhere else.

---

### Post by d4m1r on 2012-08-23
> **dcstar said:**
> Rubbish.

I regularly use Remmina to connect to XP, Vista, Windows 7, Server 2003, Server 2008 and Server 2010 machines.

I do this a part of being an IT professional, which is obviously not the situation that a lot of people posting their "opinions" are in.

Then you are using some simple setup. I use a very advanced one and have reported several error codes to the Remmina team who have confirmed the issue so....

Try running a more advanced setup like myself (RDP fullscreen on one workspace, switching workspaces, connecting over VPNc, etc). See if your clipboard works or even if you can keep a steady connection for 5-10 minutes. I will bet you you can't. I hope the OP doesn't have to do any of the above as it just isn't currently possible to do so Ubuntu 12.04 LTS -> Windows XP.....

---

### Post by Jack Waugh on 2012-08-25
Thank you, everyone, for the responses to date.

---

### Post by jim_deadlock on 2012-08-25
I've tried several of the usual RDP clients but I've found [Teamviewer]("http://www.teamviewer.com/en/index.aspx") to be by far the easiest to use, just install and go, and it's cross-platform. You can switch off the password prompt on the server end if necessary.

---

### Post by Templerun on 2012-08-25
I am great fan of TeamViewer too, try XRDP in Ubuntu it will never let you down. Installation is quite simple ...

> sudo apt-[get]("http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=get&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99") install xrdp

after this simply connect using your favorite remote desk program.

---

### Post by dcstar on 2012-09-23
The current 12.04 version of Remmina has various nagging issues that some people can cope with, but some can't so this Launchpad bug has instructions on how to use the older Remmina version:

[https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522](https://bugs.launchpad.net/ubuntu/+source/remmina/+bug/937522)

---

### Post by HermanAB on 2012-09-23
I've used rdesktop for years.

---

### Post by Jack Waugh on 2012-09-23
Thanks for all the contributions to this thread.  Eventually I will try one of the tools mentioned.

---

### Post by Jack Waugh on 2013-08-30
Besides Internet Exploder, another thing I have to test on Microsoft Windows is 'gpg' (Gnu Privacy Guard), because some of the people with whom I need to communicate, don't run Linux.  So, browser testing is not the sole motivation here.

Thanks for all replies to date.

---

### Post by Jack Waugh on 2013-08-30
When I tell my Windoze XP system that I want Remote Assistance, it wants to create an "invitation" file that it says I have to give to my assistant.  But 'rdesktop' doesn't seem to have an input for that file.

---

### Post by Jack Waugh on 2013-08-30
"You cannot use Remote Desktop Connection to connect to computers running Windows XP Home Edition."  Also spracht Microsoft [http://windows.microsoft.com/en-us/windows/connect-using-remote-desktop-connection#connect-using-remote-desktop-connection=windows-vista](http://windows.microsoft.com/en-us/windows/connect-using-remote-desktop-connection#connect-using-remote-desktop-connection=windows-vista)

---

