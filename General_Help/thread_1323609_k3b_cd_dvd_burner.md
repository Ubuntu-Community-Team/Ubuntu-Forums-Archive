---
title: "k3b cd dvd burner"
date: 2009-11-06
forum: General Help
---

### Post by 824957q on 2009-11-06
ok look i have a linux kubuntu an i have two cd drives one that only plays dvd's music and one that is the hewlett packard cd writer plus and i have the application k3b that's supposed to burn iso music and other files to the blank cd now i bought two copies of the blank cd called jvc high speed 120 min dvd=r recordable dvd=r for video and data i put in the disc and it says there                    is no medium what can i do and i am trying to install the new linux kubuntu 9.10 becasue it says your usernam is unknown to udo pleaaaaaaaaase help with either ojne  of the prolems:lolflag:

---

### Post by 824957q on 2009-11-08
ok i have two problems my sudo broke and i can't go into recovery mode. so i wanna do a clean install bye disk.. BUT there is one problem i put in the blank disc of 4 giga bites bla.. bla.. and it says please insert a medium and i have hp cd writer plus and a regular cd drive is it possibly the software im using its k3b and i dont know what version so is there anyway to do a clean install any other way and ps.. i cant access the grub menu i press the buttons and nothing happens i could really use your help thank you

---

### Post by howefield on 2009-11-08
Take a breath and formulate your questions so others can understand where you are stuck.

---

### Post by 824957q on 2009-11-08
my sudo broke cant boot into the grub menu to recovery mode i try to do clean install i download kubuntu 9.10 from torrent and when me try burn to disc it say no disc what me do????????? me have program k3b and me can't install nothing more me dont have flash player either

---

### Post by Druke on 2009-11-08
:-$ We'll be glad to help you, but we need to you to reformulate that post.
[LIST]
[*] Try using lists to separate different issues
[*]Relax, we'll do our best to help you.
[*]We cannot easily help you If we need to read your post 15 times to interprate it.
[/LIST]

---

### Post by 824957q on 2009-11-08
#1sudo is broken                                                                 2#can't boot into recovery mode or the grub menu 3#i downloaded kubuntu 9.10 from a torrent                                                               #4when i open my burner program it says please insert a medium.                                                                                                #5 i have a disc already in there

---

### Post by Druke on 2009-11-08
#1sudo is broken 2#can't boot into recovery mode or the grub menu 3#i downloaded kubuntu 9.10 from a torrent #4when i open my burner program it says please insert a medium. #5 i have a disc already in there
[LIST=1]
[*]Sudo i broken: not sure what this means (does this mean you cannot use sudo inside linux)
[*]does this mean you cannot boot up at all
[*]how is this a problem?
[*]strange... so I see you're trying to make a new install of ubuntu
[/LIST]

Ok, so sudo is broken and you can't get grub to display (however because you can get to your burner application I can assume that you actually can boot to ubuntu). You are trying to burn a new ubuntu cd, but cannot because it is failing to detect your cd.


is this all correct?

---

### Post by 824957q on 2009-11-08
yes and when sudo is broken it happens when i took myself out of the sudoers file and im not a administrater but im the only on there and i can't install any programs because sudo prompts me for a password and when i put my password it says "your username is unknown to sudo get me? yeah everything you said was correct

---

### Post by Jordanwb on 2009-11-08
> **Druke said:**
> 
[LIST=1]
[*]Sudo i broken: not sure what this means (does this mean you cannot use sudo inside linux)
is this all correct?[/list]

This actually happened to me on my server. I couldn't run "sudo ..." it would say I'm not in the sudoers file. I had to use the recovery list item to add my username to /etc/sudoers.

> **824957q said:**
> when i took myself out of the sudoers file

[adam_savage]Well there's your problem![/adam_savage]

---

### Post by Druke on 2009-11-08
That is a hard place.

You may need to burn the iso from a new computer (editing sudoers directly is BAD).

I suspect you cannot detect the cd because you don't have permission to mount it. (I may very well be mistaken)

---

### Post by Jordanwb on 2009-11-08
> **Druke said:**
> I suspect you cannot detect the cd because you don't have permission to mount it. (I may very well be mistaken)

I have this in my /etc/fstab file:

```
/dev/scd0 /media/cdrom1 udf,iso9660 **user**,noauto,exec,utf8 0 0
```

but this is my laptop.

---

### Post by 824957q on 2009-11-08
ok my uncle has a laptop with windows xp so is it possible i can put the kubuntu iso file in my mp3 player then take it out and put it on my uncles laptop?

---

### Post by Druke on 2009-11-08
yup, [but you will need an application that can burn iso's.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by 824957q on 2009-11-08
oh ok what would that application be oh and its a windows xp so can you give me the link to a free software that wont destroy my uncles computer and it would be able to burn the image to my cd lol and it has to be free lol

---

### Post by Druke on 2009-11-08
already linked it in my previous post ;)

