---
title: "Boot to blank screen???"
date: 2010-08-14
forum: General Help
---

### Post by II Bo 247 II on 2010-08-14
I went to update my nvidia drivers which didnt go to plan. i first removed my old drivers then dropped back to the console and tried installing the new ones. it didnt work so restarted and after grub my monitor just goes blank then into standby.... :(

How can i reinstall the drivers back??


Mike

---

### Post by wojox on 2010-08-14
When you reboot hold down the <enter> key.

Press 'E'

Add "nomodeset" next to "quiet splash"

Press Ctrl and X to boot

You should now be able to login to your Ubuntu as usual

---

### Post by 23dornot23d on 2010-08-14
I use the method from this link .... when I want to put drivers back ..... it works for me.

[Nvidia Solution]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/")
there are others .... but if you can get to a command line then all of these should be possible to do.

Print them off or write them down first ....... ;)

---

### Post by II Bo 247 II on 2010-08-14
> **wojox said:**
> When you reboot hold down the <enter> key.

Press 'E'

Add "nomodeset" next to "quiet splash"

Press Ctrl and X to boot

You should now be able to login to your Ubuntu as usual

ive tried that but there is no quiet splash. i tried putting nomodeset in anyway but that does not work either.

---

### Post by II Bo 247 II on 2010-08-14
> **23dornot23d said:**
> I use the method from this link .... when I want to put drivers back ..... it works for me.

[Nvidia Solution]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/")
there are others .... but if you can get to a command line then all of these should be possible to do.

Print them off or write them down first ....... ;)

i cant get to the command line. after grub the screen just goes off. i am on a live cd atm though so is there anyway to fix it through this??

---

### Post by 23dornot23d on 2010-08-14
Have you got a lot of free space on your hard drive and how many OS's do  you have on it ?

If you can get to grub .... can you choose safe mode - this menu option should give you a console

to type in the commands .....

---

### Post by II Bo 247 II on 2010-08-14
ive got 2 hdd. one with ubuntu and the other with windows 7 and they both have alot of space on them. yep i can get to grub fine and ive tried getting to the command line through the safe mode option but it just does the same. Blank screen.....

---

### Post by 23dornot23d on 2010-08-14
What I am thinking is for you to do a fresh install of Ubuntu 10.04 or maybe MINT 9 which uses a lot of the Lucid 10.04 files but has it has less problems with graphic drivers
maybe it would help to get you running linux .....you would need to put this in another partition and then either link to your data ..... or pull it across to the new OS .....

Whichever ..... as I do not know how you can easily solve this problem.

It takes 30 mins for a clean install or there abouts .....

We have choices it depends what you want to do ?

or maybe someone else can help here as the options above are what I would do .......

If you do decide to add a new partition and a new OS or the same one .... run the Bootscript file
in my footer and keep it safe somewhere ..... it keeps a lot of useful information.

[Another way I do it is to install a new UBUNTU (same version) over the existing one ,,, 
(but when doing it in choose your own existing Linux partitions - do not put a tick in to format the drives - that way it removes the system files and should leave your data files - this you do at your own risk ..... always backup your data first)
(do this without any guarantees though ..... as the graphic driver may still may be messed up]

---

### Post by II Bo 247 II on 2010-08-14
yer i was sort of hoping i didnt have to do that lol

---

### Post by 23dornot23d on 2010-08-14
Well without being able to get to the command line - other than from the LiveCD 

I cannot think of a way of removing the grub problem and get it by the graphics problem
which is what is probably what it is thats causing this to happen  ....

(even removing xorg.conf will not help here as it happens before that)

Maybe if someone sees this that has had the same problem and can do it from the LiveCD
or try some more searches ...... 

My thoughts on this are that the start GRUB menu should be simple ..... the thing is lots of processing is going on in the background and its here it gets stuck .... 

It starts the graphic drivers up .... in something called plymouth ..... and if these
have gone badly wrong for whatever reason .... this is where it will stop......

Without errors coming back on the screen like in the good old days ...... its hard to work out how to solve the problem ..... black screens tell us very little .....

---

### Post by II Bo 247 II on 2010-08-14
i think its just the fact it has no drivers to go off so if i found a way to reinstall the drivers ide be ok.

---

### Post by 23dornot23d on 2010-08-14
That may work .... as long as the kernel was not changed when you did your initial changes ....
its worth a try .....

Just thinking do you have older versions of the kernel ..... can you boot into a previous one.
( Even so if the drivers are not there or are the wrong ones this will fail too - but a older version will not
be messed with so replacing the original drivers may work for a older kernel as far as I know )

You could spend a lot of time on this and a fresh install takes around 30 mins .....

I have been here many times in my younger days ..... but you will learn things along the way ......

---

### Post by II Bo 247 II on 2010-08-14
the kernel was not changed because i didnt get to install the new drivers. basicaly all ive done is uninstall the old drivers.

---

### Post by wojox on 2010-08-14
Take a look here [Boot to blank Screen]("http://ubuntuforums.org/showthread.php?p=9718935#post9718935")

This is the Nvivdia driver?

---

