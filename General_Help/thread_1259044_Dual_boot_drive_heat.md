---
title: "Dual boot drive heat"
date: 2009-09-05
forum: General Help
---

### Post by Diluvial on 2009-09-05
Ok, so I have an 80 Gig Western Digital HDD that's really, really old at this point, but still runs fine. It has an installation of Windows XP Pro SP2 on it. Now, I recently got a 1TB Samsung HDD for a linux installation (Ubuntu Jaunty to be specific). So now I really only ever boot to Windows to play games. I've dual booted before, but always from partitions, never two seperate drives. The problem I'm having is that when I boot into Ubuntu, the 1TB drive is relatively cool. Really average operating temperature. However, when i boot to Windows, the Samasung drive gets really hot. Now my friend, who is significantly smarter than me, especially in the ways of computers, has never heard of this. His theory is that the samsung drive is never spinning down after boot, when it spins up to run GRUB, even though it's not being accessed. Neither of us could find a similar problem, or solution on Google. Has anyone heard of this, or have any suggestions for fixing it? Please tell me if I left out any specifics that could be helpful. I really couldn't think of anythign specific taht might be causing this.

---

### Post by JC Cheloven on 2009-09-05
As you pose the question, this is more a windows question, as it is under windows where the problem appears. Anyway, to cope with HD heating FROM LINUX, I'd suggest to install smartmoontools  (it is in the repos).

Once installed, smartctl -a /dev/sda  gives a lot of information:

Power-on-hours (hours of HD power on, in all its life) 

Load-cycle-count (times the head has been parked, 600000 times is considered the average lifetime of an HD). The more you park the heads, the less heat it will generate, but you'll reach the 600000 times quicker.

A ratio of about <15 per hour is considered fine for a laptop. For a desktop there is no need of much parking (no posible shaking of the pc), but if you experience heating problems, you can consider to park often.

hdparm -B 254 /dev/sda &#8594;  Disables the head parking (in some systems it's 255). Could be a desirable setting in general, but you don't want this in your case. Try with a slower number (sorry, I remebmer it wasn't obvious which value is ok, but  can't remember such a good value).

You can control the HD temperature with smartctl -a

If you want the hdparm settings etc to be permanent, ie to apply at every boot, you have to make a simple .sh script and storing it in several places at /etc/acpi/. More details at  [http://ubuntuforums.org/showpost.php?p=5031046&postcount=3](http://ubuntuforums.org/showpost.php?p=5031046&postcount=3) 

Hope this helps.

---

