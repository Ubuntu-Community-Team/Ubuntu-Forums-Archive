---
title: "SeamlessRDP in Ubuntu 9.10 Karmic"
date: 2010-03-11
forum: General Help
---

### Post by nicholas.alipaz on 2010-03-11
I have seen tons of tutorials about using seamlessrdp in older versions of Ubuntu to seamlessly pull up windows apps as if they were in Ubuntu.

I recently tried this in 9.10 to find that the remote login seems to work but it opens a full window and nothing I do will make the window float on top of the Ubuntu desktop like the screenshots I have seen on the net.

So my question is does anyone have this working in 9.10 and if so can you please share.

I use Ubuntu 9.10 64 with VMWare Workstation 7.0 (containing Windows XP SP3 Machine).

---

### Post by HermanAB on 2010-03-11
You need Cendio Seamless RDP:
[http://www.cendio.com/seamlessrdp/](http://www.cendio.com/seamlessrdp/)

---

### Post by nicholas.alipaz on 2010-03-11
Actually I already have seamlessrdp and that is why I titled this thread the way I did.

The command line "works" for logging in via seamlessrdp and rdesktop but it seems that the remote system never shows seamlessly.  I just get the big blue window.

Example:

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM> -u administrator -p password
```

This launches a fullscreen window of my vm and logs it in but it doesn't open the program and the window is fullscreen as mentioned.

---

### Post by RikoW on 2010-03-12
I did that a long time ago and I seem to remember that first to have to login to the vmware session normally and after you are logged in,  start the seamless rdp and take over the session.

Don't know, if that is still true.

Good luck,

             Riko

---

### Post by nicholas.alipaz on 2010-03-15
RikoW, yes I did do it the way you describe, but it does not open as a resized window after opening again.  I think it may not be working properly in 9.10 but I can't seem to confirm this.

I feel I am doing everything right since I can login via RDP but the programs I try to get it to launch do not open via seamlessrdp and the window is always fullsize.

I will say that if I use seamlessrdp to set the width and height of the remote window then it does get set properly.  It just doesn't listen to anything to do with the -A flag or the program to launch.

---

### Post by RikoW on 2010-03-15
Sorry that I can't help more. Maybe it has something to do with the fact you are trying to do that with a VM?! Shouldn't though. 

I do seamlessrdp with to a windows 2003 server and it works just as expected with resizing and everything.

Good luck,


          Riko

---

### Post by RikoW on 2010-03-17
Hi again,

it seems like an RDP session to the VM behaves differently then to a physical machine. A seamless RDP session to a desktop PC running XPSP3 works great, while I always get the desktop full screen when I try to do that with a VM (XPSP3) executing exactly the same command. That used to work in older versions of VMware. I'm now running Worskstation 7.0.

Cheers,
             Riko

---

### Post by nicholas.alipaz on 2010-03-19
Rikow, thanks for testing that out.  I now I know it isn't just me.  Odd that it used to work but doesn't anymore.  Seems like there would be a lot more people posting with this issue but I guess not.

Maybe someone will find a solution eventually.  If I find anything I will be sure to update this thread.

---

### Post by Brock Samson on 2010-05-05
Hi All,

just so you know, I am experiencing the same problem on 10.04.
I have a paravirtualised windows xp guest running with KVM and when I try to do a seamlessrdp session for say notpad, all I get is a huge blue window which covers both my screens! and notepad doesnt even load.

not sure what the problem is, rdesktop is the latest version and I got the seamlessrdp files from Cendio.

Any help is appreciated.

---

### Post by mlsquad on 2010-05-18
I'm having the same problem as well.  I can RDP into my Windows box just fine, but seamless RDP just gives me an RDP session that takes up both of my monitors and has no windows decorations.
I wonder if there is a regression in rdesktop 1.6.

---

### Post by mlsquad on 2010-05-18
[QUOTE=https://bugs.launchpad.net/ubuntu/+source/rdesktop/+bug/95088]Fast User Switching has to be on in order for SeamlessRDP to work.[/QUOTE]
[QUOTE=http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/fast_user_switching.mspx?mfr=true]Fast User Switching is not available on computers that are members of a network domain.[/QUOTE]
[http://www.microsoft.com/windowsxp/using/accessibility/fastuserswitching.mspx](http://www.microsoft.com/windowsxp/using/accessibility/fastuserswitching.mspx)

Unfortunately, my computer is part of a network domain, so seamless mode is not available to me. :(

---

### Post by sickrandir on 2010-10-13
I have this same problem on Ubuntu Lucid 10.04.
I tried to make SeamlessRDP work both with a Windows XP pro SP3 guest on virtualbox and with the same system on kvm. I always get the regular rdp connection with the whole desktop and no program starting. 
For example, if I connect with the command:
```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad" 192.168.1.120:3389 -u username -p pass
```
Notepad never starts and I have always get the complete desktop.
It's not a matter of "Fast user switching" in the windows guest because I have that activated and my guest is not a part of a network domain.
Any idea of what the problem might be?

---

### Post by Wiredfixer on 2010-10-25
Well, i have the same problem, i just want to execute one application in my Ubuntu 10.04, but i have only a "window" with my windows session, its fine, but for more "User Friendly" want only the App i need In my Ubuntu Desktop.

 I create a Launcher Icon on my desktop, with all the parameters, but only i have a full Windows Desktop..

 I've read all the thread and i see about my problem, the Windows PC are connected to a Domain an so the Ubuntu Desktop is (with Likewise Open 6)..
 
 Why is this it? There are another alternatives to make the appz work seamless like in citrix or like in a normal PC without domain controller?

 And Another Question, can i have seamlessrdp installed on a windows 2003 server to make connections from 10 or more Clients in this way?

 Im only Need a W2k3 Licence for do this? The app i want to run its an VB Application and i cant use in WINE because is buggy..

 Any recomendations?

---

### Post by Wiredfixer on 2010-10-26
Well...

I try to use this in a Desktop with Win Pro SP3, display a full desktop...

Next, i try to use in a W2k3 server and Works Like a Charm.

My Recomendation is to use in a Windows Server, is more prepared for this enviroments :D

My next test is with the printers, maybe i need to use printer on some appz, but i need to print locally, somebody knows how to do this?

---

