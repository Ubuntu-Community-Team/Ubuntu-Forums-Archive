---
title: "Swapping from KDE to Gnome"
date: 2009-08-22
forum: General Help
---

### Post by RabbitWho on 2009-08-22
Well I think i've reached breaking point with trying to get kubuntu to connect to the Internet ( [http://ubuntuforums.org/showthread.php?t=1246964](http://ubuntuforums.org/showthread.php?t=1246964) )  I would like to switch to the more idiot proof gnome/ubuntu option (not that people who use it are idiots, just me) before my hair falls out or I have a heart attack. 
They mentioned something in the Kubuntu help notes that if you're not happy with it you can switch from KDE to GNOME, is there a way to do this without installing everything (yet again) Will I loose the files I have? This doesn't bother me now because I only just installed yesterday.. and again this morning.. sigh... so i don't have any files to try and save, but in the future if kubuntu sorts out this ppp issue then I'd like to swap back if it was possible. 

Advice?

---

### Post by bela42 on 2009-08-22
sudo apt-get install ubuntu-desktop

And afterwards log in to a new GNOME session.

Good Luck!

---

### Post by SuperSonic4 on 2009-08-22
Kubuntu and ubuntu have largely the same OS behind closed doors so chances are there will be no difference

---

### Post by GeorgeVita on 2009-08-22
Hi,
trying to help RabbitWho I do not know the KDE text editor name.

We need to edit a configuration file (/etc/wvdial.conf) so it must run as superuser.

gnome command = 'sudo gedit /etc/wvdial.conf"

Can anybody help?

Thanks in advance,
George

---

### Post by diggedy on 2009-08-22
It might be me but I started with ubuntu and installed the KDE desktop rather than the Kubuntu desktop. I had to install many other things manually but ive tried kubuntu several times in the past and uninstalled it due to it being so buggy and unstable. Since doing it this other way everything seems fine. 
Someone might point out that there is no difference but its working for me now so something must be different.

Anyway my point is, maybe try that if you love KDE more than gnome as I do :)

---

### Post by RabbitWho on 2009-08-22
I think the text editor was "kate" George, i hope i managed to do what you asked. Thanks for not giving up on me. I won't give up as long as people think it's still possible! 

~~


Why do people say there is no difference if ubuntu takes about 30 seconds to identify and use my dongel and connect to the internet and kubuntu can't. That's more than superficial! If I had known this would happen I would have gone with ubuntu from the get-go. But now i've completly of fallen in love with the kubuntu interface and it would be with a heavy heart that I leave it. 



Is there  a way to just keep that one part (the "ppp") of gnome working and have everything else kde? 

> 
sudo apt-get install ubuntu-desktop 


Does that work without being connected to the Internet? 

Thanks for your help everyone!

---

### Post by oldos2er on 2009-08-22
> **GeorgeVita said:**
> Hi,
trying to help RabbitWho I do not know the KDE text editor name.

We need to edit a configuration file (/etc/wvdial.conf) so it must run as superuser.

gnome command = 'sudo gedit /etc/wvdial.conf"

Can anybody help?


 Use **sudo nano /etc/wvdial.conf**. KDE has several editors (kate, kedit, kwrite, etc.) but I don't know which ones are installed by default.

---

### Post by GeorgeVita on 2009-08-22
Hi **oldos2er**, thanks for answering!

For a newcomer nano & vi are a little bit confusing (line editors).
Is kwrite or kedit copy/paste style for simple .txt files?

Thanks in advance,
George

---

### Post by oldos2er on 2009-08-22
Nano is far easier for a beginner to use, compared with vi; at least in my opinion. Most commands you need to use in nano are right there at the bottom of its screen.

 If you were going to use kedit (for example), you'd run **kdesu kedit /etc/wvdial.conf**.

---

### Post by siriusb_hun on 2009-08-23
RabbitWho,

I switched from Kubuntu (KDE 4.2) to Gnome again after 4-5 months this week as well.

You need to make 2 steps:

1.) "sudo apt-get install ubuntu-desktop" in a terminal, then to get rid of kde:

2.) "sudo apt-get purge kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-wallpapers"

Backup everything you think vital (stored in kde applications) before you start.

In synaptic you can remove other kde packages.
KDE 4 is not bad, but I had to realize I prefer Gnome :)

---

### Post by RabbitWho on 2009-08-23
> RabbitWho,

I switched from Kubuntu (KDE 4.2) to Gnome again after 4-5 months this week as well.

You need to make 2 steps:

1.) "sudo apt-get install ubuntu-desktop" in a terminal, then to get rid of kde:

2.) "sudo apt-get purge kdebase-bin kdebase-data kdebase-plasma kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace kdebase-workspace-bin kdebase-workspace-data kdebase-workspace-wallpapers"

Backup everything you think vital (stored in kde applications) before you start.

In synaptic you can remove other kde packages.
KDE 4 is not bad, but I had to realize I prefer Gnome :smile:

Thanks I'll save this. 
Oh I love KDE, absolutely no doubt about it. But I'm just getting really frustrated with all the bugs. if it was just things that were my fault I could handle it and learn. But it's things like crashes and graphics glitches. I'm going out of my mind. 

Bleaugh. I'll give it another little while. But I've already invested so much time just in getting it to work!

---

### Post by SuperSonic4 on 2009-08-23
Kate is KDE's default text editor although I usually edit files in nano

---

### Post by hyperdude111 on 2009-08-23
> **diggedy said:**
> It might be me but I started with ubuntu and installed the KDE desktop rather than the Kubuntu desktop. I had to install many other things manually but ive tried kubuntu several times in the past and uninstalled it due to it being so buggy and unstable. Since doing it this other way everything seems fine. 
Someone might point out that there is no difference but its working for me now so something must be different.

Anyway my point is, maybe try that if you love KDE more than gnome as I do :)

I too had network issues with kde 4.2 and went to gnome. I think it was a fault with knetwork-manager. Since the release of KDE 4.3 I have moved back and have found the issue fixed.

However if you want gnome.

1. sudo apt-get install ubuntu-desktop

2. Log out, select options-sessions-gnome

3. Log in

---

### Post by diggedy on 2009-08-24
> **RabbitWho said:**
> Thanks I'll save this. 
Oh I love KDE, absolutely no doubt about it. But I'm just getting really frustrated with all the bugs. if it was just things that were my fault I could handle it and learn. But it's things like crashes and graphics glitches. I'm going out of my mind. 

Bleaugh. I'll give it another little while. But I've already invested so much time just in getting it to work!

try what I suggested before and install ubuntu from the live CD then using synaptics install "KDE-workspace" rather than the "kubuntu-desktop"

you will have to have a trawl through the list to install other packages to get it running how you want but it will work. As far as i know doing this just installs the base KDE workspace and none of the extras built into kubuntu which are most likely the cause of your problems

---

