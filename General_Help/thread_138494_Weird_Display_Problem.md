---
title: "Weird Display Problem"
date: 2006-03-02
forum: General Help
---

### Post by mssm on 2006-03-02
From yesterday I am having a strange problem. I am using kubuntu. I had firefox and emule opened on my computer. As I tried to drag emule window over firefox , it left its imprint all over the screen thus rendering the screen looking dirty, with lines and colored spots appearing everywhere. I thought it's a problem with x-server, so I logged out, in fact rebooted and to my surprise I found that when my computer's BIOS is performing self-test, those colored spots are still there. I was shocked. I had an ATI 9700 video card but I don't have any ATI driver installed. The worst thing came to my mind : is it a problem iwth my video card? I switched off the computer, cleaned the dirts around coolingfan and turned on the computer. Now It didn't show any problem. But again at night I had the same problem, when I tried to open a gnome-terminal.

How can I determine that :
1. It's a problem relted to X.
2. Or, my video card is at fault.

Right now, I am running memtest and it hasn't yet shown any problem.

I am really worried:cry: . Has anybody faced such problem? Any help/suggestion will be really appreciated.[COLOR="Red"][/COLOR]

---

### Post by mssm on 2006-03-02
Anybody?? 

The computer is running under windows for past few hours without any trouble. I am yet to run 3DMark benchmark test. I am certainly sure that it's an issue related related X-server and new KDE 3.5.1.

---

### Post by mssm on 2006-03-02
It now seems now that I have the same problem in windows too. It's getting worse and worse. Whole of my lCD screen is filled with green lines all over; on the browser they turn pink. I am not sure whether it is the video card or LCD screen itself is the culprit. I bought this laptop only 1.5 yrs. back from US and now I shifted to Europe. I don't have any warranty. I don't know what I should do.

---

### Post by carlosqueso on 2006-03-02
That sounds like bad pixels on your screen....can you find another monitor to plug in and try?

---

### Post by mssm on 2006-03-04
[QUOTE=carlosqueso]That sounds like bad pixels on your screen....can you find another monitor to plug in and try?[/QUOTE]

Hi carlosqueso,

Thanks for reply buddy. I have run few tests for dead pixels. On my notebook's forum, somebody suggested me that it's a temperature related problem. Even after doing proper vacuum of the vents where the fans reside, I had the problems both in windows and linux. Now in windows just now I disabled hardware acceleration and the disturbance went off. I am not sure whether it's a temporary phase, since it comes back and forth. I shall post a picture of my screenshot soon.

By the way, does anybody how to stop hardware acceleration in linux? I have an ATI card and have no ATI driver installed.

---

### Post by dermotti on 2006-03-04
If your driver is "radeon" try changing it to "ati"

if its already "ati" try "vesa" driver.

These settings are in your xorg.conf of course.

---

### Post by dermotti on 2006-03-04
You could also do a **sudo dpkg-reconfigure xserver-xorg** , that usually cleans my settings up if im having issues also...

---

### Post by mssm on 2006-03-04
[QUOTE=dermotti]You could also do a **sudo dpkg-reconfigure xserver-xorg** , that usually cleans my settings up if im having issues also...[/QUOTE]

Hi dermotti,

Thanks for your suggestion. Actually I am having the problem in Windows too. If it were problem with xorg why it is happening in Windows, is not clear to me. Moreover, sometime when I reboot, the BIOS test screen appears with letters all in violet whereas it should be white. People suggested me that it might be a temperature issue, fans not working properly, but I am still unable to still trace a single malfunction report. Is there log, or software in linux where I can look for problems?lem?

The weird problem is that sometime the problem just vanishes by itself and I get back my old crystal clear screen. I am using a Sager laptop. Has anybody in this forum faced this problem?

I have attached a screenshot of my desktop when the problem ocurred.

---

### Post by dermotti on 2006-03-05
That looks like bad/overheating video memory. Usually  When a CPU overheats, it will just freeze your screen. When memory is overheating or bad, you get a display like that and weird artifacts......

---

### Post by handy on 2006-03-05
There are no 2 ways about it, your problem is hardware related!

You will not fix it by changing settings or drivers if it is in windoze & Ubuntu.

Because it is a notebook, you can't just swap out the graphics card.  This is the problem with notebooks, we are at the mercy of specialists!

If it is near new, your cooling fan(s) should still be working.  Can you hear fan running or cuting in/out from time to time while the machine is on?

You have a slim chance in my opinion that a faulty fan is causing this.

The LCD screens have no high voltage circuit, so  cooling them really should not be a problem.

I think that in reality your graphics card has packed it in.

On many notebooks these are attached separately via pin & socket to the mainboard, so that will offset the expense, if in fact this is the problem you have?

