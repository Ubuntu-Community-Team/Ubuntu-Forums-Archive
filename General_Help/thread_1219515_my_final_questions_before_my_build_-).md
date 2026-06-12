---
title: "my final questions before my build :-)"
date: 2009-07-21
forum: General Help
---

### Post by InkedScales on 2009-07-21
Hi guys, I did make a post a while ago and the responses I got where very helpful, I havnt been looking into this for awhile as I have had alot of things on but now I'm ready to get going with it but there are a few things i need to double check and finalise before I go ahead.

firstly I have been made aware that most programs I am used to useing I can either use or there are similar ones for linux however If I need to use any I can run a "virtual desktop"? is this correct and if so how?

secondly I use my pc mostly for watching movies on my HD tv as my second monitor output, is dual monitor output possible if so how do I set it up as im used to the display settings of vista, and also what media players do people recomend as I use media player classic as it works well and has all the built in codecs for the mkv files etc I use.

someone asked me to put up what hardware I have so everyone can help to spot any issues I might have with drivers etc, my only problem is I dont have the boxes anymore so Im going on what it says on the disks which dont give me any real info like the card name etc... all I know is I have a fatality motherboard intel core2 quad CPU Q6600 @ 2.40GHz  4 GB RAM,  and from the disk ASUS VGA graphics card, X-Fi soundcard also again dont know what I would need to look into for drivers I have microsoft lifecam 1.4 software i need to install somehow :S and I have a logitech wireless mouse and keyboard the disk says setpoint 4.0

the webcam reminds me can I use msn in linux, or is there another similar program that I can use my msn address in??

is there a linux version of office also someone said theres a similar program to photoshop called gimp?? is this very similar, completely different or can it do all the same stuff just ina  different way?

I also use Utorrent, on a site I use for torrents they only allow members with certain bit torrent clients 

Here's the new list of allowed versions:
  *  Azureus 3.0.5.2, 3.1.x, & 4.x
  * BitTornado 0.3.17 & 0.3.18
  * KTorrent 2.2.8, 3.1.6, & 3.2.x
  * rtorrent 0.7.x & 0.8.x
  * Transmission 1.5.3, 1.61, 1.7.x
  * µTorrent 1.8.2, 1.8.3 stable, & 1.9 alpha
  * µTorrent Mac 0.9.1.2 (build 15399)

are any of these available in linux??

also I have a printer which is abit old so not sure if this will be able to be installed, its an epson stylus CX3200, if it can be installed I was going to find out how to network it so that my mum can use it via her laptop even though its on my pc, 1. can I set up a printer on a network if Im on linux? 2. will this still wor as Im on linux but my mum is using Vista? 3. will the two different OS's cause any problems with the normal network? (as in will my mum still be able to use the WiFi, I cant see why she couldnt as the router doesnt have an OS obviously but I had to ask)

also from what Ive read in these instructions to install ubuntu it appears that all your HD space is allocated as one even if you actually ahve seperate gard drives... am i reading this wrong??? Im sure Ill ahve to get used to the new set up for the HD's but is there anything at all that people think I shoudl know that may cause me problems before I start? (except backing stuff up as I already have a TB external with all my files on :-) )

oh one last thing I think I use winamp on my pc normally is this available and if not what music players do people use and can I use itunes in ubuntu? if not for that one is the virtual desktop a way of using .exe files as I really need to use itunes as I have an ipod and need to change the songs etc.

anyway thanks so much for everyones time 

I cant wait to get the answers I need to I can join you all in the land of Ubuntu :D

---

### Post by ecmatter on 2009-07-21
Transmission is on the Live CD.

The best way to test if your printer will work is to boot up the live CD, connect the printer, and try to print something.  I've never had anything, other than my sound card, that didn't work as soon as I plugged them in.

---

### Post by 3rdalbum on 2009-07-21
Okay let's try and answer as many of your questions as possible.

Some Windows programs can be made to work with some software called Wine, but this is very hit-and-miss. You'll enjoy your Linux experience much more if you try to use as many native Linux programs as possible.

Another option is to run Windows inside a "virtual machine", which will run Windows programs perfectly (if a little slowly). I'd still say, try and find Linux equivilant software wherever possible.

Dual-monitor is indeed possible in Ubuntu, but I have no idea how it's done these days.

Ubuntu comes with a media player called Totem, but you'll need to install extra codecs for it (Ubuntu purposely comes with only codecs that are open-source and not patent-restricted). When you try to play a file that you don't have a codec for, the system will ask you if you want to install the codec. Easy.

Most people will tell you to install VLC on Ubuntu, because it's an excellent video player and can play almost anything.

