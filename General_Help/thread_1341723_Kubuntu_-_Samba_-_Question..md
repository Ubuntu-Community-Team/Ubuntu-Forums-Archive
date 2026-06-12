---
title: "Kubuntu - Samba - Question."
date: 2009-11-30
forum: General Help
---

### Post by Roasted on 2009-11-30
When I connect to my Samba server, I go through Dolphin with Network - Samba Shares - Samba Server - My Share.

When I click on my share it requires me to log in. Except, it asks twice, every time. Why is this? Why does it need to ask twice? 

Secondly, if I close Dolphin and reopen it and navigate to my Samba share, I have to log in again (twice). Nautilus mounts the Samba drive and it stays put until I unmount it. Is there any way I can do that with Dolphin so it only unmounts if I say?

---

### Post by Zorael on 2009-11-30
Dolphin doesn't mount the drive, instead navigating to it (and in it) using its samba [KIO slave](http://en.wikipedia.org/wiki/KIO).

For what it's worth, I recommend smb4k if you want to actually mount shares. It's in the repos, package of the same name.

(I can't say why it's asking for your password twice, though.)

---

### Post by Roasted on 2009-12-01
So, what's the smartest thing to do with using Samba in KDE? Should I be using konq with smb://server/share? Or is Dolphin just fine to use with Samba?

It's just frustrating because earlier I went through Samba to hit the Windows server on our network. Then I rebooted and tried again. No shares came up. Whyyy?

---

### Post by Zorael on 2009-12-01
> **Roasted said:**
> So, what's the smartest thing to do with using Samba in KDE? Should I be using konq with smb://server/share? Or is Dolphin just fine to use with Samba?

It's just frustrating because earlier I went through Samba to hit the Windows server on our network. Then I rebooted and tried again. No shares came up. Whyyy?
In the perfect world, all apps would be KIO slave-aware, and you could use the smb:// protocol to access whatever you wanted. As it is, in many apps, when opening a file from a samba share it will first copy it to /tmp, and then open it.

gvfs works around it by mounting, and it has its points and its drawbacks. Apps will get a local path to the share, but it mounts as soon as you even think about accessing it and then other apps can't unmount it (eg. Device Notifier).

One other alternative that sadly only seems to be semi-reliable is **fusesmb**/**smbnetfs**. They're two terminal apps with the same functionality, and I don't really know what the real difference is.

Basically it will userspace mount your entire local network to a directory. Under it, it will generate another directory with your workgroup, and then under it directories for the connected hosts, and under it its shares.

It has (or used to have) stability issues if not specifically told to only use one thread, libsmbclient not being thread-safe. You'd just have to pass an argument to stop it from multithreading.


**edit**: As for not seeing servers, one thing to try is to run '**smbtree**' in a terminal. If the shares are listed there and KDE can't find them, something's wrong in KDE. If they're not listed there, something's wrong with samba on your machine, or something's up with your network. I don't know if restarting the samba service helps any, as I believe that's only the samba server?
```
$ smbtree
Enter zorael's password:
LAPPNET
        \\LETHE                         lethe server (Samba, Ubuntu)
                \\LETHE\IPC$            IPC Service (lethe server (Samba, Ubuntu))
                \\LETHE\temp
                \\LETHE\audio
                \\LETHE\video
                \\LETHE\documents
                \\LETHE\downloads
                \\LETHE\print$          Printer Drivers
```
This is my netbook connected to my local network made up by four other computers, of which it can't see any. This only happens when I'm connected to a specific router (I have two around the house), so I've narrowed it down to that router stopping samba traffic for some obscure reason. So it can be caused by hardware, too.

To be able to resolve netbios hostnames ("computer names"), you need to install winbind and add it to the resolving order. Basically, install the **winbind** package, and then edit **/etc/nsswitch.conf** and modify the hosts line to look like this.
```
hosts:          files [COLOR="Green"]**wins**[/COLOR] mdns4_minimal [NOTFOUND=return] dns mdns4
```
Annoyingly, this router also blocks this.

---

### Post by Roasted on 2009-12-01
Don't you think that it's a router config (port maybe?) that's blocking samba? Routers shouldn't block what's on the "allow" list..

---

### Post by Roasted on 2009-12-01
Has anybody found that with Dolphin if you log into a Samba share, sometimes it locks up for about 20-25 seconds? I can't remember if I ever ran into it with Nautilus or not, but I didn't use Gnome much at work, now I use KDE a lot at work and I noticed it with Dolphin.

