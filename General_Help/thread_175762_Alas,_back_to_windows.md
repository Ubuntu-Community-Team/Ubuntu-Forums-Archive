---
title: "Alas, back to windows"
date: 2006-05-13
forum: General Help
---

### Post by LinuX Nova on 2006-05-13
Ok, so this morning, i installed Ubuntu onto a Dell Latitude laptop from 1999 in the hopes that it would rock quite a lot.

Unfortunately, it seems to be running to slow to actually be of any use, so i'm returning to windows soon. I guess this thread is me asking whether there is anything at all that i can do to increase the speed of this, and failing that, to plead the ubuntu people to make an Ubuntu Lite os, cos that would be cool.

p.s. I'm keeping my desktops ubuntu setup of course.

---

### Post by IYY on 2006-05-13
> Unfortunately, it seems to be running to slow to actually be of any use, so i'm returning to windows soon. I guess this thread is me asking whether there is anything at all that i can do to increase the speed of this, and failing that, to plead the ubuntu people to make an Ubuntu Lite os, cos that would be cool.


It's already been done. Ubuntu Lite and Xubuntu are light variations of Ubuntu. The simplest solution is to just switch the window manager. IceWM + ROX for a more traditional look, and Fluxbox if you're willing to go for something a bit different. XFCE is another good choice, it's much lighter than gnome, but still heavier than the other two I mentioned.

Just so there are no surprises, here's what the different window managers look like:

IceWM:

