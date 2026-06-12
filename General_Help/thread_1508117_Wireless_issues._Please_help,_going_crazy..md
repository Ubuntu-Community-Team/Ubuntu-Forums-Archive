---
title: "Wireless issues. Please help, going crazy."
date: 2010-06-12
forum: General Help
---

### Post by Chudmuskett on 2010-06-12
Hi, please help, Im going out of my mind here. I have been trying this since 7am this morning and its now 6.35pm.

I am using a (dont laugh) Zoostorm 10-270 netbook and heres my problem:

I installed Ubuntu Desktop Remix on the hard drive replacing Windows 7 Home. I tried to activate the wireless but couldnt as the the wireless button is F2 (symbol is blue which corrisponds with the blue Fn key) and for some reason the Fn + F2 key wont work. Cut along story short I cant get the wireless working, it is a ralink rt3090 wireless.

Please help.

---

### Post by ibe2fly4chu on 2010-06-12
Just saw this post :O. Linux can be fustrating at times unfortunately, and its ironic that most the answers you need are online, when sometimes the problem is you cant get online lol.

Anywho, to turn on your wireless card (without the function FOR now..that is untill you find the right drivers/plugins to make them work)...go to Applications>accessories>Terminal and type:
"sudo iwconfig wlan0 up" without the quotes. If that dont doesnt turn on the wireless card you can also try "sudo iwconfig wlan0 auto".
report back what it says:P
*Note: this is assuming the driver for the card is installed and working. If not then you will most likely need ndiswrapper, which i can tell you how to do quick and simple...instead of point you to some guide that will probably confuse you more.

---

### Post by Chudmuskett on 2010-06-12
> **ibe2fly4chu said:**
> Just saw this post :O. Linux can be fustrating at times unfortunately, and its ironic that most the answers you need are online, when sometimes the problem is you cant get online lol.

Anywho, to turn on your wireless card (without the function FOR now..that is untill you find the right drivers/plugins to make them work)...go to Applications>accessories>Terminal and type:
"sudo iwconfig wlan0 up" without the quotes. If that dont doesnt turn on the wireless card you can also try "sudo iwconfig wlan0 auto".
report back what it says:P
*Note: this is assuming the driver for the card is installed and working. If not then you will most likely need ndiswrapper, which i can tell you how to do quick and simple...instead of point you to some guide that will probably confuse you more.

Thanks for your answer this is what happened:
iwconfig: unknown command "up"' & iwconfig: unknown command "auto"

What can I do next???

---

### Post by ibe2fly4chu on 2010-06-12
Try this driver package. Its in .deb so all you have to do is copy it to your linux machine and double click it to install it. [https://launchpad.net/~markus-tisoft...0~ppa1_all.deb](https://launchpad.net/~markus-tisoft...0~ppa1_all.deb). It has been known to work with your wireless card. 

If this doesnt work then we can try the alternate which is:

First pop your live cd in while logged into ubuntu.

Open the live cd, and navigate to pool/main/n
Install the ndiswrapper .deb files 

after installing the 2 files in the ndiswrapper folder, navigate to the ndisgtk folder and install that file as well.

At this point you might want to download your windows drivers for your wireless card. (preferably xp..it is just my personal opinion that xp drivers work best with ndiswrapper, but feel free to try other ones if xp doesnt work).

 For now i shall advise you to put the extracted folder in your home directory (places>home). Now go to terminal and type "cd .."
that should put you into the home folder. Now type cd {name of folder that the .EXE driver is in}. Once in that folder, now put in terminal "unzip -a <name of .Exefile>. This should now provide you with 2 type of file; a .sys file and a .inf .  

Now i would recommend opening a new terminal session (just to clear confusion)...type "sudo nidisgtk" and a Gui of nidwrapper should pop up. from here it should give you the option to install your windows driver. When choosing the driver to install, simply navigate to the folder that you extracted the .Exe file in and pick the file that has .INF at the end. After this the driver to your wireless card should be installed. Click on the little wireless symbol at the top of your desktop and it should show your available networks.

---

### Post by Chudmuskett on 2010-06-12
Thanks again for your help. I clicked on the link and got this message:

'There’s no page with this address in Launchpad.'

As there was an error message and I would like to try this first. I will wait for your reply before trying the other option. By the way, Im using the USB installation, not the CD.

Thanks again.

---

### Post by ibe2fly4chu on 2010-06-12
lol for some reason its not copying correctly...go figure lol...

ok refer to this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9387865](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9387865)

