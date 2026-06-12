---
title: "How easy is it to update ubuntu ?"
date: 2011-07-29
forum: General Help
---

### Post by Michael Wayne on 2011-07-29
Where can I find the documented procedure to update to the latest stable version of ubuntu that will cause me no grief? i.e. won't delete settings for samba, squid etc etc. and the fact that my server is being used as my Time Machine.

What is the best procedure to follow?
Thanks in advance,
Michael

---

### Post by dcstar on 2011-07-29
> **Michael Wayne said:**
> Where can I find the documented procedure to update to the latest stable version of ubuntu that will cause me no grief? i.e. won't delete settings for samba, squid etc etc. and the fact that my server is being used as my Time Machine.
.........

Since you are using a LTS - 8.04 - you should not really update until the next LTS is released.

The whole point of LTS releases is to provide a stable, supported platform that is not changing every six months so the fanbois can have the latest GUI toys to play with.

Decide if you want your server to continue to serve or risk installing a non-LTS release that will probably cease being supported before 8.04 server is:

[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

---

### Post by Topsiho on 2011-07-29
Hello Michael,

It is really easy to do, from ordinary distribution to ***the next one***, and from an LTS distribution to the next one, or to the next LTS distribution. So: from 8.04 LTS to 10.04 LTS.

In the Update program you are prompted to upgrade to a next version, when this becomes available, unless you have disabled this (eg. in Synaptic). So this kind of update, from distribution to the next one is called an upgrade, not: update.

The only thing you have to do is press this Upgrade button, and there you are. This does everything that you ask for, and is really easy. It takes a very long time though, as it is really a huge, gigantic monstrous update, downloading tons of data, for which you need to have sufficient memory and hard disk space, and which may take many hours, and which you may not interrupt in any way.

It proves also to be risky. Sorry to have to say that. So a clean install is IMHO a very much better option. If you have a separate /home partition, you can keep this, and so all your settings and personal files, and so on.

However, after the new install you'll have to install the extra programs of yours, and of course all the updates that were released after the Live CD was made. You are lucky here: only very recently (July 21st) the latest 10.04.03 was released, so you save a lot of work downoading this one first and use this, from Ubuntu of course).

Before you do this install it is wise to backup all your /home partition, or anyway your personal files ...

Hope this helps,

Topsiho

---

### Post by raja.genupula on 2011-07-29
Hey man , my best advice will be on your comfort . if you are ready to take risk then go to non-stable server versions , other wise move with stable .

---

### Post by grahammechanical on 2011-07-29
I am not sure if you have Update Manager in 8.04. You do have synaptic Package Manager and may be Software Sources in a menu somewhere. What you need to do is set the update method to only look for LTS releases.

In my 11.04 Synaptic I select Settings>Repositories and in the dialog box that appears I select the Updates tab. From there I can select a menu called Release Upgrade Show New Distribution Releases. I have the options of Normal Releases or Long Term Support Releases only.

That is have easy it is to upgrade.

Regards.

P.S. an upgrade will not delete settings or programs. A fresh install will. Unless you have the OS on a separate partition to what is the /home folder on the desktop version. Perhaps you should ask the moderators to move this thread to the Server Platforms section of the forums, instead of having it in General Help

---

### Post by Wim Sturkenboom on 2011-07-29
> **Michael Wayne said:**
> Where can I find the documented procedure to update to the latest stable version of ubuntu **that will cause me no grief**? i.e. won't delete settings for samba, squid etc etc. and the fact that my server is being used as my Time Machine.
You must be joking. Don't rely on the upgrade not breaking the system. If you're lucky it indeed will not cause grief; if you're not so lucky you end up doing a re-install.

My upgrade from 6.06 to 8.04 went smoothly. My upgrade from 8.04 to 10.04 went wrong and I ended up re-installing. So there is NO guaranteed safe way. Just be prepared.

---

### Post by Michael Wayne on 2011-07-30
Now that's what I call a great response. I assume that I could upgrade to 10.04LTS as this falls into the long Term Support categories. 
By definition does this mean that 10.04LTS is as stable as 8.04LTS? 

Based on the following your thoughts are appreciated:

On my Proliant server the HD that it came with has only got Ubuntu installed and is only used to run Webmin to administer the 2 additional 1TB drives which act as music store for around 


[LIST=1]
[*]3000 albums.
[*]The music repository of said music so iTunes is pointed to it to allow it to be played and distributed via my Mac Mini and then through my Pioneer LX82 amp.
[*]General on the fly back up of miscellanea when needed.
[/LIST]
It's loaded on to the 250g drive that it came with and the only thing that was loaded is the this from Kremelicious...
[http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

I also use a part (partition) of one of the big drives as a 'samba' smb connection so my wife's work Windows 7 Acer can be backed up and seen on here network via Ethernet via my 24 port switch. Works a treat. 
  
Its on my Macs that I do what I do so Ubuntu is used solely to administer

...Time Machine backups for both my Macs
...Restore point for Windows 7 laptop
...iTunes storage

From what I have read it seems that all of you use Ubuntu as your OS and therefore have a lot of 'stuff' you could potentially lose. Hence your great advice and obvious trepidation based on others upgrade failures.

Would I benefit from an upgrade to 10.04LTS or later?
  
As an educated guess from your points of view and based on my scenario, what do you think my upgrade path should be?

Thank you all for your expert knowledge and time taken to answer my queries thus far.

Michael

---

