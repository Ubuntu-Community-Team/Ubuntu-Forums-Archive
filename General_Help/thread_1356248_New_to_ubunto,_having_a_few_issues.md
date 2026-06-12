---
title: "New to ubunto, having a few issues"
date: 2009-12-15
forum: General Help
---

### Post by alexander39 on 2009-12-15
I am new to Linux and don't really understand how to work it just yet, sorry if I'm not very computer-literate but I'll try to explain.

I have Ubunto 9.04 and I need to know how to find something for the default media player that came with Ubunto to play my .mp3 songs, movies, videos, and mpeg files. I also need to know how to have my wireless receiver work on Linux too.

A friend told me that I need to install certain drivers for my computer and that this forum site would be able to help. I am completely blind about this new system and any information would be helpful. Oh, I have a HP pavillion DV2500. I was told I needed to add that so I could get the necessary drivers for my computer.

Thanks!

---

### Post by Bucky Ball on 2009-12-15
If you haven't already, plug in an ethernet cable and get all updates. This is NOT like windows in the 'get drivers' department. That will probably pick up your wireless card and offer you the correct drivers.

Go to System->Administration->Hardware drivers. Is there a driver already there for your wireless card but disabled?

Now, System->Administration->Synaptic Package Manager (while you are online) and search for and install 'ubuntu-restricted-extras'. That should take care of MP3 etc. There are heaps of media players besides whatever came with Ubuntu. You will find some in 'Applications' and 'Sound and Video' or 'multimedia'. (It varies and I am using 8.04 LTS so wouldn't know what that section is called in 9.04).

Good luck.

---

### Post by lyall on 2009-12-15
> **alexander39 said:**
> I am new to Linux and don't really understand how to work it just yet, sorry if I'm not very computer-literate but I'll try to explain.

I have Ubunto 9.04 and I need to know how to find something for the default media player that came with Ubunto to play my .mp3 songs, movies, videos, and mpeg files. I also need to know how to have my wireless receiver work on Linux too.

A friend told me that I need to install certain drivers for my computer and that this forum site would be able to help. I am completely blind about this new system and any information would be helpful. Oh, I have a HP pavillion DV2500. I was told I needed to add that so I could get the necessary drivers for my computer.

Thanks!

here a link to help you along
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty")

look at section 2.8 Multimedia Applications it will answer some if not most of you question about media players

I did a search for HP pavillion DV2500 Linux 
and found several answers for the different drivers 
which one or ones do you need
It would be a great way to found out what others are using that might work for you

Good Luck and have fun learning

ps bookmark the link above because might help you in the future

---

### Post by Bucky Ball on 2009-12-15
> **lyall said:**
> 
I did a search for HP pavillion DV2500 Linux 
and found several answers for the different drivers 
which one or ones do you need


The HP DV series generally use a Broadcom wireless card and these are very well catered for in Linux nowadays. (Not always the case.) As I said, you shouldn't have to do anything apart from plug in an ethernet cable and get your updates. The card should be picked up and you will be offered the drivers which will also drag in the firmware. Takes all of about five minutes. I should know; I have a DV6000.

There is really no manual labour of searching for and installing any exotic drivers with the vast majority of HP dv machines. A no brainer actually (generally).

MAIN POINT: Plug in an ethernet cable; get updates; check System->Administration->Hardware Drivers.

Do you see the B43 driver in there? Is it disabled?

---

### Post by alexander39 on 2009-12-17
Thanks everybody for helping me out. It all was pretty much a no-brainer. I just had to hook up an ethernet and it told me everything to do. I will book mark that link if anything else confuses me.

I appreciate everything!!

---

### Post by Bucky Ball on 2009-12-18
Welcome and enjoy!! ;)

---

