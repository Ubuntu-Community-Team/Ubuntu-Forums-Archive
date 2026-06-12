---
title: "Installing ClockworkMod Tether"
date: 2012-03-16
forum: General Help
---

### Post by FulciLives on 2012-03-16
This is a guide on installing ClockworkMod Tether in Ubuntu.

Some things you need to know:
1.) You do NOT need to have a rooted phone (also works on rooted phones)
2.) The app is free but only full featured for 14 days after which you will have to pay $4.99
3.) This is USB tether. No Wi-Fi tether.
4.) This works regardless of having a tethering plan or not with your carrier (for instance mine blocks tethering unless I pay and yet this method works even though I haven't paid extra to my carrier)

Why this guide? Well I am doing this because I know a lot of people want to Tether to their Android phone using Ubuntu and this seems like a fairly simple program that works well. Having said that there are a few things you need to do to get it installed that I think will confuse some people and so we have this guide.

First you want to download the App from the Android App Store and get it installed on your phone.

Here's a link: [CLICK HERE](https://play.google.com/store/apps/details?id=com.koushikdutta.tether)

You might also want to check out this link: [CLICK HERE](http://qbking77.blogspot.com/2012/01/how-to-get-free-tethering-on-any-phone.html)

I provide those links because they have some information as to where to get the APK file (if needed) as well as some other useful links.

Anyway once you have it installed you need to download the Linux program (which you install in Ubuntu). The app will do this right on your phone (and then you can copy it to your computer via USB connection) or you can use a direct link to download it to your computer directly (assuming you have internet for your computer other than tethering).

Basically you get a file called: tether-linux.tgz

So simply RIGHT CLICK on that to select "Open with Archive Manager" and once extracted you'll have a folder called "Tether" with a bunch of other folders and files under that.

Before you install it though you need to install the OpenSSL development package. I got this using the Synaptic Package Manager. First you have to get that from the Ubuntu Store though. Once you got it simply open it up and then do a search for "libssl-dev" and install it.

Now we can go back to the Tether folder. Click on it and under that go to the folder called "node"

Now you need to open up Terminal and be in this folder. The easy way to do that is to install "nautilus-open-terminal". This package will add a "Open in Terminal" option to the right click menu for a folder. This can be installed by search for it in Synaptic Package Manager.

So now that you are in Terminal and in the "node" folder (or directory) simply type:

```
./configure
```

After which it will do a bunch of stuff. When it is done then type:

```
make
```

After it is done you can exit the terminal.

Now go back to the main folder "Tether" and open up terminal again and type:

```
sudo linux/run.sh
```

Note: Before doing this step make sure that the app is running on your phone and that the phone is connected to the computer via USB

That's it folks. The program starts running in terminal and you are tethered to your phone. Make sure you minimize (rather than close) the terminal window.

Every time you want to do this you have to do the Terminal **sudo linux/run.sh** command as described above. Perhaps there is a way to make a batch file that does this (and thus can be kept on the Desktop for easy access?) ... if so perhaps another could explain how to make it.

Please Note:
1.) This was done using Ubuntu 12.04 Beta 1 (32-Bit)
2.) I am not a very experienced Linux guy. Although I'm 99.9% positive everything I wrote here is correct there might be a mistake. If so please point it out and I'll fix it.
3.) If anyone can chime in on ways to improve my mini-guide please do so.

---

### Post by LincMii on 2012-04-11
Thanks a lot! Helped quite a bit. 

I was installing using a clean 11.10 so one thing that I forgot to do was install build essential to help with the compilers.

sudo apt-get install build-essential

---

### Post by xyzzyman on 2012-04-11
Should I expect any better performance doing it this way? I almost asked about battery life but it's going to be on USB so no worries!

---

### Post by FulciLives on 2012-04-13
> **xyzzyman said:**
> Should I expect any better performance doing it this way? I almost asked about battery life but it's going to be on USB so no worries!
"this way" as opposed to what?

