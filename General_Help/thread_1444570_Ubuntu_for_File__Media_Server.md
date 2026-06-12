---
title: "? Ubuntu for File / Media Server ?"
date: 2010-04-01
forum: General Help
---

### Post by AP0ll0UK on 2010-04-01
Hello All

I'm currently exploring options for what I should do with my server. It is of the following spec and runs Windows 7 32-Bit:-

ABit AB9 Pro Motherboard
Intel Core 2 Duo E6600 2.4Ghz
1GB Ram [the other GB died but haven't noticed the difference]
ATI X1900XT 512MB
1TB storage split across 4 disks
Windows and Apps installed on 34GB Western Digital Raptor
Sat Card - TT-Budget S1100
iPod 5th Gen Connected
Connected to 40" Samsung LCD
Hard wired into a wireless router
No Keyboard & Mouse connected


It is mainly used for watching movies [normal divx and 1080p HD stuff in PowerDVD], occasional web browsing [Firefox], playing music through an amp [Windows Media Player], burning CDs/DVDs [Nero], storage / file server to my wireless laptops. I also have Windows Media Center setup but I don't really use it. The Sat card picks up Freeview and a few other free Sky channels but because it's faffy I haven't bothered with it much. I don't have a requirement to record live Tv as I don't watch enough to Tv. 

As I mentioned its currently running Windows 7 and has been since the beta was available.  However, the build is becoming a bit troublesome and it needs a rebuild as Windows boxes do from time to time, but before I do I'm looking at Ubuntu as a replacement. I have a laptop also running Windows 7 which I use for web browsing and watching movies in the bedroom when connected to a seperate LCD. My girlfriend also has a Windows XP laptop and she backs some of her work up to this box.

I like to watch movies on the PC [which I control through VNC] and then remote desktop to the machine in the background and kick off a few downloads.

Now I have been here before, I last tried a build of Ubuntu on a Dell X300 laptop and had trouble with the wireless drivers so it was a non-starter but wireless shouldn't be a problem in this instance because the PC is hard wired into my router.

Before that I've tried one of these 'convert yourself to Linux' things using Mandrake, before that I tried Suse and before that I ran a ClarkConnect box as a file server / firewall. I've not had much success though in terms of getting the boxes setup the way 'I' want them, I've had boxes up and running but when it comes to doing some of my daily tasks work I just want to get on with them. Again in this instance it shouldn't be too much of an issue as I have my laptop for that stuff, but the media element is important because my girlfriend and my mates and I watch a lot of movies. 

So, the question looms - can the latest version of Ubuntu give an equivalent of what I've already got, plus a few new bells and whistles?

In an ideal world I would like the main interactive session on my Tv when I logon to default to some kind of media center type interface, movies and music is essential, Freeview isn't but would be nice for the new HD channels which have just launched in the UK. It is isn't currently controlled via a remote but I will be picking one up next payday although I haven't looked into that yet.

Whilst the media center is displayed on the Tv, I'd still like to be able to remote desktop into it from my Windows 7 laptop and be able to perform tasks.

Being able to setup some fairly generic shares for files, movies and music for multiple users [i.e. my girlfirnd and me] easily is important, I don't want to spend ages looking for a way to do it, via a web interface would be nice. That doesn't mean that I'm incapable of reading docs and digging around forums, it just means that if I get frustrated from the outset then I know I'll give it up as a bad job in a fairly short space of time.

I also need to be able to burn CDs/DVDs as I backup everything my son has as he is only young and discs don't last long. This would need to be fairly straight forward for someone who is used to the Windows GUI rather than a Ubuntu / Linux GUI, and produce similar results to that of Nero and I would much prefer to do this machine as opposed to my laptop.

Being able to download new tracks to my iPod is also essential as I'd go mad without it.

I'm looking through some Ubuntu videos on Youtube at the moment to get and idea of what the user exeperience is like, there seems to be quite a lot of people showing of some nice looking desktops and a some with nice looking widgets and with live / animated desktops. In particular one with a fish tank which would probably look lovely on my Tv, is all this kind of thing easy to come by for free?

I may just pull down the latest Ubuntu Live CD, fire it up and give it a whirl and see how it runs. I'm just curious what some of you hardcore Ubuntu users have to say on the matter as no doubt some of you will be running similar if not far more complex systems. I may also visit a 64-bit version of Ubuntu providing it is going to have much impact on drivers and apps as is common in the Microsoft world, hence why I'm still on x86 versions.

Thanks.

AP0ll0UK

---

### Post by Chesamo on 2010-04-01
> **AP0ll0UK said:**
> Whilst the media center is displayed on the Tv, I'd still like to be able to remote desktop into it from my Windows 7 laptop and be able to perform tasks.
Look into VNC; it comes installed on the default Ubuntu install.
> **AP0ll0UK said:**
> Being able to setup some fairly generic shares for files, movies and music for multiple users [i.e. my girlfirnd and me] easily is important, I don't want to spend ages looking for a way to do it, via a web interface would be nice. That doesn't mean that I'm incapable of reading docs and digging around forums, it just means that if I get frustrated from the outset then I know I'll give it up as a bad job in a fairly short space of time.
FTP and Apache?
> **AP0ll0UK said:**
> I also need to be able to burn CDs/DVDs as I backup everything my son has as he is only young and discs don't last long. This would need to be fairly straight forward for someone who is used to the Windows GUI rather than a Ubuntu / Linux GUI, and produce similar results to that of Nero and I would much prefer to do this machine as opposed to my laptop.
Ubuntu comes with Brasero disc burner preinstalled. IMHO superior to Nero anyway.
> **AP0ll0UK said:**
> Being able to download new tracks to my iPod is also essential as I'd go mad without it.
This is iffy. Make sure it's supported under Rhythmbox, AmaroK, Songbird, or Totem.
> **AP0ll0UK said:**
> I'm looking through some Ubuntu videos on Youtube at the moment to get and idea of what the user exeperience is like, there seems to be quite a lot of people showing of some nice looking desktops and a some with nice looking widgets and with live / animated desktops. In particular one with a fish tank which would probably look lovely on my Tv, is all this kind of thing easy to come by for free?
Yup :)
> **AP0ll0UK said:**
> Thanks.
You're very welcome.

