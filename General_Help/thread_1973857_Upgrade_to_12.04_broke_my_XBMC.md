---
title: "Upgrade to 12.04 broke my XBMC"
date: 2012-05-05
forum: General Help
---

### Post by YfoMp5QBh2 on 2012-05-05
Hi All,

I'm having awful trouble trying to run XBMC on 12.04 precise. It loads up but the menus take 2-3 seconds to react to a keypress, needless to say its utterly useless now.

I have upgraded from 11.10 to 12.04 64bit and XBMC has since stopped working. The graphics card is NVIDIA 6150 LE. The current driver is 295.40.

I am absolutely desperate to get it working properly again can anyone help me out? I do not want to have to downgrade to 11.10

Kind Regards,
SPADGE_2356

---

### Post by kazztan0325 on 2012-05-05
Hi spadge_2356,

Have you installed the latest version of XBMC?

If not yet, please refer to following web page and try to upgrade XBMC, and then see if it would work well.

**"INSTALL XBMC ON UBUNTU 12.04 PRECISE PANGOLIN"**
[http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html]("http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html")

---

### Post by YfoMp5QBh2 on 2012-05-05
> **kazztan0325 said:**
> Hi spadge_2356,

Have you installed the latest version of XBMC?

If not yet, please refer to following web page and try to upgrade XBMC, and then see if it would work well.

**"INSTALL XBMC ON UBUNTU 12.04 PRECISE PANGOLIN"**
[http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html](http://www.noobslab.com/2011/12/install-xbmc-on-ubuntu-1204-precise.html)

Thanks, but I am already running Eden.v11. Unless theres another one been released I'm not aware of?

---

### Post by Maverickprowls on 2012-05-09
Looks like this thread [http://ubuntuforums.org/showthread.php?t=1976109]("http://ubuntuforums.org/showthread.php?t=1976109") has some useful information.  There's a known bug with the nvidia 295.X drivers for older cards.

I've removed all the proprietary drivers from my new install and am using the nouveau driver instead (your system will fall back to this if you remove all the official drivers).  It's still not as fast as my previous 11.10 install was, but reading the bug-thread suggests that this is fixed in 12.10 and will be fixed in 12.04 soon.  Here's hoping, I miss my XBMC

---

### Post by YfoMp5QBh2 on 2012-05-10
> There's a known bug with the nvidia 295.X drivers for older cards

I tried all variations of the 295.x drivers with varying results, in some cases speed increased slightly, in others I just got the black terminal screen instead of gdm. I found 295.33 worked the best but it was still unusable really!

> **Maverickprowls said:**
> this is fixed in 12.10 and will be fixed in 12.04 soon.  Here's hoping, I miss my XBMC

Me too buddy! So much that I did a clean install of 11.10, re-installed XBMC and LIRC on all my machines! Now there's a weekend of my life I'll never get back. Oh well I missed dodge when they removed it from the Unity menu anyway so now I have that back at least :P

Hopefully they will get the bugs out, and I'll be able to upgrade without any snags but for now I'm keeping with 11.10 for as long as possible. Its stable at least for now.

---

### Post by hodowany on 2012-05-12
Just a quick update. I had exactly the same issue with nvidia GeForce 7100 using driver 295.40 with xbmc in Precise 12.04. 

As suggested above, I added the precise-proposed package archives into sources.list.

The proposed nvidia driver is 295.49, and is installed with nvidia-current-updates. After installation, at least for me, it worked like a charm. xbmc on ubuntu 12.04 has been rescued

---

### Post by YfoMp5QBh2 on 2012-05-15
> **hodowany said:**
> The proposed nvidia driver is 295.49, and is installed with nvidia-current-updates. After installation, at least for me, it worked like a charm. xbmc on ubuntu 12.04 has been rescued

That's great news hodowany! I noticed they released 295.49 just after I created this thread. I have tried installing them, but it didn't solve my problems? Perhaps I neglected to install nvidia-current-updates afterwards? Did you install via the terminal or through synaptic?

If I feel brave enough I'll try upgrading again at a later date, but for now thankfully, my installation of XBMC is stable with Ubuntu 11.10

On a separate note....loving the new look of the forums! :p

---

### Post by mistergoomba on 2012-05-24
I'm having a similar problem. My latest update brought me to 12.04 and also updated XBMC to v11. When I first opened XBMC, it was stuck after the splash screen on the Videos tab of the Back Row theme. I assumed that maybe it was some add ons or the theme, so I renamed the add ons folder and the guisettings.xml file and let it use default values. Now, it just sticks on the splash screen, even if I change the add ons folder and guisettings.xml back to their original names.

My nvidia-current-updates is up to date, as well as nvidia-current

Any help would be greatly appreciated. Seems I can never upgrade without XBMC freaking out.

---

### Post by mistergoomba on 2012-05-24
> **mistergoomba said:**
> I'm having a similar problem. My latest update brought me to 12.04 and also updated XBMC to v11. When I first opened XBMC, it was stuck after the splash screen on the Videos tab of the Back Row theme. I assumed that maybe it was some add ons or the theme, so I renamed the add ons folder and the guisettings.xml file and let it use default values. Now, it just sticks on the splash screen, even if I change the add ons folder and guisettings.xml back to their original names.

My nvidia-current-updates is up to date, as well as nvidia-current

Any help would be greatly appreciated. Seems I can never upgrade without XBMC freaking out.

I just reinstalled XBMC and it's working fine. Must have been an incompatibility somewhere

---

