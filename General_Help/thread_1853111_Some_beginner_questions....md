---
title: "Some beginner questions..."
date: 2011-10-01
forum: General Help
---

### Post by capicoso on 2011-10-01
Hi. Hope not to bother.
I installed Ubuntu 11.04 on my desktop machine, it's a Core 2 Duo 2.8GHz, 2GB ram, a Nvidia graphic card which i dont remember the model but its a low-priced one 1GB ram. 
I used some linux distros like puppy, knoppix, dsl. But i just tried them, nothing serious. Now i decided to go real with Ubuntu. I uninstalled the Unity DE, then i upgraded to Ubuntu Studio for audio(puredata, ardour, jack, etc) but i think that was a mistake, it installed too many things. Then i installed the xfce de (...install xubuntu-desktop). But sometimes weird things happens! When i change too many times the desktop options it goes back to the GNOME desktop(??), the windows manager is still xfwm. But it changes the icons on the desktop, the wallpaper... And also when i shut down or start the system, first it loads the gnome desktop and then changes to xfce. 
Well, this got long, so here are the questions:
1) I feel my system is kind of messed up, because of so many things installed and upgrades, DE, etc. So if im sticking with XFCE, should i remove the other DE? Is it normal that each of my processors are at 10%-15% of work without any program opened?
2) Should i just uninstall everything and install it again?(I would stick with ubuntu, not going to Studio again)
3) Why does my desktop sometimes change to gnome when configuring xfce? 
4) Sometimes i get an error when i close the terminal( something like input/output error) is it a serious problem?
5) The thunar file manager takes like 30seconds to open(only the first time) then it gets very fast ad smooth. Normal?
6) Is there a way to "clean" the system?
7) Installing and uninstalling programs too many times ruins the system?(like on WinOs)


The system runs fast, but i feel that it should be EVEN FASTER:)!! I just feel like it's kind of unstable...

Thanks in advance and sorry for so many questions!

PS. Last time i checked i had around 146 processes running, that seems like a LOT of processes to me( used to the 30s from windows), but i dont know if its normal or not

---

### Post by MG&amp;TL on 2011-10-01
Xubuntu is what you're after. It is Ubuntu with the XFCE desktop pre-installed and no GNOME or Unity. You can install it in the same way as ubuntu, and you can install the same software in the same way. 

[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by MG&amp;TL on 2011-10-01
Because there is no registry (I think!) Linux will not slow down with too many things installed/uninstalled. The different DEs can cause problems as they do not remove their associated packages when they uninstall, only themselves. Therefore you can end up with 3 different notepad programs and email clients.

---

### Post by capicoso on 2011-10-01
Thanks for the reply. Yes, i had Xubuntu in mind. So i will try it, i wasn't sure because some people said that xubuntu is slower than ubuntu(minimal) + xfce, because Xubuntu had so much Gnome crap build into it? [http://ubuntuforums.org/showthread.php?t=899762](http://ubuntuforums.org/showthread.php?t=899762) , that thread is 3 years old though...

---

### Post by fixerdave on 2011-10-01
> **capicoso said:**
> ...
PS. Last time i checked i had around 146 processes running, that seems like a LOT of processes to me( used to the 30s from windows), but i dont know if its normal or not

I'm not saying I'm normal either ;) but, if you want a ballpark I've got about 60 or so processes listed, nearly all sleeping.  Load averages over the last while report about 0.5%.  Of course, it spikes as I refresh web pages, etc..

P.S.  One of my favourite quotes is "normal is a setting on a dryer."  Why be normal?  On the other hand, you don't want to be fluff-dry either ;)

---

### Post by WasMeHere on 2011-10-01
I suggest that you start by *saving* whatever *private data* you have to a separate disk or usb flash drive (documents, pictures, music etc). Then you download an iso file of the version of ubuntu you want. Xubuntu will probably be good for you. But you should also look at Lubuntu with the light-weight LXDE desktop.

But with > Core 2 Duo 2.8GHz, 2GB ram, a Nvidia with 1GB ram you have the horse-power to run vanilla ubuntu with unity if you like it.

Remember to make a *complete backup after the installation*! I like Clonezilla, and would let it make an image of the whole disk, but there are several other tools, that are also good.

