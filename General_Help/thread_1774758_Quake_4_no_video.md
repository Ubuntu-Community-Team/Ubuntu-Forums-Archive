---
title: "Quake 4 no video"
date: 2011-06-03
forum: General Help
---

### Post by Pizarro on 2011-06-03
I have installed quake4 using the normal instruction "http://www.blog.highub.com/linux/install-and-play-quake-4-on-ubuntu/" and everything seemed to go ok.
But on running the game the screen goes blank and monitor reports out of frequency.Judging by the audio the game is running the intro. I'm sure it is as I've played it before on a previous ubuntu install when this same machine was dual booting. Video card is a geforce 7600gs. I have edited the config file to make the game in English as I remembered it defaults to Spanish. I assume I have to tweak another config to solve my problem but have no idea what.

sorry posted here in error have reposted in Gaming and Leisure

---

### Post by Beta_Grumm on 2011-06-03
First of all I would make sure you have installed the latest drivers. I've often had to go get the latest proprietary drivers to fix this same type of issue with other games.

Second of all, I would find it hard to believe that upon a new install that the game resolution would be out of range... but nothing really surprises me. You'll need to find the config file for the video settings: (lemme see if I can conjour it up via the mighty Google)
Try looking at this file: quake4config.cfg in the id Software\Quake 4\q4base\ directory.

(I don't actually own this game. I'm just poking around Google for paths and file names)

I'm also seeing some people suggest to delete both quake4config.cfg and autoexec.cfg (after making backups of course) and the game should replace both of these with default settings. Although it sounds as if you never changed them to begin with. 

Try those, see what happens.
Good luck.

---