[[IMG]http://img115.imageshack.us/img115/3004/icebuntu1oj.th.png[/IMG]](http://img115.imageshack.us/my.php?image=icebuntu1oj.png)

Fluxbox:

[[IMG]http://img130.imageshack.us/img130/3605/screen101bm.th.jpg[/IMG]](http://img130.imageshack.us/my.php?image=screen101bm.jpg)

XFCE:

[[IMG]http://img130.imageshack.us/img130/7282/282da.th.gif[/IMG]](http://img130.imageshack.us/my.php?image=282da.gif)

---

### Post by LinuX Nova on 2006-05-13
[QUOTE=IYY]It's already been done. Ubuntu Lite and Xubuntu are light variations of Ubuntu. The simplest solution is to just switch the window manager. IceWM + ROX for a more traditional look, and Fluxbox if you're willing to go for something a bit different. XFCE is another good choice, it's much lighter than gnome, but still heavier than the other two I mentioned.

Just so there are no surprises, here's what the different window managers look like:

IceWM:

[[IMG]http://img115.imageshack.us/img115/3004/icebuntu1oj.th.png[/IMG]](http://img115.imageshack.us/my.php?image=icebuntu1oj.png)[/QUOTE]

Well it's not just that, for instance i just measured the time it took to go from login screen to desktop, and the figure is 11mins 43.

---

### Post by IYY on 2006-05-13
I know what you're talking about. I am running Ubuntu with IceWM on a machine from 1997, and the time it takes me to go from the login screen to the complete desktop is around 3 seconds (with Gnome or KDE it took a minute or so) Just try it:

sudo apt-get install icewm

---

### Post by skippy81 on 2006-05-13
Well, what are the specs of the laptop?

Also once the thing finally boots open a terminal and type:

> hdparm /dev/hda

and

> hdparm -t /dev/hda

and post the results. If DMA is disabled then that will double or triple your loading time.

---

### Post by 5-HT on 2006-05-13
Edited. Sorry, misread LinuX NoVa's post and my advice was therefore not appropriate.

---

### Post by LinuX Nova on 2006-05-13
I'll try both, thanks!



EDIT: Once it loads...

EDIT 2: If it loads...

EDIT 3: Beginning to get slightly worried...

---

### Post by IYY on 2006-05-13
You know, you don't need Gnome to use apt-get. Just Ctrl+Alt+F1, and log into a terminal.

---

### Post by LinuX Nova on 2006-05-13
At which point do i do this?

Oh my god, even this command prompt is mega slow!

---

### Post by LinuX Nova on 2006-05-13
W: Couldnt stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt...) - stat (2 No such file or directory)
E: Couldn't find package icewm

---

### Post by IYY on 2006-05-13
Try 

```
sudo apt-get update
```

But the CLI being slow? That's weird. It should be quite fast on a machine twice older than yours. Run 

```
top
```

to see what process is eating up your CPU/RAM.

---

### Post by LinuX Nova on 2006-05-13
CPU(s): 2.8% us, 2.0% sy, 0.0% ni, 0.0% id, 94.5% wa, 0.6% hi, 0.0% si

---

### Post by MetalMusicAddict on 2006-05-13
Can you please post your system specs? ie:CPU, RAM etc...

---

### Post by LinuX Nova on 2006-05-14
How can I find these out?

---

### Post by skippy81 on 2006-05-14
If you give us the model number written on the casing that would be a start. Either that or just type it into google, you should be able to get the specs easy that way.

Did you check the DMA setting by the way? I can't empasise enough how big a difference DMA makes.  My hard disk was accessing at around 3 mb/sec before i got DMA up, it now accesses at around 50.

Oh and also, open a terminal and type

> dmesg and 

> lspci

paste both into the forums - it will help people work out if hardware problems are causing your computer to hang.

---

### Post by LinuX Nova on 2006-05-14
I can't paste, I'll have to type manually, will it take long?

Apparrently the laptop is a Dell Latitude CPx PPX 99125 500Mhz PIII P3 Laptop, if that helps, i'm trying the DMA thing now

---

### Post by LinuX Nova on 2006-05-14
I got a lot of results, is there any specific thing you want to know?

---

### Post by MetalMusicAddict on 2006-05-14
How much RAM do you have?

And not to be a d!ck but "Alas, back to windows" if you really just want help on speeding up your laptop shouldnt have been you title. ;) 
Titles like yours are just another in a long line of windows users having high expectations without reading and doing a little work.

To futher help us how old are you and how much PC experience do you have? Answers to these questions will give us a clue as to how to talk to you.

---

### Post by LinuX Nova on 2006-05-14
Ah, but the title is to specifically engineer people to come and flame me cos they think i'm dissing ubuntu, therefore increasing traffic to the thread, I mean, look at the number of views it's had... clever eh?

I'll check the ram in a sec for you.

Oh, and fyi, i have ben using Ubuntu on my desktop pc for over a year now, so i already had the right expectations, and it's not exactly like i want to go back to M$, ergo the alas.

---

### Post by matthew on 2006-05-14
[quote=LinuX Nova]Ah, but the title is to specifically engineer people to come and flame me cos they think i'm dissing ubuntu, therefore increasing traffic to the thread, I mean, look at the number of views it's had... clever eh?[/quote]Not really. Actually we tend to frown on that sort of thing and would appreciate it if you were to try to think up more appropriate titles in the future. Titles like "Alas, back to windows" may draw crowds, but they are not typically the sort of crowds that are as useful to a person as a good, descriptive title would be (current thread excepted, of course--to all who have given help: good job, guys). 

To minimize silly arguments, foolish distractions and to help people in the future who may encounter the same problem as you have please try to use more useful thread titles. Thank you.

---

### Post by LinuX Nova on 2006-05-14
[QUOTE=matthew]Not really. Actually we tend to frown on that sort of thing and would appreciate it if you were to try to think up more appropriate titles in the future. Titles like "Alas, back to windows" may draw crowds, but they are not typically the sort of crowds that are as useful to a person as a good, descriptive title would be (current thread excepted, of course--to all who have given help: good job, guys). 

To minimize silly arguments, foolish distractions and to help people in the future who may encounter the same problem as you have please try to use more useful thread titles. Thank you.[/QUOTE]

Ok, you are a mod, if you get any spare time, could you please rename it as you see fit?

Thank you.

---

### Post by matthew on 2006-05-14
[quote=LinuX Nova]Ok, you are a mod, if you get any spare time, could you please rename it as you see fit?

Thank you.[/quote]I appreciate your good attitude. Thank you. I have changed the title of the first post, but it may be too little, too late (meaning it may not change the title in the forum listing of threads...but we shall see). It's not a super-huge deal this time. Now you know our preference for the future and as far as I'm concerned your attitude more than compensates for the mistake.

---

### Post by LinuX Nova on 2006-05-14
Thank you. I want to adhere to the rules and to hopefully sort out this problem, and i don't want to offend anyone.

---

### Post by matthew on 2006-05-14
[quote=LinuX Nova]Thank you. I want to adhere to the rules and to hopefully sort out this problem, and i don't want to offend anyone.[/quote]Consider it taken care of. 

Welcome to the community--I wish everyone was as eager to adhere to the [forum policy]("http://ubuntuforums.org/index.php?page=policy") as you are. (See Section II, number 1 for the reason I commented about the title earlier, and thanks again for being so responsive!)

---

### Post by kelsey23 on 2006-05-14
If you are using Linux as a cheap replacement for Windows, you are using it for the wrong reason(s).

---

### Post by LinuX Nova on 2006-05-14
That's a load of bs.

To start with, No, i am not. I am using it because it is reliable, and fast, and did i mention the reliability?

Also, I see no reason why it could not be used as a cheap alternative to windows, as it has everything anyone could ever need.

---

### Post by kelsey23 on 2006-05-14
I'm pretty sure I know what the benifits of GNU/Linux are :-)

---

### Post by Gomek on 2006-05-14
You mention you can't copy/paste, so that means you're probably posting from another computer.  I gotta ask...  is your laptop connected to the internet?  That would probably explain why you can't install icewm.

Also you never posted a good response to what process was eating your CPU/RAM (use top).  Nor did you post how much RAM you have.  Nor did you post whether your DMA is enabled.

---

### Post by LinuX Nova on 2006-05-14
[QUOTE=Gomek]You mention you can't copy/paste, so that means you're probably posting from another computer.  I gotta ask...  is your laptop connected to the internet?  That would probably explain why you can't install icewm.

Also you never posted a good response to what process was eating your CPU/RAM (use top).  Nor did you post how much RAM you have.  Nor did you post whether your DMA is enabled.[/QUOTE]

Nope, cant get my PCMCIA Wifi card to work, which i believe is associated to this current problem.

I will post all that stuff, but could you tell me what i would have to run to get them again?

Also, which maybe of interest, I cant seem to get any repositaries to load in the package manager :S

---

### Post by newpants2003 on 2006-05-14
if i want to swith to XFCE, all my setting for gnome will also working without reconfig? ie, video card, twinview, and all the software i installed in gnome?

---

### Post by dotdot on 2006-05-14
ok linux nova - come on give us the detail.

hw config . ie mem etc then we'll try to help further - can we have no further
'thoughts on windows' please - it's, we'd agree, unecessary noise.

...we're tuned and, yes, you'll be staying :@)

..

---

### Post by IYY on 2006-05-14
> if i want to swith to XFCE, all my setting for gnome will also working without reconfig? ie, video card, twinview, and all the software i installed in gnome?

Your "gnome settings" will not be working. However, your video card, twinview and the software you install while in Gnome does not fall under the "gnome settings" category. These things will work fine.

> Nope, cant get my PCMCIA Wifi card to work, which i believe is associated to this current problem.

I will post all that stuff, but could you tell me what i would have to run to get them again?

Also, which maybe of interest, I cant seem to get any repositaries to load in the package manager :S

Well, it's obvious that you can't get the repositories to load. Most of the repositories (execpt for the CD ones) are designed to download software from the internet to your machine. I think the first thing you'll have to do is get your wifi card to work. If it doesn't work automatically, you'll probably need to use the NDIS wrapper.

---

### Post by LinuX Nova on 2006-05-14
Ok, well when i was installing, I remember a small error message appearing, So i am reinstalling the entire thing. When that's finished (I give it 10 mins more), I'll inform you.

So, just to recap, I'm running:

```
hw config
```
```
ie mem
```

anything else?

---

### Post by LinuX Nova on 2006-05-14
```
hw config
```
gives me -
bash: hw: command not found
```
ie mem
```
bash: hw: command not found

lol, what am I doing wrong?

---

### Post by Gomek on 2006-05-14
Where'd you pull those commands from?  Try running
```
hdparm /dev/hda
```
to find whether DMA is enabled.
```
hdparm -t /dev/hda
```
Will tell you your hard drive's performance (speed).
```
free -m
```
Will tell you your memory information.

---

### Post by learning curve on 2006-05-14
type this in terminal: sudo apt-get update
this will update your resource directories, or places you download from.  then try to get what you need again.  Learning Curve:) 