I suggest that you read the following post, and if you wish the whole thread
[_http://ubuntuforums.org/showpost.php?p=11302166&postcount=_6]("http://ubuntuforums.org/showpost.php?p=11302166&postcount=6")

Have fun
Olle

---

### Post by MG&amp;TL on 2011-10-01
Ah. You DID install the driver for your graphics card?

---

### Post by capicoso on 2011-10-01
> **Olle Wiklund said:**
> I suggest that you start by *saving* whatever *private data*  you have to a separate disk or usb flash drive (documents, pictures,  music etc). Then you download an iso file of the version of ubuntu you  want. Xubuntu will probably be good for you. But you should also look at  Lubuntu with the light-weight LXDE desktop.

But with  you have the horse-power to run vanilla ubuntu with unity if you like it.

Remember to make a *complete backup after the installation*! I like Clonezilla, and would let it make an image of the whole disk, but there are several other tools, that are also good.

I suggest that you read the following post, and if you wish the whole thread
[_http://ubuntuforums.org/showpost.php?p=11302166&postcount=_6]("http://ubuntuforums.org/showpost.php?p=11302166&postcount=6")

Have fun
Olle

I tried Lubuntu and i liked it, but i just fell i love with Xfce, so simple and easily customizable. Yeah, Unity ran ok, but i'm kind of old school and like minimal environments. I had WinXP with the look of win98... So many colors and effects hurt my eyes,  i pay more attention to the effects than to what im doing ahah.

I'm downloading Xubuntu 10.04 now. I didnt think about making a backup AFTER installation, thats a good one. Clonezilla is like Norton Ghost i guess?
Thanks, im going out to buy a CD and burn Xubuntu!
Hope i can get processing, arduino and puredata to work properly... had to make so many things on ubuntu that i forgot what i did.
Thanks everyone.

---

### Post by MG&amp;TL on 2011-10-01
Hey, processing and arduino! Love those things. Yeah, they work on Xubu.

---

### Post by capicoso on 2011-10-01
> **MG&TL said:**
> Hey, processing and arduino! Love those things. Yeah, they work on Xubu.

Yeah, powerful little thingies! and got to love the fact that they are crossplatform and open source !

---

### Post by WasMeHere on 2011-10-01
> I'm downloading Xubuntu 10.04 now. I didnt think about making a backup AFTER installation, thats a good one. Clonezilla is like Norton Ghost i guess?

You download *Clonezilla* as an iso file and make a live CD or USB. It is text-based but quite clear and easy to understand. The software that is used by default unless there are some read/write problem is *Partclone*.

I started to use Ghost way back in the 1990ies. During several years I used PING (Partimage Is Not Ghost), but it cannot backup ext4 drives, so I had to go for something new, and I'm happy with Clonezilla.

But I have a dedicated partition for multimedia (pictures, video, audio). These files are already compressed, and they are big, so I use *Unison* to sync that partition with an esata disk.

---

### Post by thunderbirdje on 2011-10-01
> **capicoso said:**
> I'm downloading Xubuntu 10.04 now.

Hi capicoso,

I would recommend you to download a xx.10 version. Those are the stable versions. When a new version comes out, they release it in the xx.04 'test version' before the put all the feedback and corrections into the xx.10 version.

I believe in 12 days there will be the 11.10 version [https://wiki.ubuntu.com/OneiricReleaseSchedule]("https://wiki.ubuntu.com/OneiricReleaseSchedule"). In meanwhile just enjoy the other version.

I am running now 11.04 and it took me some work to fix stuff, however everyone is very helpful here and it is a pleasure to learn and run Ubuntu :)

Good luck!

---

### Post by MG&amp;TL on 2011-10-01
Have you tried the one where you hook one up to the other and graph the results in processing? Anyway, have fun. :D

---

### Post by Paddy Landau on 2011-10-01
> **thunderbirdje said:**
> I would recommend you to download a xx.10 version. Those are the stable versions. When a new version comes out, they release it in the xx.04 'test version' before the put all the feedback and corrections into the xx.10 version.!
Are you sure?

10.04 is the LTS version, which is preferred for people (like me) who need stability more than cutting-edge.

---

### Post by WasMeHere on 2011-10-01
> **paddy landau said:**
> are you sure?

10.04 is the lts version, which is preferred for people (like me) who need stability more than cutting-edge.

+1 = *agree*

---

### Post by MG&amp;TL on 2011-10-01
I suppose you could look at it like that.

However, *officially*, the even-numbered April (xx.04) releases are the LTS. (i.e supposed to be stable)

---

### Post by capicoso on 2011-10-01
> **MG&TL said:**
> Have you tried the one where you hook one up to the other and graph the results in processing? Anyway, have fun. :D

Yes, and connected also with Pduino(puredata patch) : D



Well i downloaded the 10.04 one because lot of people told me i should use LTS releases, i hope i did the right thing.


One more thing, is there any conf file to copy and paste it in my new install so i dont have to customize the DE again? Just wondering...

-----
And yes, this community seems to be very nice, kind and active. I'm glad to be joining in!;)

---

### Post by MG&amp;TL on 2011-10-01
The community IS nice and kind and active. You want to be careful or you'll end up like me. Obsessed.

LTSs are simply more stable, there is no right/wrong thing about them. 

There is no one single .conf file, I'm afraid. I suggest trying to remember what you did and copying the .conf or wherever from there.

---