What I mean to say is that I was looking for a solution to tether my phone while using Ubuntu (I already knew how to do this with my Windows install but didn't know how to do it with Linux nor Ubuntu). So I found THIS way and it worked so I made this "mini-guide" to help others.

However this is the ONLY way that I know how to do it.

---

### Post by xyzzyman on 2012-04-13
> **FulciLives said:**
> "this way" as opposed to what?

What I mean to say is that I was looking for a solution to tether my phone while using Ubuntu (I already knew how to do this with my Windows install but didn't know how to do it with Linux nor Ubuntu). So I found THIS way and it worked so I made this "mini-guide" to help others.

However this is the ONLY way that I know how to do it.

As opposed to tethering via wi-fi? I've used Barnacle Wi-Fi Tethering but some devices won't connect to it. I had to buy a better USB cable for my phone (The included one would only charge but wouldn't let me access data on the phone), and I can go into USB Storage mode, but have never tried tethering via the cable.

You are using the term tethering right, correct? [http://en.wikipedia.org/wiki/Tethering](http://en.wikipedia.org/wiki/Tethering) And not just using it as a term for copying files back and forth via USB? Maybe that's the confusion. :)

---

### Post by FulciLives on 2012-04-14
Well my point was that I'm sure there is more than one way to USB tether but this is the only way that I know. At least for USB tethering. I'm sure there are other ways of doing USB tethering but again this is the only way I know and have tried.

I didn't think of wireless tether because my home computer is a desktop and has no wireless internet ability built-in (it is hard wired to my router via an ethernet cord). So basically wireless tether with my desktop (my only computer) is not an option for me.

And yes I am using tethering correctly I just didn't know what you meant by your implication of another way. You didn't say what other way and due to my set-up it didn't occur to me that you meant wireless. I thought you meant some other means of USB tethering (i.e., another tethering program or app etc.)

Sorry for the confusion.

---

### Post by qouic on 2012-07-14
Thank you for that, it was really helpful!
However, i have a problem: everything seems to be working, the app on my phone is displaying "USB tether is running" and the terminal is open and says "phone still connected.." but i can't manage to connect to the internet. I am using ubuntu 12.04, is there something to do extra to the connection settings or something?

Thanks!

/edit/
Actually, problem solved, i don't know what it was but it works just fine now!

---

### Post by calapos on 2012-07-17
if you want to create a file to run this from your desktop go to terminal and type:
```
nano ~/Desktop/tether.sh
```then put this in the tether.sh file:
```
cd WHEREVERYOURTETHERFOLDERIS
sudo linux/run.sh 
```Then you have to make the sh file on your desktop executable, so right click on it and go to properties, then go to the permissions tab and click the radio box at the bottom.
now you can just double click the file, and click run in terminal. It should ask you your password then work like normal
hope that helps people

---

### Post by Kingsley721 on 2012-09-28
I know this topic is SUPER old. But I managed to compile the latest tarball on my Puppy machine.

Can someone give me a pastebin or something of a normal operation of Clockworkmod Tether?

Mine isn't doing much... and I can't figure out how to manage the connection from my computer.

I didn't know where to post this honestly... I couldn't find a thread in a Puppy forum... and I can't find any support documentation from Clockworkmod/Koush...

So this is the best I can do.. My apologies.


edit: I read through most of the 93, yes... 93 readme files in the Clockworkmod tarball.

---

### Post by sedruco on 2013-01-21
I followed your steps and it shows this :  Any help  pleae!! Thankx in advance


rocco@rocco-U56E:~/Downloads/Tether/Tether$ sudo linux/run.sh
[sudo] password for rocco: 
Please compile the included node.js package before running Tether!
cd /home/rocco/Downloads/Tether/Tether/node
./configure
make
rocco@rocco-U56E:~/Downloads/Tether/Tether$

---

### Post by meteorrock on 2013-01-21
Did you make a directory for your program? I have noticed alot of people forget to include that step in drawing up guides or assume one knows about that already. 

```
sudo mkdir /usr/bin/< whatever > 
```

Or it might work trying to put that tether inside of your home folder, which others use this ~ symbol. ~ home/ whatever you named your folder.

Then drag and drop that newly made folder and use the cd command to mount it.

---

### Post by dlw on 2013-03-18
There is no 'run.sh' in /Tether/linux/
There is only an 'adb' binary.

Any help appreciated.

---

### Post by testconfig on 2013-10-17
Instructions are pretty complete, but one thing missing, although minor, is a step to disconnect any current internet connection.  Because most people will have a connection while they troubleshoot their tether issues.

That said, my connection speed **is less than 1Mbps**.  I've already tried rebooting to no avail.  

I'm tethered to a Razr Maxx HD through Verizon, with grandfather unlimited plan, and 4G.  My speed using USB Tether (Azlink) with an original Droid phone (3G?) was 1Mbps.

Edit:  I also tested the phone's speed by itself and the results were dramatic:  **10.32 Mbps** download,   **13.93 Mbps** upload.  Test site was [www.bandwidthplace.com](www.bandwidthplace.com).

---

### Post by mcgill.carpenter on 2013-11-22
Followed this and I can get web pages to load and everything, but I can't seem to use it for anything else. Like Updates or getting anything from the Ubuntu Software Center. Those things tell me to check my internet connection. Which doesn't surprise me since the networks icon also says I'm not connected to internet. Did I do something wrong, or is this normal?

---

