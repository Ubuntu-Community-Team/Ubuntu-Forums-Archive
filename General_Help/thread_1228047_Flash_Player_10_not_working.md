---
title: "Flash Player 10 not working"
date: 2009-07-31
forum: General Help
---

### Post by askinne2 on 2009-07-31
Hi, I am running ubuntu 8.1 that I just upgraded too last night. I am a complete ubuntu beginner so I will have to have my hand held through this process. Basically flash stopped working. I tried removing the nonfree plugin and reinstalling it and nothing. According to firefox these are my shockwave plugins: "Shockwave Flash 9.0 r999" and "Shockwave  Flash 9.0 r999. Gnash 0.8.4, the GNU SWF Player....". This does not make sense to me because through Synaptic Manager I have "flashplugin-nonfree 10.0.22.87" and "flashplugin-nonfree extrasound" installed. I have have installed Flash Player 10 via the deb downloaded from the Adobe website. Anyways, all I see is a grey block where videos on youtube and such should be. They have a big wierd player button in the middle of them. You can click the button, but the video never loads.  Any help is appreciated.

---

### Post by Hamchan on 2009-07-31
You seem to have some redundant flash players. That grey box is normal for Gnash, which is why many choose not to use it. Use synaptic to remove gnash, then firefox should start using the adobe plugin but you may want to reinstall that just to be sure.

---

### Post by wojox on 2009-07-31
Check out lovinglinux post:

[http://ubuntuforums.org/showthread.php?t=1193567](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by askinne2 on 2009-07-31
Thanks for the replies. I removed Gnash and also tried following the instructions in the thread I was directed too. Now youtube is telling me to get Flash Player 9 or higher to watch the video. The grey box that is associated with gnash is gone of course, so now theres just a message telling me I dont have flash when indeed I do. I suspect that firefox is not communicating with flash correctly.

Edit: I checked firefoxs plugin page and the Shockwave Flash plugins have disappeared now that I removed the flashplugin-nonfree via the terminal then I reinstalled it. But although I reinstalled, its missing from firefox. Synaptic says that I have the plugins installed but firefox doesnt.

---

### Post by grizzler on 2009-07-31
> **askinne2 said:**
> Synaptic says that I have the plugins installed but firefox doesnt.

What does the directory **~/.mozilla/plugins** contain? Is **libflashplayer.so** there? Is it an old one?

When I tried to update, for some reason that file couldn't be overwritten. So I manually copied the new version from the downloaded .deb package (it's in **data.tar.gz/usr/lib/adobe-flashplugin**), restarted Firefox and Flash 10.0 r32 was present.

---

### Post by askinne2 on 2009-07-31
Thanks for your reply. There was no libflashplayer.so present in that directory. I got the lobflashplayer.so file on my desktop. When I try to move it into that /usr/lib/mozilla/plugins/ directory it says I dont have permission. How do I move it in there then?

---

### Post by grizzler on 2009-07-31
It belongs in the **~/.mozilla/plugins** directory, i.e. the settings directory in your home directory.

It's possible you can't 'see' this directory as it's a hidden one (name starts with a dot). If you're using Nautilus, there should be some setting to enable you to see the hidden files and directories (I'm not sure exactly where, as I'm using Dolphin on Kubuntu).

---

### Post by Hamchan on 2009-07-31
To see hidden files, go to your home directory and press ctrl+h. Find the .mozilla folder and open it. Create a new folder called plugins in the mozilla folder and drag your .so file there. That should install Flash for firefox

---

### Post by askinne2 on 2009-07-31
I am able to see hidden files and folders but I cannot find any ".mozilla" folder. I have only found a "mozilla" folder which contained a "plugins" folder which in turn did not contain the file "libflashplayer.so". 

If the "mozilla" folder is indeed the same as the ".mozilla" folder you referred too then how can I manually copy the "libflashplayer.so" file into the "plugins" folder. It says I do not have permission to copy the file into that folder. Maybe if I try to do it from the terminal instead of Nautilus. Any instructions on the commands I use to move or copy the file from my desktop into the plugins folder? I am a terminal noob....

---

### Post by askinne2 on 2009-07-31
> **Hamchan said:**
> To see hidden files, go to your home directory and press ctrl+h. Find the .mozilla folder and open it. Create a new folder called plugins in the mozilla folder and drag your .so file there. That should install Flash for firefox

Thank you! This worked. And also huge thanks to grizzler!

---

### Post by Tclarkie on 2009-08-01
[I]
				here is the .deb  
[http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb](http://rapidshare.com/files/155584596/install_flash_player_10_linux.deb) [/I]

---

### Post by Tclarkie on 2009-08-03
this works heaps well [http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177)

---

