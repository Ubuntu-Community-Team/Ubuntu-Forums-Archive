---
title: "ndiswrapper is not working properly, have I installed it wrong?"
date: 2006-02-26
forum: General Help
---

### Post by iteyoidar on 2006-02-26
I am trying to connect to the internet on a broadcom wireless card.

I couldn't can't connect to the internet with a cable(other reasons that have nothing to do with Kubuntu), but I found another message that explained how to install ndiswrapper offline, that linked to the files I need.

I installed ndiswrapper

I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+broadcom](http://ubuntuforums.org/showthread.php?t=25683&highlight=ndiswrapper+broadcom)
my light never lighted up like it was supposed to, and wlan0 does not show up on the networking window so I can't select it.

I also tried using that scan command on wlan0 and it doesn't do anything either.

I can't even find that message about installing ndiswrapper offline anymore, but I wonder if maybe the ndiswrapper files that I installed with were outdated or something, is there anyway to tell what is going on?  Or is there anyway to just start all over with everything?  I've run so many commands I don't know if I've completely screwed something up or what :(

Also, ndiswrapper -l says that my driver isn't valid

Assuming I did install the wrong version(I suspect I installed like, version 1.1):

1.  How do I fix everything an uninstall ndiswrapper?
2.  I want to download the files for the latest version onto my drive from windows and then install them, how can I do this?

---

### Post by msak007 on 2006-02-26
I'm a linux n00b myself (I've only been using Kubuntu a month now) so I may not be much help, but I got my Broadcom wireless card working. I'm using a Linksys WMP54G, which uses the BCM4306 chipset, so if you are as well I might be able to help you out a little bit more. Also, are you using any encryption in your router? WPA is harder to set up than WEP as it isn't supported natively and requires wpasupplicant.

I'll answer question #2 first. As far as getting your drivers from Windows to your Linux partition, there are several ways to do this. The first is editing your fstab so it'll automatically mount your Windows partition at boot-up. This will allow you to browse to the partition and read from it (no write capability yet unfortunately) so you can copy the files over to your Linux partition. [This thread]("http://ubuntuforums.org/showthread.php?t=133362&highlight=ntfs+read") should help you out, but there are plenty of others in the forum about mounting NTFS partitions. I assume that's what your Windows partition is as that's the default file system, but if it's FAT32 you can search for that and you'll find the answers as well. The second way is doing it from Windows, as I had to because my Linksys driver was a .exe and I had to use WinRAR to extract the contents first. It requires use of [Ext2 IFS]("http://www.fs-driver.org/") - it's a free util that lets Windows read / write to ext2 / ext3 partitions. I've had success with it, and used it to test whether or not my Windows partition would be able to write to my Linux partition before I took the plunge and stopped using Windows. I had to verify this first as I'm sharing some partitions with Windows users on the network and wanted to give them the ability to read / write to ext3 partitions. But anyway once you've set that up and can see your Linux partition, you can download the correct driver from your card's manufacturer then extract it to a directory on your Linux partition (for example, on your Desktop). That's how I did it anyway, but there may be better / more efficient solutions out there. That leads to question #1.

[This wiki]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") helped me out tremendously in getting my driver set up. There are numerous sources out there, including on this forum. I didn't have success following the thread you linked to so I had to look elsewhere. If you followed it verbatim, that may be the problem as my card uses WMP54GSa.inf, not bcmwl5.inf - knowing which card you're using is key. 

What does "ndiswrapper -l" output? If it lists a driver, but says the hardware isn't present, type "sudo ndiwsrapper -e <name of driver>" to uninstall it, then follow the instructions in the wiki to install the correct driver.

Sorry if this reply is a little verbose but I hope it helps nonetheless. Like I said I'm pretty new to Linux myself and there are many people in the forum more knowledgeable than I am in that respect, but I'll try to help out anyway.

---

### Post by iteyoidar on 2006-02-26
Thank you for your reply.  

The wiki link actually seems to be what I attempted earlier.  I can get the driver file from windows.  I do everything like the link says.  Then it tells me to input the command 

ndiswrapper -l

which outputs a bcmwl5 not valid! message and a second very similar message.

The reason I wonder about the version is because I used ndiswrapper on the knoppix live CD and it worked perfectly, loaded up my driver, and I could connect to the internet.  So I wonder if there is a newer version of ndiswrapper than the one in that link, or if I installed mine wrong.

On what seems to be the official ndiswrapper page: [http://ndiswrapper.sourceforge.net/](http://ndiswrapper.sourceforge.net/) the latest version seems to be 1.10.  The file on the wiki link says ndiswrapper-modules-1.1, does that mean it is version 1.1?

I tried installing the 1.10 originally, I was able to decompress it, but then I got to the compile and install part where it said to do the commands
make distclean
make install

and linux didn't even recognise the "make" command..

---

### Post by msak007 on 2006-02-26
The fact that it says "bcmwl5" is not valid leads me to believe that you installed the driver per the thread you linked in your post. Like I said, I had to use a different driver for my card and you may need to as well. Find out which card you're using and which driver is required, and you can take it from there. You can uninstall that driver you have installed first by typing "sudo ndiswrapper -e bcmwl5". Then install the driver your card needs.

---

### Post by iteyoidar on 2006-02-26
bcmwl5 is the right driver, it's the one installed on my computer for windows as well.  I also tried searching on the page for an alternate driver with the same pciiid.  It was also invalid.  On Knoppix, when I loaded that same driver it worked perfectly.

Does this mean I need a different version?

---

### Post by msak007 on 2006-02-26
I'm not sure what the problem is then because I didn't use that driver. Is it a generic Broadcom driver for all Broadcom chipsets? You also still didn't mention which card you're using. You might want to try a driver specific to that card. I've never used Knoppix, so I can't tell you why it worked there and not with Kubuntu. Sorry if I'm not much help.

---

### Post by iteyoidar on 2006-02-26
Yay! :) I got it all working, my main issue was that I didn't copy all of the driver files into the folder I was using them from, I had only copied the .inf file. 

One issue though, I couldn't get into the admin mode on the wireless configuration because it wouldn't take my password, for some reason.   I found something else on the message boards about what to type in the terminal to get it working, but now every time I want to connect to wireless I have to type something like

sudo su
modprobe ndiswrapper
ifconfig wlan0 up
iwconfig wlan0 essid []
sudo dhclient wlan0

can I just make it do this on startup somehow?

---

### Post by aldegaz on 2006-06-09
sudo ndiswrapper -m

that should make ndiswrapper load from the beginning

---

