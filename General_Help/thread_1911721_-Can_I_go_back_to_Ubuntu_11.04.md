---
title: "-Can I go back to Ubuntu 11.04?"
date: 2012-01-19
forum: General Help
---

### Post by labtek on 2012-01-19
Hello to the group and good day.

A few days ago, in a moment of weakness, I upgraded from 11.04 to 11.10 and am very unhappy with what what I'm now seeing. As a Linux and Ubuntu user for many years, I usually research what the new version looks like before committing to it.

The issues associated with 11.10 have been spoken about in the forums by others so it's not necessary to go back over old ground.

I'd like very much to return to 11.04 but I would like to save as much information as I can (bookmarks, stored passwords, etc) that I had with 11.04. I can back up Evolution and restore it to a fresh install but am uncertain if much else can be salvaged.

Any suggestions of how to re-load 11.04? Thanks in advance for any help.

---

### Post by kc1di on 2012-01-19
Hi,
if you have a seperate home partition you can re-install 11.04 without formatting that partition , it holds all your personal data.
if you did not make a separate home partition the only thing you can do is back up all that you want to save and re enter it after you've installed 11.04  you could use Ubuntu One to store the info on if you want.

Good luck,

Dave

---

### Post by Frogs Hair on 2012-01-19
Sorry to write that down-grades are not possible . You will have to backup your data and preform a clean installation of 11.04 . You can export browser bookmarks and save them as a document , but I am not an evolution user and don't  if exporting contacts is possible . Any new releases you have interest in future you may want to test from a live cd before installing .  I have had no problems with 11.10 but I was aware it was going to be quite different 11.04 when I installed .

---

### Post by raja.genupula on 2012-01-19
Downgrade not possible , take your home directory as backup is the best i think . 

but i have read one point in forums . make a /home partition and  / partition at the time of installation . this current home partition which you have taken as back up , place this thing at the partition of /home . i mean replace the new one with old one . 

but i havent tried this , so i am not sure about it . but its not going to give any loss . so try it . dont forget taking your home folder as back up .

all the best.

EDIT : @kc1di i did late post , so i haven't seen your post . sorry man . we have similar information .

---

### Post by Scott Baker on 2012-01-19
Regarding Evolution, it does give you the opportunity to back up your settings (it's located in the "file" section of Evolution). Now, on to a question. Labtek, what is it that you dislike about 11.10. The 11.10 version is now pretty smooth, with a lot of the hiccups gone. If you'd share what's actually making you crazy about your upgrade, someone may have a suggestion that will save you the grief of having to go through the trouble of reinstalling 11.04. Good luck, and keep us up to date.  :lol:

---

### Post by labtek on 2012-01-19
Many thanks for the helpful posts. The information offered is pretty much as I had expected.

I guess I will try to live with 11.10 for awhile before I abandon it while in the meantime trying to transfer as much as possible to recordable media.

Military types would refer to it as an "orderly retreat" rather than surrender.

---

### Post by labtek on 2012-01-19
Scott Baker- thanks for the post.

I particularly do not like the graphic tool bar on the left side of the screen. Also, when I minimize an application, it disappears back to the tool bar and I don't know what is open but minimized or not openend at all.

Perhaps there are workarounds for these "aggravations" or something that I'm missing but it seems such a step backwards from 11.04, which I thought was very smooth working and user friendly.

To my mind, 11.10 is intended for Ubuntu newbies with it's emphasis on graphics.

All the more reason to research new distros before blindly embracing them.

---

### Post by jerrrys on 2012-01-19
I don't see it mention.  For a old style look (gnome2) you can install gnome classic.

sudo apt-get install gnome-session-fallback

---

### Post by kc1di on 2012-01-19
> **labtek said:**
> Scott Baker- thanks for the post.

I particularly do not like the graphic tool bar on the left side of the screen. Also, when I minimize an application, it disappears back to the tool bar and I don't know what is open but minimized or not openend at all.



If you want you can install gnome shell and it does allow you veiw all apps you have open though it stills has the left panel , don't know if that is movable yet. 
Also I believe you can install Mint's Cinnamon desktop which has a bottom panel.

Cheers,
Dave

---

### Post by Lars Noodén on 2012-01-19
Xubuntu is also possible, it's become much more popular lately because of this.  It has a much more traditional interface.

---

### Post by labtek on 2012-01-19
Therein lies the versatility of Linux...no matter what your particular tastes are, there is always a distro for you.

Thanks to all who posted.

---

### Post by Scott Baker on 2012-01-19
Here's one more for you;
sudo apt-get install gnome-panel. Once installed, log out. When you get to your log in screen, click the gear next to your name. You should now see the option to change for the Unity based screen to the classic. This is what I use on my laptops, and haven't experienced any issues with it. [-o<

---

### Post by kc1di on 2012-01-21
Someone asked me how to install Cinnamon on Ubuntu you can do a google search and there are several. pages that explain how to.

or you can go here and download and install the .deb package. I've tried it both ways and they both work.

[http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/]("http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/")

---

