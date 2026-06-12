---
title: "Thinking about using ubuntu, would like help on how to do some things first!"
date: 2010-08-25
forum: General Help
---

### Post by ICANSEEYOU7687 on 2010-08-25
I guess i should post my setup first.

Currently im using...
amd Sempron 1.9ghz, with 1 gig of DDR333 memory.  I know it sounds crappy, but it does what it needs to do for file pushing.  I run it as a media server, and FTP server.

Currently, for the media server, I just map the drive to my laptop and push it out to my hdtv via HDMI through the network drive.

Now I am going to upgrade the server to a Phenom II x2/x4 (if i can get the cores unlocked) 3.0 ghz, with 4 gigs of DDR1333 memory, and the ATI HD 4200 IGP should be able to handle 1080p just fine.

AS FAR AS Ubuntu... my friend recommended it to me.  Currently while in college I am working at an engineering company's helpdesk, and I want to learn more linux commands and get more familiar with the system.

So here are the thigns I wanted to be able to do
**Media Server** - Up to 1080p VLC maybe?
**sFTP/FTP** -  Ubuntu comes with OpenSSH already doesnt it?
**RDP/VNC** - VNC is easy... but ive gotten so use to remote desktop.  I have seen post mentioning linux does have RDP clients but are any stable?[B]
Mapping Network drive to windows - [/B]should be pretty straight forward, never done it with linux though.
**Orb - **I use this for live streaming, but after googling ubuntu and 1080p it seems that there are some good options for video streaming

I would love any suggestions, pointers.  I actually borrowed mandriva from a buddy and put it onto a partition of my laptop but I dont use it much.  But thanks for listening!  It seems with a little know-how and reading everything should be doable,  but I would really appreciate some suggestions and advice!

---

### Post by DavidOfLondon on 2010-08-25
My advice to you is the advice I wish I'd received - 

Do Not Switch To Ubuntu directly. Install it alongside your current OS (it'll run alongside windows just fine, depending on your specs, that is). 

The problem with the jump to Linux is discovering the colossal number of programs that simply won't work with the OS using Linux. I deleted a faulty install of Windows XP which kept crashing but I wish now that I'd simply installed Ubuntu 10.04 ALONGSIDE it as I've lost all my windows capability on this laptop.

If you've never used Linux terminals for anything in-depth be warned that it can be very different to what you're used to - the same logic as is used in DOS is there but hundreds of command structures are totally different.

That said...

Ubuntu has never crashed on me, not even once. The desktop loads up in under 20 seconds for me, even on a 4 year old laptop. You can customize every aspect of your desktop - ( YouTube "ubuntu 3d cube" for example). The package manager is very user-friendly. 

And of course, Linux OS PCs stand the smallest possible chance of virus attack - the file structures are so segregated that worms etc just aren't capable of going on a windows-esque rampage because the user (even if he's an admin) doesn't work out of the root folder unless he forces the OS to let him.

I can't answer your other technical questions but I can say your best option is to go to the Ubuntu website, download and burn the ISO image of the operating system onto a CD (don't use the USB option unless you have to) and use the "Try It First" option (all instructions on website) which will allow you to run the OS from boot up from the CD only with pretty much full functionallity. That will allow you to look into your tech options re your above usage.

It's brilliant, it's free, and if you ever have a problem the Linux community will answer it for you.

I vote Yes to giving it a try!

Best,

David.

---

### Post by Xanko on 2010-08-26
You might be able to leave the 'Media/File Server' as is, I use a Intel P4 2.26 GHZ/1gig DDR system as my print/file/media/desktop system and it runs decently not too slow (I really look forward to a new Intel Core I7 system with all the upgrades though.... (at which point this older system will be dedicated file/backup/print server) This is the same machine that ran slow as molasses with Windows 2000 so I'm sure you'll be pleasantly surprised with how much more efficient Linux is.

Not sure if OpenSSH is pre-installed with Ubuntu but you can easily find it in was is called the repository which is a large database of programs you can install. Cool thing about the repository is that if there is any files a program is dependent on they will be installed as needed. Also all files are kept up to date with the repository constantly checking for updates. BASICALLY, its easy to install if not pre-installed.

Never looked into RDP however I have used VNC with my personal network and it seems to work well, there is different client and server software you can pickup and it works differently from Windows. With VNC in linux you can choose to view the main display output that is being sent to the monitor or you can setup a new 'display' as they are called and use a GUI that has no monitor attached to it. Kinda cool if you wanted to have a bunch of virtual displays setup off one computer. One issue I ran into was the speed of VNC which is apparently tied to how fast the system can READ the memory of your video card (apparently NVidia cards can do this faster) so definitely look into this before purchasing hardware.

Mapping network drives between Windows and Linux is done using SAMBA....its pretty easy to setup but has a TON of features if you want to try them out. I can browse all shares on my network from any computer (linux, windows, or my android phone)

Not sure what ORB is but on my network I have the laptop hooked to 1080p HDTV, the laptop just pulls file across the network via shares to display on TV. It would probably be a little more complicated if I was trying to pull files from the other side of my firewall but im sure it could be done... (SSH tunneling or VPN)

All that said I used to be a Microsoft Junkie.....love Windows, Outlook, Exchange, etc. My transition to Ubuntu started with a 4 year old dell laptop that got a new lease on life with linux...the machine just felt faster. Now all my computers use linux and I use VM's or WINE for the few windows programs I still use (FullTiltPoker). I might need to go back to Windows to run some racing simulators here in the near future but that will really be a bare bones installation for gaming. Everything else I would rather do in Ubuntu.

---

### Post by ICANSEEYOU7687 on 2010-08-26
Thanks for the replies.

For the record ORB is media streaming software.  You host a server and then go through a web page to easily stream video.  But like I said setting up streaming video in linux seems like it would be fairly easy.

All my hardware is already bought.  Currently I have my router and windows Server 2008 set up so that I can remote desktop to it from my android Cell phone, which I actually use a lot.  I really love RDP, but im sure I could get use to VNC if need be.

This is more of a project to help get me use to linux, I really want to be more proficient using a terminal

---

### Post by silverglade00 on 2010-08-26
There are quite a few programs for RDP. My favorite is Gnome-RDP, which lets you run RDP, VNC, or SSH sessions. It keeps a menu of all your computers and you just click on the computer name and the session fires up. I use it all day long at work and I miss it on other Linux distributions when they don't have it.

---

### Post by Xanko on 2010-08-26
what are the advantages of RDP over VNC???

any what software have you found for linux as opposed to using ORB. I have tons of media which I would like to access when I am not at home.

---

### Post by silverglade00 on 2010-08-26
> **Xanko said:**
> what are the advantages of RDP over VNC???

Windows has RDP builtin from XP on. You have to install a VNC server to use that, but VNC always seemed to be quicker to me.

---

### Post by ICANSEEYOU7687 on 2010-08-26
Well, RDP is actually faster then VNC, although in most cases only by a little bit. Instead of polling the entire screen and mimicking the server screen, it more or less just send information about a certain area, size and color.

But with the VNC Hook drive and network speeds now-a-days they are probably pretty much negligible. 

I did find a program called xrdp, which might work.  But I think VNC would just be something that I would need to get use it.

I have a mandriva paritition on my laptop I have been fiddling with.  But I really cant wait for my memory to get here so I can put ubuntu on this server im making! wooo

---

