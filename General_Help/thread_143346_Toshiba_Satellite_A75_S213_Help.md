---
title: "Toshiba Satellite A75 S213 Help"
date: 2006-03-12
forum: General Help
---

### Post by viniciuscarvalho on 2006-03-12
Hello there! I'm one of the idiots who bought this junk notebook from Toshiba. After trying eight distros (Suse, Red Hat, Fedora, Debian, Kurumin, Kubuntu & Ubuntu) the only one who installed properly was Kurumin. I was able to install both Kubuntu and Ubuntu with special parameters (vga=771 noapic nolapic). 
Well recently I had to format the HD. And now, I don't know why, I can't get Ubuntu to install. I've tried the default no parameters install. Also with parameters above, It's always the same, it starts to uncompress the kernel, Then, (it's so fast I can't see the messages :( ) the last message I see is something about buffer, then my screen goes black, no HD activity, no CD reading, nothing, it stays blocked for minutes if I let it that way, nor even the keyboard responds, letting the only way to restart is pressing and holding the power button.

Please if someone cares, I'd love to dump my crappy windows and come back to use a linux distro. Now I don't have enough money to dump this piece of crap notebook, but soon I'll change it for a real one, who could support linux :)

Best Regards


PS: My notebook configuration:

P4 3.33 HT
1G Ram
Mobile ATI Radeon 9200 (crap) with 128 shared memmory
15,4" Screen

---

### Post by njzillest on 2006-03-12
same problem happend to me, when the screen went blank. 

Im using a toshiba R/10 (yeah it is pretty sh!tty) with about the same specs. 

i reisntalled ubuntu with a different disk, my problem was i burnt the disk way to fast. make sure when you burn the disk its at 4X or less. Also try to re download the ISO file, sometimes it wil  be inturepted during the download process



hope this helped :)

---

### Post by viniciuscarvalho on 2006-03-12
Well I have the original Ubuntu CD. Do you have any clue why this happens? could this be a X11 problem?

Regards

---

### Post by njzillest on 2006-03-12
try to burn it your self. ive read in other posts that the ubuntu Cd's dont allways necessarly work..


just download the ISO and burn the image file using nero, roxio, or some other freeware burner. 




for good free or trial burners go to [www.download.com](www.download.com)

---

### Post by patrick87 on 2006-03-12
make the cd yourself man.. i made 5.1 last night for myself..  my cd that was an actual ubuntu 5.04 cd had files missing.. and only got through 6% of install before failing. If you have a good internet connection.. its best, because it took about an hour to 30 minutes..wasnt paying attention really.. to download the iso from the site..download a good burning program..and make the cd.  THIS CD WORKED LIKE A CHARM. So that could be your problem. 

As far as the Toshiba's go. They are set up to work with linux, some! If you go to walmart and buy one.. dont expect it to be the greatest toshiba laptop, those are their lowest model ones. My dad is a Registered Toshiba Dealer... and the Tecra's seem to be the best.. Tecra's run linux based programs jus fine.

---

### Post by viniciuscarvalho on 2006-03-13
Well, what's odd is that I've already had an ubuntu installation from ubuntu's disk on this machine (it was a hard one but I could get it to work). So Yesterday I've followed patrick's advice and burn my own image, no success either.

As I said I had my HD formatted but I have an unfinished Suse 10 installation (unfinished cuz it installed ok, just not boot unless failsafe mode) 

It uses Grub 1.5, I was wondering if these could be the problem. I'm affraid of formatting the reiser partition (using Partition Magic) and mess up good with the boot loader.

Any suggestions please?

Regards

---

### Post by outlawtanker on 2006-03-13
I haven't seemed to have any problems with any distro except the Debian pure distro, and also Red Hat, I also have a A75, I'll admit, there are a few problems, but it hasn't been too bad to me.  My DVD burner crapped on me. Have you tried just a very basic install and building from there?

also, Slackware ran pretty good for me too, although there's a lot of configuration.

---

### Post by njzillest on 2006-03-13
reformatt your whole disk, or the unleft linux partitions. make it into "free space" and then format it to ext 2 or 3. make a linux swap (if you have 512 ram then all you need is 512 swap but if you have 16 mb of ram then youll need 64-128 mb of swap) install ubuntu to the MBR and install suse on a SEPERATE PARTITION to the MBR where it will boot of the partition. usually it will have a seperate step explaining you everything


hope this helped

---