"If you strike me down, I shall become more powerful than you can possibly imagine."    Obiwan

---

### Post by nocturn on 2006-05-15
[QUOTE=LinuX Nova]I can't paste, I'll have to type manually, will it take long?

Apparrently the laptop is a Dell Latitude CPx PPX 99125 500Mhz PIII P3 Laptop, if that helps, i'm trying the DMA thing now[/QUOTE]

That's strange

I used to have A latitue CPiA, a PII 333 with 128 MB of RAM and it was quite useable with XFCE.

As yours is much faster, it should even be able to do Gnome.  I'm beginning to suspect that something is broken on that machine.

One question though, you do have at least 128 MB of RAM?

---

### Post by hoggbottom59 on 2006-05-15
Seems funny. Must be a configuration problem. Using the Synaptic program have you the correct kernel for your processor?

The only way I've noticed that Linux appears slower is the screen redraws. This is only asthetic anyway and if it is a problem you can use a more minimal window manager as someone has mentioned.

I have a laptop running XP which is a P4 3Ghz. My Linux desktop is an Athlon XP at 1.6Ghz and doesn't seem any slower.

Don't forget it does also matter what programs you are using and if your hardware is fully supported. For example Windows can use a graphics card to draw translucent selections. 

This equivalent feature might not be present in Linux but I think Linux is worth sticking with.