---

### Post by 824957q on 2009-11-08
oh ok cool thanks for your help dude why can't we have more nerds like you lol

---

### Post by Druke on 2009-11-08
Geek is my preference actually ;)

---

### Post by 824957q on 2009-11-08
ha ha ok well hopefully it works.. oh! ojne more thing you the the little conectrer for audio a microphone and all that for some reason its noit working will it work aftrer i install the new version

---

### Post by Druke on 2009-11-08
no idea, you never told us what sort of hardware you have.

---

### Post by 824957q on 2009-11-08
it says i have riptide

---

### Post by 824957q on 2009-11-08
i keep getting this message why?

---

### Post by 824957q on 2009-11-08
i get this message your username is unknown to sudo and im the only person on there i cant install anything and i cant get into the grub menu at start up please help

---

### Post by overdrank on 2009-11-08
Threads merged.

---

### Post by Druke on 2009-11-08
no idea what you're talking about.

---

### Post by 824957q on 2009-11-11
ok so i have kubuntu 9.4 and i want to try to upgrade to karmic koala, but i can't make my own install cd and i can't upgrade because i broke sudo is there a way were i can request a cd from somewere for free like a install cd? or is there another way to fix sudo without going into recovery mode?

---

### Post by Vaphell on 2009-11-11
can't you simply download .iso from the internet? sudo is not required to download and burn stuff to cd.

---

### Post by Andy H. on 2009-11-11
I ran update manager in 9.04 and it did the upgrade for me to 9.10.  I'd recommend starting before you go to bed or go out for awhile unless you have a super fast connection as you're looking at about 650MB to download.
 
Good luck,
 
  -AH

---

### Post by SuperSonic4 on 2009-11-11
> **Andy H. said:**
> I ran update manager in 9.04 and it did the upgrade for me to 9.10.  I'd recommend starting before you go to bed or go out for awhile unless you have a super fast connection as you're looking at about 650MB to download.
 
Good luck,
 
  -AH

Explain how to do this without sudo and I'll edit out your inability to read the OP

you can fix sudo, should be a simple google job

---

### Post by 824957q on 2009-11-11
ok first of all i have k3b and can't download anything else because k3b is not picking up the disc and thats why i need a better copy! and i can't update because it prompts me for a password and when i put in the password it says your username is unknown to sudo so again my main question please

---

### Post by 824957q on 2009-11-11
can i request a cd from linux?  like they mail it to  my house?

---

### Post by delcypher on 2009-11-11
Google is your friend.

[https://shop.canonical.com/index.php?cPath=17]("https://shop.canonical.com/index.php?cPath=17")

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/kubuntu?affiliate=distrowatch]("http://www.osdisc.com/cgi-bin/view.cgi/products/linux/kubuntu?affiliate=distrowatch")

[https://shipit.kubuntu.org/]("https://shipit.kubuntu.org/")

---

### Post by Zoot7 on 2009-11-11
Yes you can, and yes they do. It's free too.
[https://shipit.kubuntu.org/](https://shipit.kubuntu.org/)

---

### Post by 824957q on 2009-11-11
were can i buy a copy of karmic koala to install on my computer

---

### Post by sliketymo on 2009-11-11
http;//www.ubuntu.com

[http://www.ondisk.com](http://www.ondisk.com)

[http://www.distrowatch.com](http://www.distrowatch.com)

for starters.

---

### Post by benerivo on 2009-11-11
Also, it may be included on cover disks of linux magazines.

---

### Post by hansdown on 2009-11-11
Hi 824957q.

You can download the ISO for free.

[http://www.thegeekstuff.com/2009/10/ubuntu-9-10-karmic-koala-released-download-now-or-get-free-cd/](http://www.thegeekstuff.com/2009/10/ubuntu-9-10-karmic-koala-released-download-now-or-get-free-cd/)

Burn it to a CD, and install.

I've seen your other posts, so you may wish to try 9.04.

[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)

---

### Post by mudguts on 2009-11-11
I've seen it on ebay I think..

and even though it is free to download, i can see why people do 'buy' it.  Afterall, I have a 60GB cap per month so pulling down a 700MB file and then burning the ISO etc. etc.  sometimes it's just not worth it when I can spend $5 and get it.

[Buzz Out Loud]("http://www.cnet.com/buzz-out-loud-podcast/") was talking about that the other day on their podcast.

---

### Post by 824957q on 2009-11-11
i have k3b dvd cd burner i pick burn iso file everything loads up then it says that there is no cd inserted hat do i do??? please helpp

---

### Post by stinger30au on 2009-11-11
are oyu using 9.10


if so, log off then log on again

works for me

---

