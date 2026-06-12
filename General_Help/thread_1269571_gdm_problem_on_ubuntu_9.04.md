---
title: "gdm problem on ubuntu 9.04"
date: 2009-09-18
forum: General Help
---

### Post by ashkan.ekhtiari on 2009-09-18
Hello,

I use ubuntu 9.04 juanty on my laptop. I deleted some files in /tmp by mistake, and also removed eclipse and related packages from applications->add/remove.
After that when I restarted in order for changes to take place I encountered an error:
"GDM user gdm doesn't exist, please correct configuration and restart gdm"

I am not able to log in though, So I tried by Live CD, and tried variety of solutions which I found on forums, like :

sudo apt-get --reinstall install gdm
sudo shutdown -rn now

it shows just a black page

sudo dpkg-reconfigure gdm
sudo reboot

didn't work

  gdm files exist in  /var/lib/gdm , they are 0.Xauth  :0.Xservers

  sudo service gdm restart   /// goes to black page and does nothing

I really need my installed and configured programmes not to be distryed.
I am in process of my master thesis work and did a lot, now all of my configured programms and data could be lost.

I backed up the whole ubuntu drive into an external disk, but I want to recover my system, some of configurations may take so much time to repare and it's out of deadlines for me.

If anyone has a solution to my problem please infrom me.

Thank you in advance

---