Leon.

---------------------------------------------------------------------
Dapper Drake
Foxconn K7S741MG - Sis963L and Sis741 chipsets.
1.67 GHz Athlon XP
1Gb Memory.
Standard DVD-Rom and monitor.

---

### Post by Googler on 2006-05-15
[QUOTE=IYY]

IceWM:

[[IMG]http://img115.imageshack.us/img115/3004/icebuntu1oj.th.png[/IMG]](http://img115.imageshack.us/my.php?image=icebuntu1oj.png)

[/QUOTE]

how could u make IceWM looks like that

---

### Post by GoodPanos on 2006-05-15
Yeah! Really, how did you make IceWM look like that??!!  :-k

---

### Post by IYY on 2006-05-16
Glad you asked :D 

It's my own theme, based on the one from Dapper. Get it [right here]("http://freshmeat.net/projects/icebuntu/?branch_id=64282&release_id=226919"). The desktop is drawn by Rox-Filer.

---

### Post by GoodPanos on 2006-05-16
Please elaborate.  Steps on how you got shortcuts on the desktop, wallpaper etc.  How does rox-filer work?

---

### Post by IYY on 2006-05-16
First, install rox filer: 

```
sudo apt-get install rox
```

Then, the command to create a desktop is:

```
rox --pinboard=MyPinboard
```

You can substitute "MyPinboard" with any name you like. 

There, now you have a desktop, to which you can drag shortcuts from any rox-filer window, and you can change the wallpaper on it too. What you can't do is store files on the desktop itself.

If you're using Dapper, you already have a very nice icon theme for ROX. Otherwise, get one here:

[http://rox.sourceforge.net/desktop/node/270?PHPSESSID=cc459a954a4bc6fab90ee773918b352a](http://rox.sourceforge.net/desktop/node/270?PHPSESSID=cc459a954a4bc6fab90ee773918b352a)

---

### Post by GoodPanos on 2006-05-17
Thanks for the details.  That makes it easier for us newbies.  :) 

One more question.  Do you have to run rox one time or do you have to run it each time you boot?

---