Also - what is it about Konqueror that allows it to search smb shares and Firefox can't? I understand Konq is a KDE app and all that, I'm just curious what's going on in the background between Firefox and Konqueror.

---

### Post by Zorael on 2009-12-01
Well, it shouldn't really block anything inside the local network. The router should just act as a switch (or wireless access point), but obviously it's being picky.

Regarding Dolphin pauses; no idea, never experienced that myself. Anything output to the terminal?

Regarding Firefox; this may just be the winbind deal I mentioned in my earlier post. Maybe the library KDE uses to interface with samba servers (and look up their hostnames) can do what you would otherwise need winbind for.

---

### Post by Roasted on 2009-12-01
How would I run Dolphin/Samba from terminal so I could get an output?

It's not a big deal, it rarely happens, but if I scroll through folders with lightning speed sometimes that triggers it.

I notice it more on my laptop than I do my spare desktop. Perhaps network connectivity could play a factor in it? (wireless?)

---

### Post by Zorael on 2009-12-02
```
$ dolphin &
```
:3

---

### Post by Roasted on 2009-12-02
It happens on my laptop pretty frequently now, whereas on my spare desktop it really doesn't happen much at all. I only had it happen once and it recovered itself very quickly.

Both systems are 9.04 64 bit with KDE 4.3.2.

On the laptop if I connect right away and then select music and scroll up and down a couple times really fast, that often is enough to lock it up for a few seconds (15-20 average), whereas the desktop is perfectly fine, yet considerably less powered than the laptop (1gb RAM P4 versus core 2 duo 4gb RAM).

Desktop is wired.
Laptop is wireless.

Laptop has decent signal.

Running Dolphin & in terminal only yielded Error in thread 93485903845029384590283502389 a few times. Half of these popped up from me selecting "Samba Shares" from Network, and the other half happened when I was in the directory going click happy to see if it'd freeze.

Hmm... any thoughts?

---

### Post by rkoma on 2009-12-02
> **Roasted said:**
> Has anybody found that with Dolphin if you log into a Samba share, sometimes it locks up for about 20-25 seconds? I can't remember if I ever ran into it with Nautilus or not, but I didn't use Gnome much at work, now I use KDE a lot at work and I noticed it with Dolphin.


I have similar problem, when View Properties are changed on samba directory, Dolphin is locked for 10-20 seconds. View properties are not saved, when I enter the same directory again, the old view remains.

View properties are saved in .directory file. While Dolphin is locked, from the terminal I can see that Dolphin creates .directory.lock.<number> file several times, but it seems that it fails to copy/move it to .directory file. After several tries, Dolphin gives up and no .directory file is created.

This happens only on samba mounted directories, on local directories works perfectly.

Does anybody knows what are the exact internal steps in Dolphin to create .directory file?

---

### Post by Roasted on 2009-12-02
My view properties seem to be fine. They always open in column view, which I prefer. It's just when I get super click happy like I'm a hamster on steroids that things will lock up for a little bit. I wonder if my situation is also dealing with the .directory?

What version of KDE are you running? Do you have this same problem with Konquerer?

---

### Post by rkoma on 2009-12-03
I am using KDE 4.3.4, but I had the same issue with all previous KDE 4.xx versions. My default view properties are set to my preference and everything work ok until I try to change view mode on mounted smb directory - there is always a problem I have described above.

Just tested with Konqueror, the same issue happens, .directory file can not be created.

---

### Post by Roasted on 2009-12-03
So the red flag was you try to change the view when connected to Samba shares and it just doesn't save the fact you changed the view when you re-open it? Is that what your issue is?

---

### Post by Roasted on 2009-12-03
Is Dolphin retarded?

Konquerer can find the samba server just fine.
5 minutes ago, Dolphin could find it just fine.
Now, Dolphin can't.
Yet Konquerer still can.

---

### Post by Zorael on 2009-12-03
That is weird. Shouldn't Konqueror be using the same code as Dolphin for file management? (dolphinpart)

---

### Post by Roasted on 2009-12-03
Not sure. I think part of the problem was I had a computer plugged in to the one I was using.

The one that failed to see the proper samba server was an imaging server with FOG installed. All I could see was that computer that was plugged into it. I rebooted the system and as it was rebooting realized I was still connected, so I unplugged it and it was fine then. I don't know if it was the reboot that fixed it or the unplugging of the other computer.

I have 2 network cards in this system. 1 with a static IP just for imaging, and the other for DHCP access.

Maybe I posted here a bit too quickly. :P

---

