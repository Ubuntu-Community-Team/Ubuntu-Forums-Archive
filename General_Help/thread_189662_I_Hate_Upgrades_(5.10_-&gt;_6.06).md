---
title: "I Hate Upgrades (5.10 -&gt; 6.06)"
date: 2006-06-05
forum: General Help
---

### Post by Dauphinfay on 2006-06-05
Ok. I ran the graphical upgrade and all hell broke loose. After taking only an hour and a half to run the upgrade it asked me whether or not I wanted to keep my original login script. I accidently closed the window after clicking on the terminal triangle to see what the differences were...so I didn't answer the question. Then it restarted the whole process but said it would take 7 hours. In anycase, after rebooting I have got nothing more than a broken box. I managed to reconfigure the gdm but gnome is down. But more important than that is that I can't get my wireless card to work. ifconfig ath0 brings about an error that goes like this: error fetching interface information: Device not found.  ](*,) 

1) is there anyway to fix the wireless so I can get back to restarting this upgrade?

2) would downloading and burning the new dapper cd allow me to upgrade without losing my whole system?

As always, tahnks in advance everyone.

---

### Post by S{yndrom}e on 2006-06-05
ouch canceling during an update.

Anyway there is hope mabey. When you installed ubuntu, did u set up ur /home on a seperate partition? if so u can use the install disk to format/install a new ext3 primary "/" partition over the old "/" partition and that should fix it. You will have to reinstall all the programs, but "data" in the home folder (i am assuming u used it for data" will be intact

However if your partition table looked like

Primary Partition "/"
Swap

Then you most likely have to do a clean install. Actually there *might* be a way. Some one more advanced in partitioning could say if this is possible. You insert the ubuntu live cd, mount the linux drive (and since only gnome is broken the data should be intact), backup data and the do a clean install.

Hope i helped

---

### Post by Dauphinfay on 2006-06-05
Unfortunately, it is on the same partition. I used a kanotix cd to go and get madwifi but it appears that I can't get it untar'd. is there a way to use a live cd to repair what I need to here?

---

### Post by Ramses de Norre on 2006-06-05
Redoing ```
sudo aptitude update && sudo aptitude dist-upgrade
``` might solve this, or ```
sudo apt-get install -f
``` or ```
sudo dpkg --configure -a
```

If none of them help I'd use a live cd to back up your data and then do a reinstall..

---

### Post by Dauphinfay on 2006-06-17
No dice with anything suggested. I also went back and downloaded dapper and burned to a CD and tried that. It appears that everytime I attempt to burn a copy of dapper and install it something is wrong with either the checksum or some other broken file because I just can't get an install. The closest I got was when I tried to install the server version. Nonetheless, I downloaded another version of linux just in the off case that it was something with the way my hardware is burning. No probs downloading and burning Damn Small Linux or Kanotix. I am about to jump ship if I can't get this by the end of the weekend. I can't afford to keep screwing around with this. Thanks for the help folks but I'm not quite out of the woods yet.

---

### Post by Computeruser on 2006-06-17
Your download may be bad. I upgraded from Breezy to Dapper, and for me, the upgrade was like any other upgrade in any other OS - bad. I downloaded Dapper to disk, started a new machine with the ISO file, and it all worked. I have issues with VMware Tools that I cannot resolve; otherwise, Dapper is running OK. I like Breezy better at this point, but I have a Dapper machine and will give it a fair trial.

---

