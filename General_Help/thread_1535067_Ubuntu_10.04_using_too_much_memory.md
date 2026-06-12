---
title: "Ubuntu 10.04 using too much memory"
date: 2010-07-20
forum: General Help
---

### Post by KingNeil on 2010-07-20
I'm running 10.04 on a machine with 512 MB of RAM and a 3.2Ghz processor. Without any programs open, memory usage is around 350 out of 500 MB, or, around 70% of total memory.

I was previously running 9.04, but upgraded to get the long term support. Although I don't have it installed now, and didn't write it down, I'm sure 9.04 used much less memory, and it certainly felt a lot faster when opening and using applications.

Is it normal for Ubuntu 10.04 to be using this much memory, and if so, what are some things I can do to reduce memory consumption?

Reading Wikipedia, [it says]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#System_requirements") Ubuntu only uses 128 MB of RAM. 

By the way, here is a screenshot:

[http://i.imgur.com/nrAQJ.png](http://i.imgur.com/nrAQJ.png)

---

### Post by valbaca on 2010-07-20
The **minimum** **SERVER** requirements is 128 MB. You are not running a server.
The **minimum DESKTOP** requirement is 512 MB.
Neither of those imply that is all Ubuntu will use.
 
If you are using a system with lower specs, Xubuntu is recommended.

---

### Post by mike555 on 2010-07-20
You can uninstall things you don't use , like maybe Ubuntu-one, etc ...... also shut off the start-up of things you don't use ,like bluetooth, ubuntu-one, etc. ...... I got mine down to this ;

[IMG]http://i40.tinypic.com/14c402e.jpg[/IMG]

---

### Post by KingNeil on 2010-07-20
On my VirtualBox on my other computer, it uses only 124MB, or even as low as 90MB. 

I wonder if that's because Windows already does some of the work, above the VirtualBox layer.

If anyone has Ubuntu 10.04 now, would it be possible to close all your programs and check how much it's using? Or, if anyone happens to know what it should look like for a new install.

I just installed this.

[quote=mike555]
I got mine down to this ;
[/quote]

How much memory did yours use before you removed the stuff, and what exactly did you remove?

---

### Post by zer2 on 2010-07-20
Good to know that I'm not alone and  other people have similar problems to mine. I just hope you'll manage to solve the problem.

 In my case it's even worse cause it seems to use more CPU power than Vista. And this is beyond my imagination. Maybe someone can help me with it [http://ubuntuforums.org/showthread.php?t=1535007](http://ubuntuforums.org/showthread.php?t=1535007)

---

### Post by mike555 on 2010-07-20
Uninstalled ; Ubuntu-one ,Evolution , indicator-me, empathy , all mono stuff , gwibber, bluetooth, britty , computer janitor, e-speak, and probably some I forgot ...

 of course doing this I lost a few things , so installed ;Thunderbird, pigeon, mirage, shot well , etc.

---

### Post by KingNeil on 2010-07-20
> **mike555 said:**
> Uninstalled ; Ubuntu-one ,Evolution , indicator-me, empathy , all mono stuff , gwibber, bluetooth, britty , computer janitor, e-speak, and probably some I forgot ...

 of course doing this I lost a few things , so installed ;Thunderbird, pigeon, mirage, shot well , etc.

What is "all mono stuff"?

Also, what was your memory before you removed all this stuff?

It's just... the stuff you've listed, as far as I know, doesn't run all the time, so there's no reason it would eat your memory unless it's open.

---

### Post by Rubi1200 on 2010-07-20
If there are processes using too much memory and CPU you can check by running the following command in the terminal:

```
top
```

This

```
initctl list
```

will show you what is running at startup.

---

### Post by nmaster on 2010-07-20
i say this to people a lot but if you really want a low memory footprint, you should start with the minimal install (getISO from : [http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=minimal%20install&as_qdr=all&lang=en#870](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=minimal%20install&as_qdr=all&lang=en#870)) and then build the desktop up from there.  this is a pretty good guide to help you get started: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

i don't use it regularly, but i think LXDE looks pretty nice too.  i have debian+LXDE running on an old 800MHz PIII, 128MB desktop i found and its pretty slick.

---

### Post by KingNeil on 2010-07-20
> **Rubi1200 said:**
> If there are processes using too much memory

Well, there really doesn't seem to many processes hogging memory.

Screenshot:

[IMG]http://i.imgur.com/h0CMN.png[/IMG]

[IMG]http://i.imgur.com/KbhC4.png[/IMG]

I calculate the total memory of these processes to be 30.5748MB.. So... nothing really. I want to know where all the other 100s of MBs are coming from..

[quote=neal.m.master]if you really want a low memory footprint, you should start with the minimal install[/quote]

Yeah, I've seen the guide on this, and it looks interesting. It's just, 9.04 was running so well as a full install. I'm trying to see what the major difference in memory has been between 9.04 and 10.04.

If my processes calculations are correct, I guess the only other memory usage comes from services. Is that right?

---

### Post by techunit on 2010-07-20
I am constantly using around 512MB of ram on my 64bit install of lucid... But seeing that I have 4GBs to pull on I don't see a problem... for you I can though.... Disabling compiz should give you around 30MBs back (change system appearence)... Firefox can use up to 80MBs so try chromium...

---

### Post by nmaster on 2010-07-20
instead of using the system monitor, try using top.  when in top hit 'M'.  this will sort the processes by memory usage.  post that.

---

### Post by nmaster on 2010-07-20
> **techunit said:**
> I am constantly using around 512MB of ram on my 64bit install of lucid... But seeing that I have 4GBs to pull on I don't see a problem... for you I can though.... 
i have basically the same situation, so i'm not immediately sure what the problem is for the OP.

> Firefox can use up to 80MBs so try chromium...
that might not be a great suggestion.  chromium opens each tab as a new process.  this can potentially chew up a LOT of memory.  if you want a lightweight browser, try epiphany (or any of the other alternatives discussed on the link i posted earlier).

---

### Post by soltanis on 2010-07-20
Start by removing useless daemons running in the background you don't use. Also consider using a different desktop environment; Gnome is resource-hungry. XFCE is a common one, you can go even lower with Fluxbox and its cousins. You don't need to reinstall to do that, either; you can do it all with apt-get.

---

### Post by KingNeil on 2010-07-20
Switching browsers is no good. Ubuntu is using 350MB out of 500MB, with no programs open whatsoever. I don't like Chrome as a browser anyway.

Now, disabling compiz would give me 30MB, you say. But that isn't enough. One guy in this thread posted a screenshot with Ubuntu 10.04 (with compiz) using only 90MB. 

Correct me if I'm wrong, but all the programs he listed aren't running by default anyway, so I really would like to know what he's done.

---

### Post by mike555 on 2010-07-20
All I know is I went from about 400 to 93 by uninstalling those apps and shutting off startup apps ............. just trying to help others ...

---

### Post by nmaster on 2010-07-20
you can either take the desktop install and start trimming, or you can use the minimal install and build up...

i think that the latter is a bit easier, and that way you'll actually *know* what you have on your system.

---

### Post by KingNeil on 2010-07-20
> **mike555 said:**
> All I know is I went from about 400 to 93 by uninstalling those apps and **shutting off startup apps** 

OK, which startup apps did you remove?

[quote=neil.m.master]
or you can use the minimal install and build up...
[/quote]

The problem I have with that is, I don't have the knowledge of Ubuntu to know what things to include, and I certainly wouldn't want to be missing anything critical.

---

### Post by nmaster on 2010-07-20
> **KingNeil said:**
> The problem I have with that is, I don't have the knowledge of Ubuntu to know what things to include, and I certainly wouldn't want to be missing anything critical.

as long as you usually have an internet connection, you can just use APT to install things as you need them. usually its pretty obvious.  for example, if you need to set up your printer install CUPS. if you need to use ssh, install openSSH.  its really not that big of a deal.

that being said, i can understand how it can seem intimidating.  if you don't feel comfortable doing it, don't.  good luck with whatever solution you do try.

---

### Post by KingNeil on 2010-07-20
Thanks a lot.

I'm still trying to figure out what mike555 managed to do... I tried removing all the apps he said, and I managed to gain 10MB of RAM.

I have absolutely no idea how he went from 400MB to 90MB. It seems like magic. There is obviously something major he did, which he forgot.

If I can't get an answer on this one, I'm going to try Xubuntu.

---

### Post by nmaster on 2010-07-20
something lighter like lubuntu might be worth a look as well.

---

### Post by KingNeil on 2010-07-20
Upgraded via synaptic to Xubuntu. Still using the same amount of RAM. Was going to do a fresh install, but the keyboard would not work during the disc boot. 

This whole minimum install thing is looking more and more attractive.

---

### Post by mike555 on 2010-07-20
OK, you all got me wondering how I did it, so I did it again , this time on a 2001 AMD 1 GHz. with 3 sticks of 128 memory, after installing it (it took a while) I uninstalled things I don't use ,then updated , then installed some lighter apps ,but was getting 190 mb at startup ..... I then uninstalled the me-menu, rt.clicked on the envelope and the switch user removing them from the toolbar , restarted and am now down to around 90 mb at startup ........ so I guess the big thing is the me-menu,the switch user, and the envelope thingys .... weird..

[IMG]http://i29.tinypic.com/2z8sy92.jpg[/IMG]

---

### Post by philinux on 2010-07-20
> **KingNeil said:**
> Upgraded via synaptic to Xubuntu. Still using the same amount of RAM. Was going to do a fresh install, but the keyboard would not work during the disc boot. 

This whole minimum install thing is looking more and more attractive.

There is no problem with your memory usage at
all. Linux uses ram very diff than  windows. Unless your system is not running well ignore it. How big is swap.

---

### Post by KingNeil on 2010-07-20
I just restarted my computer, and now I'm down to 140MB. This is great, so thanks to mike555 for that. But I'm looking to trim right down to 90 or so. So I'm going to see what else I can cut. Still haven't cut compiz.

[quote=philinux]
There is no problem with your memory usage at
all. Linux uses ram very diff than windows. Unless your system is not running well ignore it. How big is swap. 
[/quote]

It was a big problem, because my hard drive was constantly churning, and everything was slow. Now it's totally silent, and everything is fast. So, there must have been a lot of swap.

---

### Post by KingNeil on 2010-07-20
Cut compiz and I'm down to 120MB. 0 swap.

I should point out that I installed xubuntu-desktop, then restarted, then removed it, then restarted. Installing it may have removed some Ubuntu features that were memory hogs.

---

### Post by KingNeil on 2010-07-20
Sorry for the triple post, but I restarted Ubuntu again, and now it's back to 350MB+ swap. Urrrgggghhh.

Restarted again and now I'm back to normal again. Strange business....

---

### Post by nmaster on 2010-07-20
> **KingNeil said:**
> This whole minimum install thing is looking more and more attractive.

go for it then.  just back up your data and in the worst case you've only wasted a little time.  in the best case, you have exactly what you want.

---

### Post by KingNeil on 2010-07-21
I'm marking this thread as **[Solved]**. Mike555's solutions have worked very well.

In addition to stuff he's said to remove in this thread (go back and look), here are some things he PMd me:

bluez, britty,compiz,computer janitor,empathy,espeak, evolution,(BUT NOT
evolution-data-server-common),gbrainy,gwibber,ubuntu-one

then went into startup and unchecked remote desktop,login sound,user folder update, visual assistance.

right clicked on the envelope thingy and removed it from the toolbar and also the switch user thingy

--

As well as these, and everything else he's said in the thread, I disabled the following services, in boot-up manager (bum):

rsync, cron, cups (keep this if you want printing), acpid (you might want to keep this if you have a laptop, I'm not sure)

--

The key here is... you have to RESTART the computer, possibly twice, to see the effects. And, when you're uninstalling in synaptic, choose full removal, just to be safe.

--

Overall, this has worked very well. But... it has been very unscientific. If I knew the right tool to check which processes are using what memory, this could have been done without me posting a thread. System Monitor did not show the 230 or so MB I managed to cut. As I posted earlier, it only showed about 30MB of total processes. Boot-up manager doesn't show resource usage of services. I have no idea where to find the usage of startup apps. It's quite frustrating to be frank.

But for those out there who want to keep Ubuntu 10.04 lean, I can definitely recommend this thread. Maybe if I type some keywords here, it will show up in Google searches. Ubuntu 10.04 cut memory usage free up memory use less memory make faster trim memory consumption stop processes services daemons slim down ubuntu.

Thank you.

---

### Post by Paqman on 2010-07-22
> **KingNeil said:**
> 
The problem I have with that is, I don't have the knowledge of Ubuntu to know what things to include, and I certainly wouldn't want to be missing anything critical.

You'd probably find the script in my sig very useful then ;)

---

### Post by bobwdn on 2010-08-30
I tried this and it worked great.

First, *sudo apt-get update && sudo apt-get upgrade.*Then I backed up the computer so I had a bare bones base to return to should I create an issue for myself. I STRONGLY SUGGEST YOU BACKUP BEFORE YOU BEGIN!!!!

IN MY CASE, I had experienced some variation of the posts in this thread, although, not much.

The following reduced my memory use from 252Mb RAM (on a P4-2.5 512Mb RAM machine) to 135Mb.

This is my daughters machine and it has always been rather slow compared to my other P4 experiences. (Grated some of those experiences used Xubuntu, but my daughter likes her Ubuntu Desktop, so I was trying to keep it for her.)

So, from the notes I made from ALL the comments above me, I removed the following using synaptic:

Select for "complete" removeal:
evolution, evolution-common, evolution-couchdb, evolution-exchange, evolution-indicator, evolution-plugin, evolution-webcal, indictor-one, empathy, empathy-common *(synaptic will prompt you to remove nautilus-sendto-empathy, so tell it agree)*, mono *(now, the mono selection is going to cause synaptic to pop-up many, many other programs that will be removed with it. I agreed to all and have not had a problem, YET!!! The list included: f-spot, gbrainy, libart2.0-cil, libflickrnet2.2-cil, libgconf2.0-cil, libglade2.0-cil, libglib2.0-cil, libmime2.4-cil, libgnome-keyring1.0-cil, libgnome-vfs2.0-cil, libgnome2.24-cil, libgnomepanel2.24-cil, libgtk2.0-cil, libluanchpad-integration1.0-cil, libmono-addins-gui0.2-cil, libmono-adins-gui0.2-cil, libmono-cairo2.0-cil, libmono-corlib2.0-cil, libmono-data-tds2.0-cil, libmono-i18n-west2.0-cil, libmono-posix2.0-cil, libmono-security2.0-cil, libmonosharpizp2.84-cil, libmono-sqlite2.0-cil, libmono-system-data2.0-cil, libmono-system-runtime2.0-cil, libmono-system-web2.0-cil, libmono-system2.0-cil, libmono2.0-cil, libndesk-dbus-glib1.0-cil, libndesk-dbus1.0-cil, libnunit2.4-cil, mono-gac, mono-runtime AND tomboy)*

Additonally, continue selecting for "complete" removal:
gwibber, gwibber-service, bluetooth *(Synaptic prompts to remove bluez-utils, I agreed)*, computer-janitor *(Synaptic prompts to remove computer-janitor-gtk, I agreed)*, espeak, *(Synaptic prompts to remove gnome-orca, libspeak1, python-speechd AND speech-dispatcher, I agreed)*, espeak-data *(Synaptic prompts to remove gnome-bluetooth AND gnome-user-share, I agreed)*, bluez *(then below bluez was bluez-alsa, bluez-cups AND bluez-gstreamer, so I saw no reason to keep those and remove them also)*, and finally compiz *(Synaptic prompts to remove compiz-fusion-plugins-main, compiz-gnome, compiz-pluginz, compizconfig-backend-gconf AND libcompizconfig0, and I agreed to remove those, also.)*

Then I went into *System--> Preferences--> Startup Applications* and un-checked: Evolution Alarm Notification (evolution is gone), GNOME Login Sound, Remote Desktop AND User folders update.

Finally, up in my taskbar, I right clicked 'envelope thingy' and removed it from the panel which removed the volume control icon. When I went to add them back (I thought!!) I got the volume applet back and not the envelope thingy. Things that make you go hum-m-m! But, oh well, I only wanted the volume control, anyway!

I rebooted and my memory use had dropped to 135Mb RAM and 0Mb swap.

And as I said up above, so far all is good. 

So, REMEMBER, BACK UP FIRST, then if you have an issue you can start over.

Good luck . . . .

---

### Post by soldier1st on 2010-09-24
i have to disagree with this thread as someone said earlier that Linux uses memory differently than Windows and removing ANY of the default ubuntu apps can result in an unstable system and disabling the default startups won't make much difference. ifyou want a responsive system then either upgrade your memory(it is dirt cheap) or use a lighter Ubuntu/Linux distro, if you are not willing to do those simple things then your sol.

---

### Post by KingNeil on 2010-09-24
> **soldier1st said:**
> i have to disagree with this thread as someone said earlier that Linux uses memory differently than Windows and removing ANY of the default ubuntu apps can result in an unstable system and disabling the default startups won't make much difference. ifyou want a responsive system then either upgrade your memory(it is dirt cheap) or use a lighter Ubuntu/Linux distro, if you are not willing to do those simple things then your sol.

What you're saying is simply not true. By removing the apps listed in this thread, you can take your machine from 400MB usage to about 100MB. The system is perfectly stable, and you're just using generalisations based on no specific details.

---

### Post by 7h3d4rk0n3 on 2010-09-24
When you are in the System Monitor, go to "View" and select "All Processes" and then repost the image that way.

---