Sorry if I sound pessimistic, but this is how it looks to me!

I hope that I am wrong, & a fan will do it for you!

---

### Post by mssm on 2006-03-05
Hi Dermotti and Handy,

Thanks a lot to both of you for helping me at this critical juncture. I think you are right since I noticed this problem after the GPU fan vent got clogged with dirt which I didn't clean for sometime. I shall enquire with the reseller(Sager) whether the GPU or its memory can be changed. At least the manual does not show how to upgrade the GPU, though it shows how to upgrade all others. Is anybody familiar with such thing? I have an ATI Radeon 9700 video card with 128 MB built-in memory(Samsung).

I have noticed one thing which I want to share with you : After I upgrade the BIOS(Phoenix) to its latest version, the problem has been drastically reduced, though I am not sure whether it's temporary. But can any bug in old BIOS resurface after 1.5 yrs? There was a bug in the old BIOS, since when I boot into Ubuntu in recovery mode, dmesg usually kept reporting about some BIOS bug.

Final question is : if I have a bad/overheated video memory wil it be reported somewhere in dmesg?

---

### Post by foxmulder on 2006-03-05
Hi,

I have had the same problem with a videocard (GeForce 5600) and it turned out the fan was dead! It overheated to the point where I got exactlty the same problems as you!

Bottomline: the card was DEAD. Since I did not have any warranty on it (older than 1 year) I ended up buying a new one (6600GT).

Whatever you do: make sure they replace the videocard! I gurantee you it will not be reliable anymore once it has been overheating like this!

Good luck!

---

### Post by mssm on 2006-03-05
[QUOTE=foxmulder]Hi,

I have had the same problem with a videocard (GeForce 5600) and it turned out the fan was dead! It overheated to the point where I got exactlty the same problems as you!

Bottomline: the card was DEAD. Since I did not have any warranty on it (older than 1 year) I ended up buying a new one (6600GT).

Whatever you do: make sure they replace the videocard! I gurantee you it will not be reliable anymore once it has been overheating like this!

Good luck![/QUOTE]

Hi foxmulder,

Thanks a bunch for your response. At least I know somebody else had similar type of problem. So muyintuition about the overheated/dead video card. Did you have a notebook or desktop? If notebook, how did you replace it: yourself or through some repair service? Is it easy to do? If I change my video card, do I have to reinstall my OS? Sorry for asking so many dumb questions.

---

### Post by MeWhOeLsE on 2006-03-05
Well from my experience changing a GPU in a laptop is an absolute pain in teh ***.. I've tried to do two different laptops, one had the GPU permanantly affixed into the mobo (the company decided to glue the two very strongly together) and the other had been modified to fit inside the laptop, so a standard replacement wouldn't fit. I think you'll ahve to go back to teh original comapny to get any kind of repalcemnt if thats even possible. But I've heard stories of them cahrging for a whole new Mobo and GFx card in your case. Its really the worse thing that can go wrong with a laptop! :???: 

But on teh bright side... you probably won;t have to reinstall your OS. In ubuntu you might just have to setup xorg again.

---

### Post by handy on 2006-03-05
I have done little work on notebooks, so my knowledge is limited.

Some have removable graphics cards & some don't.  They are always customised for notebooks, so your problem is, that if you want to do the job yourself, you have to find someone to supply you with the component(s) that you need.

This can be hard, but not impossible!

Many authorised service centres, will not supply you with parts, & want to do the work themselves.  If they do, they will charge you for an hour's labour, even though it will take them half that.

If you do the job yourself, be prepared to spend a lot longer than an hour, as you work it out as you go.  Being very careful not to break anything!

If you are a handy type of person, who likes a challenge & doesn't mind a fiddly job, you will probably enjoy it! :KS

All the best...

---

### Post by dermotti on 2006-03-13
You could also see if you could find a utility to adjust hte clock rate of you gpu/memory. You could drop the clock rate down at the expense of performance but it would reduce the heat your hardware is producing.

I think nvidia includes clocking features in their drivers, dunno bout ati.

---

### Post by J77 on 2006-03-13
I've been having this problem recently with my F-S Celsius R and Scenicview LCD...

Will changing the monitor help?

Quite strange cos it only happens when I'm doing something in Mozilla?!?

---

### Post by J77 on 2006-03-16
Have been using my laptop (again Ubuntu) for netwrok type stuff, ie. mozilla, and have had no problem.

Browsed on my desktop again and Mozilla 'crashed' once more - I think at the time it was trying to load xine to view one of those annoying videos that people are starting to embed in webpages :(

Should I be treating this as a Mozilla problem, a Ubuntu problem, or a problem with my desktop overheating?

(My specs are: F-S Celsius R, 2 x dual core 3.4GHz)

---

