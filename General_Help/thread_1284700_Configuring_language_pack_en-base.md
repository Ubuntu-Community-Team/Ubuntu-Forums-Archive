---
title: "Configuring language pack en-base"
date: 2009-10-06
forum: General Help
---

### Post by PrePenguin on 2009-10-06
**[B]**[/B]I have tried over and over to install ubuntu 9.04 and i am new to linux however i get everything installed but when it reaches the Configuring language pack en-base screen it stays at 1% and wont install further .. I have tried to use command-line install and normal install however i keep getting stuck at this point. I have burned 3 cd's making sure it wasnt a defective disk burn. I do not know how to solve this issue.. this is for low memory system installs for the 433mhz etc installs i have followed everything to the T but getting hung up here. This is a single partition system with ubuntu being the only OS. Any help resolving this issue would be greatly appreciated i have for 3 days now tried to install this thing with no avail or if i install grub it wont let me log in if i get that far. Help please.. Thank You!

---

### Post by ankspo71 on 2009-10-06
Hi,
Have you tried the alternate CD? [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate) . Here are the system requirements for Ubuntu. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) .
 The alternate cd should install if you meet the 'Bare Minimum' requirements found on that page. If you were using the live CD where it got hung up, then the alternate cd should help.

Other than that... Have you tried checking your memory with the Ubuntu CD? Have you tried checking the cd for defects? You can see where to check it in this image: 
[IMG]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=Install2StartUp.png[/IMG]
James

---

### Post by PrePenguin on 2009-10-06
Thanks for the response Ankspo71.. I am using the alternate CD install for low-mem systems also no liveCD.. I have ran memory check with the disk all checks fine. I also checked CD integrity on all 3 cd's I burned its checks ok.  I also used the command-line install as alternate install and keep wiping partition and reformatting HD for install so its a fresh install, however just when it gets to the configuring the language pack it hangs at 1% I am baffled by this. I am trying once again. Anymore suggestions would be great I am open to anything..

---

### Post by ankspo71 on 2009-10-07
Hi again,
The main download servers are extremely slow lately, so I have a suggestion. Use the alternate installation method, and when it asks for the url for the mirror, replace the default url with ```
 mirror.anl.gov 
``` I think the language packs have to be downloaded first before it can actually configure them, which could take a long time with the way the main server has been lately.
Hope this helps.
James.

---

### Post by PrePenguin on 2009-10-07
Ankspo this machine has no access to internet at the moment i have no wireless card installed yet for broadband.. Are you saying this is why the language pack config is hanging up? If so is there away around this for non-connected systems getting around this language pack deal? Your answers are very appreciated..
 
                                                   Tre

---

### Post by ankspo71 on 2009-10-07
Hi,
In the system requirements link above, it lists internet as a recommended requirement. I do believe that internet is required for language packs, which I think is why Ubuntu also provides DVD's with language packs in them.Can you burn and play DVD discs? If so, try here [http://www.ubuntu.com/getubuntu/downloadmirrors#dvd](http://www.ubuntu.com/getubuntu/downloadmirrors#dvd) <- 8.04 version

