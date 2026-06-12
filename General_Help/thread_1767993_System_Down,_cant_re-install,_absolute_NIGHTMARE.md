---
title: "System Down, cant re-install, absolute NIGHTMARE"
date: 2011-05-26
forum: General Help
---

### Post by iclestu on 2011-05-26
Ok - I made the mistake of trying to fix a tiny little glitch that never bothered me.... Now I have no system! Make matters worse, I cant get the Live CD to work properly (it boots fine but no network access)

I tried removing gnome. See [U][this thread]("http://ubuntuforums.org/showthread.php?t=1767146")

[/U]Now I cannot boot into Kubuntu. Grub appears and then a kubuntu splash screen but the signal to the monitor dissapears shortly after. I tried to go into recovery and boot to failsafe graphics but that doesnt work either. I tried manually to run ```
xstart
``` but it doesnt work (not that i know what I am doing with that).

Eventually, cutting my losses i decided to bang in the live cd and see if i can fix/install from there....

Ouch Live CD cannot access network. It is a WIRED connection and connect fine when i boot into safe mode from hard drive! Eth0 does not show under manage connections when operating from live cd and if i disable the re-enable networking it goes thru the motions for a min or two but hangs at setting network address before giving up and reverting to 'not connected'

Please great gurus of the Linux world, help me get back on my feet and i promise I wont try and fix any more minor glitches again! 

Please help guys.

Many Thanks

---

### Post by 4Orbs on 2011-05-26
Have you tried turning the monitor off and back on when the screen goes blank?

---

### Post by iclestu on 2011-05-26
yes I did. Tho having mucked about at the command line i now cant recreate that original state

Id settle for a means to get netweoking up in the live cd. dont mind re-installing now i got to this stage. Got all my files on netbook anyways so no biggie to reinstall.....

Thanks for the reply tho....

---

### Post by dragonfly41 on 2011-05-26
I had been tinkering with my dual boot configuration after having some problems with a drive. I found that I could not get wired Internet connection so I'll suggest some ideas which worked for me.

(1) Try turning off the power to your cable modem and leaving for about 30 seconds before turning on power again.  This may reset your IP address.

(2) Open Preferences > Network Connections and under "Wired" tab edit select "Auto eth0" and then in the popup window click on "Apply".  After a password - "System Policy prevents modification of system setting" this reset my network connection.

---

### Post by iclestu on 2011-05-26
> **dragonfly41 said:**
> I had been tinkering with my dual boot configuration after having some problems with a drive. I found that I could not get wired Internet connection so I'll suggest some ideas which worked for me.

(1) Try turning off the power to your cable modem and leaving for about 30 seconds before turning on power again.  This may reset your IP address.

(2) Open Preferences > Network Connections and under "Wired" tab edit select "Auto eth0" and then in the popup window click on "Apply".  After a password - "System Policy prevents modification of system setting" this reset my network connection.

Re (2): No Auto eth0 appears....... can get access to router settings through netbook and it doesnt 'see' my main computer

---

### Post by 4Orbs on 2011-05-26
When you boot into the livecd, select the option to try Kubuntu first. When the desktop finally loads click on the network icon and select the "Show More" button which should then give you the ability to connect to internet. Then (assuming you are able to connect) you can click on the "Install" launcher.

---

### Post by iclestu on 2011-05-26
show more doesnt do anything.... There are no connections listed....

---

### Post by dragonfly41 on 2011-05-26
Try these commands to inspect connections ..

sudo ifconfig

sudo lshw -C network

---

### Post by oldfred on 2011-05-26
If you can get to command line and get Internet you can just try updating/reinstalling.

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove kubuntu-desktop 
apt-get install kubuntu-desktop

---

### Post by iclestu on 2011-05-26
got it! Not quite sure how!

sudo ifconfig

sudo lshw -C network

Lol - did those commands, looked again at router details on netbook and there it was... (it wasnt there before!). No idea whats happened - those commands dont DO nything, do they? they just show the state of things? no?

Either way, I am ever so grateful. On with a fresh install now! Wish me luck.

Many Thanks for your help guys. Remember if you get an annoying flicker when you come out of your screensaver and you can live with it. LIVE WITH IT! Lol Thanks again

---

### Post by iclestu on 2011-05-26
> **oldfred said:**
> If you can get to command line and get Internet you can just try updating/reinstalling.

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove kubuntu-desktop 
apt-get install kubuntu-desktop

Oooo oldfred. Thanks I really would have tried that... Just a fraction too late - installation in progress now... Wish I had hung off a second.

Thanks v much though

---

### Post by iclestu on 2011-05-27
well back fully operational now. Reinstalled no probs once got network up and running and it happily saved all my home folders and settings (windows doesnt do that on re-install does it!? ;-) ).

Nice to know I have a clean pure KDE install. Still got no idea what went wrong with that command nor what was wrong with my network on the live CD but I am grateful for your suggestions and just pleased to be back up and running... 

Now that Kile is back, I no excuses left for avoiding my maths assignment ;) ! 

Thanks again folks :)

---

