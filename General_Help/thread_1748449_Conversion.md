---
title: "Conversion?"
date: 2011-05-03
forum: General Help
---

### Post by dhinderliter on 2011-05-03
No I didn't search...I have no idea what to search for. I had ubuntu on my laptop a few years ago and while i really loved it my phone was.not.compatible. I don't think my camera liked it either. Anyways....I have an EVO now which I am SURE works on ubuntu right? I mean if it doesn't i'll be floored and probably have a heart attack. I just wanted to mention it just in case. I am wanting to install ubuntu on my laptop and my desktop and then my BF's desktop will probably stay windows (not sure). I use my desktop as a media center and store all of our movies and music on there and use it to backup files (or some hodge podge of backups..continue reading). I shouldn't have any problems putting ubuntu on it and still using it as a media center right? There's not going to be some weird problem with playback on movies (torrentz), netflix, itunes (?? i still own an ipod and don't want to make it worthless either) or networking (i had successfuly networked my windows and ubuntu before so i know that it can be done). 

Another goal of using a new OS is to sync everything. I have lots of digital stuff (as I'm sure we all do now) and I want to keep it straight, access it from anywhere (looks like the ubuntu cloud is great!), and also have my computers sync to the media center and the media center do a whole backup to my external hard drive. I'm hoping Ubuntu can help. 

also has anyone gotten a gmail drive on ubuntu? I would also like to utilize this free storage space.
what about amazon mp3 cloud player? 
what about the apps through the android marketplace that have syncing to computer capabilitys? do most/all of the apps on android work within ubuntu? (i would hope and think so but weirder things have happened)

---

### Post by wilee-nilee on 2011-05-03
Make it easy start out with a wubi install or a dual boot, or a virtual setup.

---

### Post by jeremy1138 on 2011-05-03
Netflix does not work on Linux.  The only workaround that I know of (and it's not a good one at all) is to run windows in a virtual machine and watch Netflix in that.  I really hope Netflix stops using that Silverlight monstrosity someday soon but I don't think it's likely.

---

### Post by dhinderliter on 2011-05-03
> **jeremy1138 said:**
> Netflix does not work on Linux.  The only workaround that I know of (and it's not a good one at all) is to run windows in a virtual machine and watch Netflix in that.  I really hope Netflix stops using that Silverlight monstrosity someday soon but I don't think it's likely.

ah i should have known that. i was just reading about the problems of netflix on the evo and silverlight. damn.....
i didn't really like dual booting last time, it just seemed to be a big waste of time but i was also having to use basically 2 computers for my daily activities. will have to look up wubi cause i don't know what that is. i do want to keep netflix streaming, especially since there is an app (paid...so i don't have it yet) that i can stream the netflix through the computer to my phone. i guess i can either leave bf's computer as windows or provide a small partion for dual booting, altough i think that means i would need to be able to leave my computer in windows in order to stream netflix...which is pointless. damn damn damn....i had planned on streaming netflix through my laptop to hook to my bedroom tv but i guess i'll have to invest in miniHDMI instead and just stream it through the evo instead. not sure what i'll do when i finally get the media center working to hook back up to the tv (burned video card, i want to put in an HDMI port however i do that), or i'll just have to figure something else out. 

Is the benefits worth it? I probably should just look up some screen shots huh....

ok wubi=windows app. doing it now to test out.

what about parental controls? i have SMALL children and basically want to make a few buttons for kids webpages, and a start menu with games...does ubuntu have good parental control options?

---

### Post by jeremy1138 on 2011-05-03
Ubuntu is an amazing operating system but, just like anything else, it has its drawbacks.  For me, the major problems are Netflix streaming and gaming.  I use a dual boot configuration and I just have to boot my computer into whatever OS I need at the moment.

I'll try to answer some of your questions from above.

WUBI is an installer that allows you to install Ubuntu through Windows as if it was a program.  This has the advantage of not having to partition your hard drive or use the GRUB bootloader and it also allows you to uninstall Ubuntu through add/remove programs in Windows.  In my opinion this is not a good option in your case because it does have performance drawbacks and other weirdness and you still have to select the OS you want to boot into when you start it up just as if you were using any other dual boot configuration.

Adding an HDMI port to your computer will (as far as I know) require you to install a new video card.  There are many cards out there that have different combinations of DVI, VGA and HDMI ports.  I have an ATI Radeon 4670 that has two DVI ports and an HDMI port for example.  You'll have to do some research on whether or not audio from your computer can be routed through the HDMI port in this fashion because I have no experience with that.

edit:
you could also use like a DVI to HDMI (or whatever you have) adapter to get HDMI video out of your computer, but you will definitely have to use an alternative method to get audio to your TV using this method.

---

### Post by dhinderliter on 2011-05-03
> **jeremy1138 said:**
> Netflix does not work on Linux.  The only workaround that I know of (and it's not a good one at all) is to run windows in a virtual machine and watch Netflix in that.  I really hope Netflix stops using that Silverlight monstrosity someday soon but I don't think it's likely.

you are talking about using portable apps with firefox portable and the silverlight loaded on the usb drive? cause i just looked that up and was wondering if it would work.

---

### Post by jeremy1138 on 2011-05-04
I'm not sure exactly what you're referring to with running silverlight on a usb drive...

The reason Netflix doesn't work on Linux is a problem with DRM.  While there is an open source version of Silverlight (known as Moonlight), the DRM portion of the program is not available on Linux.  Since this DRM is not available on Linux, the content providers won't allow Netflix to stream their movies/shows to a computer running Linux.

I've seen some documentation of attempts to install Silverlight via Wine but none have been successful as far as I know.

What I was referring to when I mentioned a virtual machine was that you would actually run a windows operating system inside a virtual machine using Virtual Box or something similar.  It's a far from ideal solution and I wish there was something better...

edit:
Please post a link to the web page where you got the information on installing Silverlight on a USB key.  I'd like to take a look at it.

---

