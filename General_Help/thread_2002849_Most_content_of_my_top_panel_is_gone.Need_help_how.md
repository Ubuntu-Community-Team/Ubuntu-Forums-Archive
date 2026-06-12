---
title: "Most content of my top panel is gone.Need help how to restore."
date: 2012-06-13
forum: General Help
---

### Post by psycrow117 on 2012-06-13
Hi, I'm a starter at Ubuntu. I had this problem my computer suddenly turn off due to power failure. After turning it on again. my top panel content is gone. the default content of gnome classic(even on gnome classic no effects) on Ubuntu 12.04 LTS.  Is there anyway I can reset to default this again?

---

### Post by steve7777777 on 2012-06-13
bump.
I don't have an answer, but there are two that you should consider doing:

1. Make an image of your boot drive using Clonezilla and save it on a USB drive, or another drive on the machine. Off site if is best. On my stable system an image is made about once a month or when a bunch of packages are installed. This way if you lose a hard drive or have some other problem, just restore the image. 
2. Do routine (daily) backups of /home and /etc using the backup method of choice.

---

### Post by Frogs Hair on 2012-06-13
The following command worked with the gnome panel in previous versions. ```
gconftool --recursive-unset /apps/panel && killall gnome-panel

```

---

### Post by psycrow117 on 2012-06-13
@steve7777777

That's too much. =( I just want the default settings of my top panel...

@Frogs Hair

It's still doesn't work it just reset the top panel.

---

### Post by JosephBeck on 2012-06-13
Go into compiz manager (If you don't have it, install it), Go to preferences on the left at the bottom. Where it says unity, switch it to default. It'll undo all changes to Unity since you installed it so you will need to resize launcher icons again but other than that shouldn't be much work at all.

---

### Post by steve7777777 on 2012-06-13
> **psycrow117 said:**
> @steve7777777

That's too much. =( I just want the default settings of my top panel...


Sorry this is off topic, once you get the top panel deal with the backup stuff. BTW from what you're describing there may be other problems too. 

Get Clonezilla at [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php) and make a boot CD. Boot off of that then use defaults. You choose the destination/target for the image first, then later select the source - again, choose defaults, the whole drive, likely SDA.
I had a hard drive with many bad sectors. No problem, I threw out the old drive, installed a fresh drive and restored an image to the bare metal drive. Very east and I was back up and running.

For backup - like I said you need to backup at least /home and /etc. Many ways, gui's or set up a cron job. 

OK I'll be quiet now and good luck.

---

### Post by JosephBeck on 2012-06-13
> **steve7777777 said:**
> Sorry this is off topic, once you get the top panel deal with the backup stuff. BTW from what you're describing there may be other problems too. 

Get Clonezilla at [http://clonezilla.org/downloads.php](http://clonezilla.org/downloads.php) and make a boot CD. Boot off of that then use defaults. You choose the destination/target for the image first, then later select the source - again, choose defaults, the whole drive, likely SDA.
I had a hard drive with many bad sectors. No problem, I threw out the old drive, installed a fresh drive and restored an image to the bare metal drive. Very east and I was back up and running.

For backup - like I said you need to backup at least /home and /etc. Many ways, gui's or set up a cron job. 

OK I'll be quiet now and good luck.


He doesn't need to do all that extra work for a simple home computer. Once he resets Unity via Compiz and sets it to how he likes he can export the settings and next time it messes up he can import the settings file and it'll restore the settings to how they should be, as the panel is part of Compiz. No need to back up all this extra stuff just for a simple panel issue.

---

### Post by steve7777777 on 2012-06-14
> **JosephBeck said:**
> **He doesn't need to do all that extra work for a simple home computer.** Once he resets Unity via Compiz and sets it to how he likes he can export the settings and next time it messes up he can import the settings file and it'll restore the settings to how they should be, as the panel is part of Compiz. No need to back up all this extra stuff just for a simple panel issue.

IMO it's not good advice to dissuade someone from backing up on a regular basis and creating a system image occasionally, even for a "simple home computer."

---

### Post by Mark Phelps on 2012-06-14
I had a similar problem a while back, and the commands in the link below fixed it:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

### Post by SmallWorld on 2012-09-11
I had a very similar problem wherein I deleted the panel battery icon by accident and couldn't get it back.  I wanted to just reset the panels, but all the suggestions I saw online just made my panels disappear and then reappear in the same broken state.

I'm running Gnome3 Classic on Ubuntu DE 12.04.1 64bit.

The second post at [http://askubuntu.com/questions/125662/how-to-reset-gnome-panel]("http://askubuntu.com/questions/125662/how-to-reset-gnome-panel") gave me a solution that did work. To paraphrase that post, my solution was:

```
sudo apt-get install dconf-tools
dconf reset -f /org/gnome/gnome-panel/
```

This reset my panels to the default settings.

---

