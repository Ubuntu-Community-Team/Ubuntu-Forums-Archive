---
title: "Using cron to run a script from home partition"
date: 2011-05-01
forum: General Help
---

### Post by trpnblies7 on 2011-05-01
Yesterday I did a fresh install of my system, but this time, instead of putting everything on one partition, I decided to make separate root and home partitions (root is mounted as / and home is mounted as /home). Everything is working fine, except for one small thing.

I have a script stored in my home folder (/home/brian/background.sh) that changes my desktop background each night. I had it setup in two ways. First, as a startup command, in case my computer was turned off at night, and second, in crontab, to run the script each night when my computer is left on.

The startup command, which I just have in Startup Applications, still works fine:

```
bash /home/brian/background.sh
```

However, the cron version is no longer working:

```
01 1 * * * /home/brian/background.sh
```

Do I need to change the parameters of the cron version since I now have a separate home partition?

I've tried running the script in a terminal to try and figure out the issue, but I can only get it to work if I change my directory to my home folder.

Any help is greatly appreciated.

---

### Post by DaithiF on 2011-05-01
Hi,
2 things:
1. capture the output of the cron job so that you can see if errors occur:
```
01 1 * * * /home/brian/background.sh > /home/brian/background.log 2>&1
```
inspect the background.log file afterward to see what happened.
2. sounds like the script needs fixing so that it isn't dependent on the starting directory.  feel free to post it here if you want help with that.

---

### Post by trpnblies7 on 2011-05-01
Ok, so part of the problem was that I was using root's crontab instead of my user crontab. This wasn't a problem before when I didn't have a separate home partition. So I fixed that problem, but something still isn't working correctly. The script runs from my user's cron now, but the background doesn't change. It still works from the terminal, though.

This is the script. It's supposed to grab the current day's APOD photo and combine it with another image stored in my home folder, then set the new image as the background:

```
#calvin
#
#set this for your self widthxheight  - no spaces
desksize="1680x1050"
# download image from apod site
wget -A.jpg -R.txt -r -l1 --no-parent -nH [http://apod.nasa.gov/apod/astropix.html](http://apod.nasa.gov/apod/astropix.html) 
# move image from obscure folder to main folder, rename image
find ./apod -name "*.jpg" | while read line ; do
	mv "$line" "apod.jpg"
done
rm -r apod
	convert calvincanvas.png -background transparent -resize $desksize^ \
		-gravity center -extent $desksize^ calvincanvasRS.png
	convert apod.jpg -resize $desksize^ \
		-gravity center -extent $desksize^ apodRS.jpg
	convert apodRS.jpg calvincanvasRS.png -mosaic calvin.jpg
gconftool-2 --type string --set \/desktop/gnome/background/picture_filename "$PWD/calvin.jpg"
```

---

### Post by trpnblies7 on 2011-05-01
After a bit more research, it seems that the problem is with cron running a gconftool command. The gconf line at the end of the script, when run directly in a terminal with the full path of the image used, works fine. However, if I tell cron to run the gconf line, nothing happens.

Is there a reason cron wouldn't be able to run a gconf command?

---

### Post by DaithiF on 2011-05-01
> **trpnblies7 said:**
> Is there a reason cron wouldn't be able to run a gconf command?
Yes indeed, gconf relies on dbus environment variables which won't be set in cron's environment.  try the workaround here: [http://ubuntuforums.org/archive/index.php/t-952452.html](http://ubuntuforums.org/archive/index.php/t-952452.html)

---

### Post by trpnblies7 on 2011-05-01
Ah, thank you!

---