The system information you provided isn't terribly helpful... if you had model numbers, that would be fantastic. The CPU isn't a problem, of course. Asus makes ATI and Nvidia graphics cards so I don't know which you have. ATI cards will work, but under Linux they are nowhere near as good as Nvidia cards.

Your X-Fi sound might be an issue; Creative has no idea how to write Linux drivers and as a result the official X-Fi driver was absolutely shockingly bad. Now it is open-source, the community is improving it, but you may come across problems. If this is a discrete sound card, it might be an idea to try using your inbuilt motherboard audio, at least until things improve.

You generally don't need to search around for drivers; Ubuntu pretty much comes with everything you need in that regard, or will be able to download it on-demand. I have no idea about the Microsoft Lifecam as you didn't give us a model number, but you don't need to install the Microsoft software.

Ubuntu comes with IM software called Pidgin that can access MSN. If you want to use your webcam on MSN you will have to install a different client called Kopete.

There is not a Linux version of Microsoft Office (I wouldn't expect there to be as Linux is a competitor to Microsoft Windows) but Ubuntu comes with Openoffice.org; a very capable office suite that can read and write MS-Office files. The Gimp is an advanced image editor that also comes on the Ubuntu disc.

All those torrent clients except uTorrent are available for Linux. In fact, Transmission comes preinstalled.

The Epson Stylus CX3200 is listed as working "perfectly" on Linux. I've set up printer sharing Ubuntu to Ubuntu, and it's ridiculously easy, but I've never tried Vista to Ubuntu for this. It probably works in the same way, or you might need to install Samba (Windows networking) on Ubuntu.

The network will not be affected by the different operating systems running on it; they communicate using standards.

When you go to install Ubuntu, you can do it in one of two ways:

1. Erase an entire disk and dedicate it to Ubuntu
2. Resize an existing partition to free some physical disk space, and install Ubuntu into the free space.

The installer will give you the option. If you erase an entire disk, it does not hurt your other disks.

The best advice I will give you is: If you choose the option to resize a partition, a bar chart appears at the bottom of the window. On the right side of the bar chart is a handle. **Slide the handle to the left to allocate more disk space for Ubuntu.** Some people have not noticed the handle and have just blindly clicked "Next", causing Ubuntu to install itself with the 2.3 gigabyte minimum partition, and then they run out of room as soon as they try and install updates.

I'd recommend disconnecting all other disks when you install Ubuntu, just so you can't make any mistakes, and so the bootloader gets installed onto the correct disk. After installation you can safely plug them back in again.

Winamp is, as the name suggests, a Windows program. iTunes is also Windows-only. Ubuntu comes with Rhythmbox, which is a pretty good music manager. There are close on a hundred other music managers for Linux, so you have plenty of choice.

You don't need iTunes. There is a lot of iPod management software for Ubuntu, and a few of the music managers can do it too.

Good luck!

---

### Post by InkedScales on 2009-07-22
Wow thanks for all the advise, Im sorry about the model numers etc I knew that might be an issue but as im running things atm I couldnt pull my pc apart to have a good look, I will do as soon as I can and stick them up... one issue I have with the sound card if I cant get it to work is that the optical (which I use as I use my amp for the 5.1) on my motherboard is fried due to a muppit mate who thought it would be clever while we were tinkering to shuve his hand straight in when it had been running with the components not all fixed down and caused a static shock to arc off his finger and blow it.... thats why I baught the card initially.

thanks about the words of wisdom regarding itunes I honestly didnt realise that you can use other programs for ipods.

anyway I will make note of what you have said so far and try get all the model numbers of all hardware so that I can see if you can help me further as Im abit cagey about actually installing ubuntu unless I know everyting that I need will work.

anyway thanks again for the answers Ill see what details of the hardware I can get

---

### Post by InkedScales on 2009-07-25
right ive got more info I think now my graphics card is ATI Radeon HD 3600 Series

and sound card is Creative SB X-Fi
High Definition Audio Device (2x)

sorry if this isnt helpful again but I used to Belarc advisor to find out....

also thanks for previous help but can anyone else make any input into my question about dual monitor display??

thanks

---

### Post by InkedScales on 2009-07-25
just thought, if its not clear what Im asking, does antyone know how I would set up dual monitors on an ubuntu machine and also with the hardware details I gave u do you think there will be a problemw ith drivers?

thanks again

> **InkedScales said:**
> right ive got more info I think now my graphics card is ATI Radeon HD 3600 Series

and sound card is Creative SB X-Fi
High Definition Audio Device (2x)

sorry if this isnt helpful again but I used to Belarc advisor to find out....

also thanks for previous help but can anyone else make any input into my question about dual monitor display??

thanks

---