---

### Post by AP0ll0UK on 2010-04-01
Thanks for the speedy reply and also for your thoughts on the various items :D

I'll do some digging on the apps you suggested, have a bit of a read and see what they look like.

Do you know much about the media center side of things please?

---

### Post by moetunes on 2010-04-01
I use a pentium3 800mhz as my home multimedia/file server - using nfs as a way to mount the files locally the system is so undertaxed I'm working on downgrading to the pentium2 266mhz system I have sitting gathering dust. Doesn't seem to matter the codec of the vid I'm watching - the system never stretches its' legs at all. I don't have windows in my home so everything is smooth and light on the network side of things. I'm more than impressed with how it all worked out on the lan :)

---

### Post by AP0ll0UK on 2010-04-01
Three things from what you've said there moetunes:-

1) What do you use as your media center app? Is there a generic one which comes with Ubuntu as part of a vanilla install, or do you use a specific app?

2) Do you play a lot of HD stuff? I'm talking 1080p HD movies running in full 1920x1080?

3) LAN Traffic, one thing that really annoys me about Windows file transfers between my wired server and wireless laptops is that I seem to get roughly a 2MB/s transfer rate despite using wireless G kit. Even when I was using a Linksys wireless N router [which recently died but will soon be replaced], I was still seeing very similar speeds. Do you see higher transfer rates using Ubuntu across all your machines?

Thanks again people :D

---

### Post by moetunes on 2010-04-01
> 1) What do you use as your media center app? Is there a generic one which comes with Ubuntu as part of a vanilla install, or do you use a specific app?

I use fluxbox and have set the files in the nfs mount to show in the menu and open with svlc - no media center app needed at all.
>  2) Do you play a lot of HD stuff? I'm talking 1080p HD movies running in full 1920x1080?
I play recorded hd stuff and it works fine. Using ssh and top I see the file server isn't working much at all - but I'm wired not wireless and never have lan speed issues.

---

### Post by AP0ll0UK on 2010-04-01
> I use fluxbox and have set the files in the nfs mount to show in the menu and open with svlc - no media center app needed at all.

I was thinking something a little more automated for the Tv display with more of a media center look and feel to it, a library of movies and music with cover art. Something a slick looking like Windows Media Center, or Media Portal which looks a bit naff by default but looks very sexy with a nice skin, plus it displays cover art, movie descriptions, that kind of stuff.

> 
I play recorded hd stuff and it works fine. Using ssh and top I see the file server isn't working much at all - but I'm wired not wireless and never have lan speed issues.

I guess this is one area where Ubuntu is going to seriously excel over its Microsoft counterpart - resources! If your box is showing 1080p movies on a box of such a low spec then I have to admit that is pretty impressive :D

---

### Post by moetunes on 2010-04-01
The pent3 is headless - it just serves the files through nfs to any other comp on the lan. Serving the files through nfs uses no resources on the headless server. Sorry I wasn't more clear on that. :)

---

### Post by Chesamo on 2010-04-01
Take a look at Moovida:

[http://www.moovida.com/](http://www.moovida.com/)

---

### Post by AP0ll0UK on 2010-04-02
> **Chesamo said:**
> Take a look at Moovida:

[http://www.moovida.com/](http://www.moovida.com/)

I've had a look aroun for this and watched a couple of video's on YouTube and I must say I'm very impressed so thank you for the suggestion.

I've also come across LinuxMCE which seems to be more advanced in terms of functionality, both definately seem well worth further investigation.

Well I've just burnt my Ubuntu iso so I'm going to dig out a keyboard for the box and get it installing!

Thanks again :D

---