at the very bottom of page 2 someone has the same link posted there and it leads you directly to the .deb file i was referring to. ^^

---

### Post by Chudmuskett on 2010-06-12
> **ibe2fly4chu said:**
> lol for some reason its not copying correctly...go figure lol...

ok refer to this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9387865](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9387865)

at the very bottom of page 2 someone has the same link posted there and it leads you directly to the .deb file i was referring to. ^^

Nope, the link still doesnt work :(

---

### Post by ibe2fly4chu on 2010-06-12
hmm thats odd. Opens fine for me. Trying going to [www.google.com](www.google.com) 
 then pasting the link " http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9387865" into the search engine. it should be like the second link that pops up...

then once you are on the thread go to page 2, scroll all the way to the bottom, you should be able to see the original link i was trying to give ya with the .deb file

---

### Post by Chudmuskett on 2010-06-12
> **ibe2fly4chu said:**
> hmm thats odd. Opens fine for me. Trying going to [www.google.com]("http://www.google.com") 
 then pasting the link " http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9387865" into the search engine. it should be like the second link that pops up...

then once you are on the thread go to page 2, scroll all the way to the bottom, you should be able to see the original link i was trying to give ya with the .deb file

Please I am obviously missing something, the full link: 'deb [http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu) karmic main' isnt a link because it has spaces and if I start from the http bit and end at /ubuntu it takes me to a strange place that I dont understand what I am looking for.

---

### Post by ibe2fly4chu on 2010-06-12
ok no problem. Give me a minute to compress the .deb file and il upload it to this thread myself ^^

---

### Post by ibe2fly4chu on 2010-06-12
Nvm the email exchange request, i managed to find a free file hosting site. go to [http://www.filedropper.com/rt3090wirelessdriver_1](http://www.filedropper.com/rt3090wirelessdriver_1)
and download the file. it should be the zip file i uploaded. Extract it and install the .deb file

---

### Post by sea_coffee_programmer on 2010-06-12
I have the same issue on a diff. Netbook and different key combo...  fn + f11.  If you find everything out, let me know.  I have been stumped for the last 7 hours myself.

---

### Post by Chudmuskett on 2010-06-12
> **ibe2fly4chu said:**
> Nvm the email exchange request, i managed to find a free file hosting site. go to [http://www.filedropper.com/rt3090wirelessdriver_1](http://www.filedropper.com/rt3090wirelessdriver_1)
and download the file. it should be the zip file i uploaded. Extract it and install the .deb file

Thanks for that, its just doing stuff, I will get back to you once its finished.

---

### Post by Chudmuskett on 2010-06-12
> **sea_coffee_programmer said:**
> I have the same issue on a diff. Netbook and different key combo...  fn + f11.  If you find everything out, let me know.  I have been stumped for the last 7 hours myself.

Hi there, you wanna talk to this man '[ibe2fly4chu]("http://ubuntuforums.org/member.php?u=1088802")' he is an Ubuntu God :)

---

### Post by Chudmuskett on 2010-06-12
> **ibe2fly4chu said:**
> Nvm the email exchange request, i managed to find a free file hosting site. go to [http://www.filedropper.com/rt3090wirelessdriver_1](http://www.filedropper.com/rt3090wirelessdriver_1)
and download the file. it should be the zip file i uploaded. Extract it and install the .deb file

OK, Installation is finished, where we go now matey ?

---

### Post by ibe2fly4chu on 2010-06-12
After you installed the .deb file, go to the wireless icon symbol on the top of your desktop and see if it is picking up your wireless network. If it is, then all you will have to do is click on it and enter your password (if any). Also, if it doesnt show any connections, go to terminal and type: "sudo iwconfig wlan0 up". Post back the information here. reboot and then try sudo iwconfig wlan0 up again. If it still doesnt show anything then we can try nidiswrapper approach.

---

### Post by Chudmuskett on 2010-06-12
> **ibe2fly4chu said:**
> After you installed the .deb file, go to the wireless icon symbol on the top of your desktop and see if it is picking up your wireless network. If it is, then all you will have to do is click on it and enter your password (if any). Also, if it doesnt show any connections, go to terminal and type: "sudo iwconfig wlan0 up". Post back the information here. reboot and then try sudo iwconfig wlan0 up again. If it still doesnt show anything then we can try nidiswrapper approach.

OK, I unplugged my internet cable and it didnt pick up the wireless so I typed sudo iwconfig wlan0 up and got this message  iwconfig: unknown command "up"

---

### Post by Chudmuskett on 2010-06-12
Thanks for your help so far, I will have to come back and carry this on tomorow as its getting late here. Thanks again.

---

### Post by ibe2fly4chu on 2010-06-12
hmm... open terminal and type : "lshw -C network". Paste your results back here.

---

### Post by ibe2fly4chu on 2010-06-12
no problem. If all else fails just remember that ndiswrapper will fix almost 95% of your network card issues. With the steps i gave you, should have no problem following ^^.

---

### Post by Chudmuskett on 2010-06-13
Hi, the results of what lshw -C network is:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:1a:13:bb:2d:80
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.65 latency=0 multicast=yes
       resources: irq:27 ioport:3000(size=256) memory:50010000-50010fff(prefetchable) memory:50000000-5000ffff(prefetchable) memory:50020000-5003ffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: ra0
       version: 00
       serial: 00:1a:13:ba:d5:3d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:54100000-5410ffff

---

### Post by ibe2fly4chu on 2010-06-13
ok it seems everthing is in order. Next in terminal, type: "iwlist wlan0 s" ....This should now use your network card to scan for available networks in your area. You should see your connections along with others if they are near by. Post back results we can go from there.

---

### Post by Chudmuskett on 2010-06-13
Hi again, I did what you said and it told me: wlan0     No scan results. UPDATE: Please ignore this and read next rply I posted, I made a mistake

---

### Post by Chudmuskett on 2010-06-13
I forgot, I reinstalled the os this morning so I reinstalled the .deb file and typed what you said again and got this message: wlan0     Interface doesn't support scanning could you guide me through the ndiswrapper please. I have just installed it through software centre

---

### Post by ibe2fly4chu on 2010-06-13
> **Chudmuskett said:**
> I forgot, I reinstalled the os this morning so I reinstalled the .deb file and typed what you said again and got this message: wlan0     Interface doesn't support scanning could you guide me through the ndiswrapper please. I have just installed it through software centre

First pop your live cd in while logged into ubuntu.

Open the live cd, and navigate to pool/main/n
Install the ndiswrapper .deb files 

*i would recomend still installing those .deb files from the live cd because there are some utilities and other packages not provided in software center*

after installing the 2 files in the ndiswrapper folder, navigate to the ndisgtk folder and install that file as well.

At this point you might want to download your windows drivers for your wireless card if you havent already. (preferably xp..it is just my personal opinion that xp drivers work best with ndiswrapper, but feel free to try other ones if xp doesnt work).

For now i shall advise you to put the extracted folder in your home directory (places>home). (just for a visual: folder path should look like this {places>home>"folder with your driver">.Exe file} Now go to terminal and type "cd .."
that should put you into the home folder. Now type cd {name of folder that the .EXE driver is in}. Once in that folder, now put in terminal "sudo unzip -a <name of .Exefile>. This should now provide you with 2 type of file; a .sys file and a .inf . 

Now i would recommend opening a new terminal session (just to clear confusion)...type "sudo nidisgtk" and a Gui of nidwrapper should pop up. from here it should give you the option to install your windows driver. When choosing the driver to install, simply navigate to the folder that you extracted the .Exe file in and pick the file that has .INF at the end. After this the driver to your wireless card should be installed. Click on the little wireless symbol at the top of your desktop and it should show your available networks.

Also note: there are other guides out there on how to use ndiswrapper. I usually try to simplify the process however because if this is the first time you are using linux it can get confusing.

---

### Post by ibe2fly4chu on 2010-06-14
Did this solve the issue?

---

### Post by Chudmuskett on 2010-06-15
Hi, I got up to the unzip the exe part then it didnt work :( it wont unzip it

---

### Post by ibe2fly4chu on 2010-06-16
hm. I think you need cabbex. Il look into it and post back

---

### Post by ibe2fly4chu on 2010-06-16
Cabextract should have come installed on 10.4 already. i looked into the commands to make sure i wrote them right and the one stated above Should be valid. They seem correct...

for now *bump*..il post back if i learn anything.

---

### Post by ibe2fly4chu on 2010-06-17
*bump* anyone?

---

### Post by Chudmuskett on 2010-06-19
I dont understand whats going on now :( this is going to have to be a totally hold hands and feed me operation

---

### Post by dino99 on 2010-06-19
install this package:

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb](https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb)

or follow this howto (more complicated)

[http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/](http://www.halibutdepot.org/how_to_build_rt3090_for_ubuntu_lucid/)

---

### Post by Chudmuskett on 2010-06-19
Tried that and yet again, got to a certain point and it didnt work. I GIVE UP AAAARRRRGGGHHH How the hell do they expect to make this sort of OS more appealing to windows users if it is not newbie friendly. Ubuntu is a chocolate teapot to new users, we are not all programmers or psychic. SORT IT OUT UBUNTU PROGRAMMERS otherwise you are never going to have ANY sort of new user support.

---

### Post by Chudmuskett on 2010-06-19
Well, I take back everything I said, IT WORKED!!!!!!!!!!!!!

Sorry Ubuntu Programmers :) 

Ive always said it is a fantastic program. LOL

:p:KS\\:D/

And thank you to [ibe2fly4chu]("http://ubuntuforums.org/member.php?u=1088802")  and [dino99]("http://ubuntuforums.org/member.php?u=129712")  for your time, effort and help, I cant thank you enough.

=D>=D>=D>=D>

---

### Post by sea_coffee_programmer on 2010-06-20
Heh, i have been watching this thread since it was started.  At least you got it up and running.  I didnt mean to not post anything, but thats because i was in a similar situation to you and i sort of figured it out on page one, but thats because i already spent like 8 hours trolling around terminal. >_>

Glad that it is up and running for you.  :)

---

### Post by Chudmuskett on 2010-06-20
> **sea_coffee_programmer said:**
> Heh, i have been watching this thread since it was started.  At least you got it up and running.  I didnt mean to not post anything, but thats because i was in a similar situation to you and i sort of figured it out on page one, but thats because i already spent like 8 hours trolling around terminal. >_>

Glad that it is up and running for you.  :)

So you are telling me that I have spent almost a week & four pages of my life getting this sorted out and you have been watching the whole time and could have jumped in at page one. Thanks for posting now to let me know, its really helped. LOL.

---

### Post by kloparto on 2010-07-06
Could you please say how you did work it out?

---

### Post by alexp81 on 2010-07-12
> **dino99 said:**
> install this package:

[https://launchpad.net/~markus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0~ppa1_all.deb]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090/+files/rt3090-dkms_2.3.1.3-0ubuntu0%7Eppa1_all.deb")

...

Having the same problem, I downloaded the package you mention above, but when I open it there is an error: Dependency is not satisfiable: dkms

Any help?

---