Edited: Ubuntu 9.04 DVD is here: 
[http://cdimage.ubuntu.com/releases/9.04/release/](http://cdimage.ubuntu.com/releases/9.04/release/) 
[http://mirror.anl.gov/pub/ubuntu-iso/DVDs-Ubuntu/9.04/release/](http://mirror.anl.gov/pub/ubuntu-iso/DVDs-Ubuntu/9.04/release/)

> DVD downloads
Don't be confused, even though DVDs can hold far more data than the typical Ubuntu CD, the main benefit of the DVD downloads is to get access to all of the available language packs. Most people will be fine with the standard CD installer. There are fewer download locations for the DVD images and this list is updated less frequently than for the CD images.
James

---

### Post by PrePenguin on 2009-10-07
Yes I can burn the Dvd download on this machine however on the older HP system has no Dvd reader which would make that useless..And with this being a alternate install and starting from a clean install how would they assume people would have internet connection unless running a dual boot system? This is confusing me.. Surely there has to be a way to bypass these and update later. I am still on the hunt if anyone gets a great idea please let me know thanks...
 
 
                                                                     Sincerely,
                                                                                    Tre

---

### Post by ankspo71 on 2009-10-07
Hi,

I have some news. Since I last posted I tried out the alternate cd (without internet) inside Virtualbox [http://www.virtualbox.org/]("http://www.virtualbox.org/") 

I was able to install it without internet, and with only 256mb memory and 64mb graphics memory. It took me about an hour but it did finally finish the install. The language pack itself took about 3-4 minutes before it got past that 1% mark. I have a 3.0Ghz computer though, so I think your other computer might take a bit longer. So english(us) must come with  Ubuntu (obviously).

If you are just looking to try out Ubuntu for a while to see if you like it, you can always install Virtualbox on your good computer and install Ubuntu inside that... I mean if you can't get it installed on the other computer right now. Btw, Ubuntu 9.10 comes out in about 3 weeks.

What are your computer's specs? I'm all out of ideas for now, but that will help other people help you.

Good luck,
James.

---

### Post by PrePenguin on 2009-10-07
Great ankspo for going through all that legwork I will give it a shot.. I mostly want to see ubuntu in action before i persue putting on my newer machines to make sure i feel comfortable with it .. Plus I have all these aging systems i need to find something that will work with older hardware and less memory consumption.. Thats the goal anyways. Once again I will report if i have any progress in this .. I am giving it hell trying .. I just may have to use a better system to set-up a trial run but if this one can run it any can in my opinion... Thanks alot Tre....
 
 
By the way this system has only 128mb memory and a 8.5 gig hd witha a 466mhz Pentium Celeron processor so its pretty low spec's.. But if i can get it on this in graphical form I can run it on all these aging systems of course once i get it installed I will do some memory upgrading from spare old modules.. However according to the minimal specs it should install on this system..

---

### Post by PrePenguin on 2009-10-07
Still hanging at 1% on the Configuring language-pack-en-base everything else installs great still looking for a solution to this if anyone can help.. Thanks in advance.

---

### Post by PrePenguin on 2009-10-07
> **PrePenguin said:**
> Still hanging at 1% on the Configuring language-pack-en-base everything else installs great still looking for a solution to this if anyone can help.. Thanks in advance.
 
 
I would also like to note that even though the install is hanging at 1% that the Hard Drive activity light is staying constantly lit yet the progress doesnt gain an inch. Still looking for any suggestions thanks..:confused:

---

### Post by PrePenguin on 2009-10-08
**Ok I have installed ubuntu 9.04 on this laptop and is running great so far but since i am new to linux desktop I have a few issues refering how to install plug-ins for the movie player like codecs and suggestions on software to add and how. Please be patient with me since I am a true newbie of ubuntu..If I can get some guidance to getting things working and where to get good linux software would be appreciated. My first post using linux yay ;) lol..**

---

### Post by ankspo71 on 2009-10-08
I'm glad you finally got it installed. :) 

If you want to browse through some programs to see what is available, you can click on your applications menu and select 'add - remove...' . 

But to answer your question about the codecs and things... A better way to do it is to go to System > Administration > Synaptic Package Manger. From there you will want to search for a package called ubuntu-restricted-extras. This package contains all of the popular codecs, adobe flash, extra fonts etc. Once you find it, you will want to click the box so that it will mark it for installation. Then all you need to do is click on the apply button. The reason they are not installed by default is because they use different software licenses than what Ubuntu uses.

Sooner or later you might want to learn how to use the terminal to do things by command line, so I will include the code for installing this package for future reference. Open the terminal and type (or copy paste):

```
sudo apt-get install ubuntu-restricted-extras
```I'm glad to hear you are enjoying ubuntu already.
James

---

### Post by PrePenguin on 2009-10-08
**Thanks for all your help ankspo u have been great.. Unfortunately i never did get it to install on that old system.. I am running it now on a dual Boot Acer Aspire with a 2.1 AMD Athlon X2 QL-64 Processor with 3Gigs of Memory ,ATI HD 3200 Graphics card with a 320 Gig HD. I am sure I will be needing alot of help getting use to using linux in the future here soon and if everyone is as helpful as you it will be great.. My only issue so far is adding desktop icons and finding proper software because it all seems to have silly names and nothings in lamons terms.. I know Linux programmers take pride in being techno but they really need to use common plainenglish to name things more direct it sure would make for windows movers to be so much less hesitant.. Keep watching for me bud I am sure i will have a million more questions lol... Once again Thanks Ankspo...**

---

