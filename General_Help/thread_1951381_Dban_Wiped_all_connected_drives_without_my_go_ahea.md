---
title: "Dban Wiped all connected drives without my go ahead."
date: 2012-04-02
forum: General Help
---

### Post by Mi11z on 2012-04-02
Hello well yes the title of the thread says it all. I sent an e-mail to their support address (Darik's Boot and Nuke) which I will now copy and paste below (I really don't have time to edit or rewrite an account of what happened apologies for the lack of punctuation and the overly passionate nature lol I was annoyed and tired at the time.)


> Dear DBAN,

Well, I'm really unhappy and annoyed about this happening and how. Basically I added the dban .iso to a live system USB I had already created using "Multisystem" a linux program which enables you to have and run more than one .iso running live as normal live cd or usb would. I had ubuntu 11.10, linux mint 12 and parted magic alongside dban. Anyway so I restarted my linux mint 11 partition after creating the live usb this time with dban added, entered the boot menu, selected the usb (Sandisk Cruzer), the Multisystem boot loader popped up (as it should) I selected dban from the list and heres where I could have died. Dban loads and searches for usb media as i think it normally would but then! immediately after this it started to wipe all media it found! including itself (the usb drive) It didn't even give me any warning I thought dban normallly loaded up searched for devices, you select your device or run "autowipe" it didn't do this, it loaded , searched for devices and then started wiping straight away! I was in shock, I then quickly turned of my laptop by pressing and holding the power button (not healthy I know) it wasn't far at all in terms of percentage wiped.  Now I'm left with a totally wiped at least formatted hard disk  and it also wiped the usb. It's lucky I had the sense to unplug my removable drive where all my main data is. Although there was no particularly important data on my laptop's hard disk and usb drive I'm left with no operating system at all and will have to do a fresh install. I don't want to do this yet because despite the data not being too important I would still like to recover as much as I can before reinstalling an operating system. Could you please recommend to me some software a method, procedure or someone I can contact to help me recover the data at no charge because this has obviously been a ridiculous inconvenience and I'm quite annoyed!

 Please help!

---

### Post by Paddy Landau on 2012-04-02
Sorry for your problem.

These forums contain several suggestions for programs to recover data lost after an accidental reformat. Search ubuntuforums.org and Google, and choose one to your liking.

Of course, run it from a USB and do not change your hard drive at all until you have recovered whatever you can.

---

### Post by Mi11z on 2012-04-02
> **Paddy Landau said:**
> Sorry for your problem.

These forums contain several suggestions for programs to recover data lost after an accidental reformat. Search ubuntuforums.org and Google, and choose one to your liking.

Of course, run it from a USB and do not change your hard drive at all until you have recovered whatever you can.

Cheers Paddy, thank you for your reply, do you think you could perhaps give me just a little bit more information than that? Perhaps, well what's the most used file recovery program, the best or the best for ease of use? I'll will do some searching on google right now though. :)

---

### Post by winh8r on 2012-04-02
You can have a look at this:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")

and if you want to use it you can install it either via the Software Centre or open a terminal (control + alt + T) and enter this
```

sudo apt-get install testdisk
```

Be sure to read the guide before proceeding, any questions , just ask.

Hope this helps.

---

### Post by Mark Phelps on 2012-04-02
The program dban is designed to "wipe" your drive -- removing all trace of anything there before.  When it works, NOTHING is recoverable from that drive.  If anything was, then dban would be no different than any other partition removal tool.

---

### Post by philinux on 2012-04-02
> **Mark Phelps said:**
> The program dban is designed to "wipe" your drive -- removing all trace of anything there before.  When it works, NOTHING is recoverable from that drive.  If anything was, then dban would be no different than any other partition removal tool.

Indeed. If the OP had just formatted then testdisk will work but dban has nuked it.

---

### Post by winh8r on 2012-04-02
> **Mi11z said:**
> [COLOR="Red"]**Now I'm left with a totally wiped at least formatted hard disk and it also wiped the usb**[/COLOR]

Ahh, I missed that bit! I had understood that you had aborted before it had done the first pass. In that case , I would refer you to the answer given by Mark Phelps above.

Looks like it has gone.

---

### Post by dcstar on 2012-04-03
And this has exactly ***what*** to do with Ubuntu?

---

### Post by Paddy Landau on 2012-04-03
> **dcstar said:**
> And this has exactly ***what*** to do with Ubuntu?
These forums are the most friendly and helpful I have ever had the pleasure to be on. This may not be directly relevant to Ubuntu, but the OP will probably get more help here than elsewhere.

Don't you think?

---

### Post by Mi11z on 2012-04-04
> **Paddy Landau said:**
> These forums are the most friendly and helpful I have ever had the pleasure to be on. This may not be directly relevant to Ubuntu, but the OP will probably get more help here than elsewhere.

Don't you think?

I agree with that. Yes I came here because I knew I would get some help or at least some interest here, straight away. And thanks for all the replies everyone I'll try your suggestions and get back to you.

---

### Post by dcstar on 2012-04-04
> **Paddy Landau said:**
> These forums are the most friendly and helpful I have ever had the pleasure to be on. This may not be directly relevant to Ubuntu, but the OP will probably get more help here than elsewhere.

Don't you think?

No. This forum is **specifically**:

General Help
**All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu and Lubuntu**.

It is not a "General Help" forum for other products, your toaster or your car.

If you have a **specific** complaint about another product - which is exactly what the OP has - then go to their forums.

---

### Post by QIII on 2012-04-04
One cold and rainy day, a haggard, white-haired old man came to my door with an empty bowl asking for rice.

Then i saw the dban button on his shirt ...

---

### Post by Azdour on 2012-04-05
> **Paddy Landau said:**
> These forums are the most friendly and helpful I have ever had the pleasure to be on. This may not be directly relevant to Ubuntu, but the OP will probably get more help here than elsewhere.

Don't you think?

I whole heartedly agree with this. Its the reason why I have stayed with this forum community.

While I agree that the OP and the title was directed towards a complaint about a specific product it did contain a question regarding retrieving the overwritten data on their HDD. Other people replied with suggestions and with the information that maybe they will not be able to get their data back.

If the OP did quickly shutdown their laptop is a chance that some of the data may be recoverable because DBan was not run to completion?

---

### Post by Paddy Landau on 2012-04-05
> **dcstar said:**
> If you have a **specific** complaint about another product - which is exactly what the OP has - then go to their forums.
In that case, go to the first post, press the "Report Abuse" button, and (politely) request that the thread be moved to a different forum of your suggestion. I'm not sure which forum would be more appropriate -- perhaps the [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401")?

But, personally, I think this forum is indeed appropriate, because the most likely help (if any) would be to use an **Ubuntu** Live CD with an appropriate program to investigate and recover.

---

### Post by philinux on 2012-04-05
> **Paddy Landau said:**
> In that case, go to the first post, press the "Report Abuse" button, and (politely) request that the thread be moved to a different forum of your suggestion. I'm not sure which forum would be more appropriate -- perhaps the [Other OS/Distro Talk]("http://ubuntuforums.org/forumdisplay.php?f=401")?

But, personally, I think this forum is indeed appropriate, because the most likely help (if any) would be to use an **Ubuntu** Live CD with an appropriate program to investigate and recover.

Well he was running 11.10 and other stuff and indeed he would have needed the livecd etc to recover.

Personally I would not have moved it anywhere else.

Dban = caveat emptor even though it's free.

---

### Post by Mi11z on 2012-04-06
Hello again fellas,

Just a quick update. I'm using Testdisk through Parted Magic on a live usb and it seems to be working. I seem to have recovered the windows 7 partition by using it. I haven't got round to installing a boot loader yet but now when I boot up it doesn't say "no operating system found" so obviously it recognises that a partition is now there. I'm now performing another deep search through Testdisk and will go ahead with trying to restore my linux partitions. I will then install a boot loader and hopefully all going well, I should be where I want to be, well once was.

---

### Post by xyzzyman on 2012-04-07
You have to type autonuke for it to do anything like what you described. If all you pressed was enter, you'd have to select the drives and press F10. You must have typed autonuke.

EDIT: Unless it was because of multisystem... When I use multisystem, Ubuntu goes straight to a live desktop, instead of giving me the option to install or 'try ubuntu'... It's possible that multisystem is automatically sending you straight to autonuke!

The question is though, why were you even running something as dangerous as dban in the first place? lol

---

### Post by Mi11z on 2012-04-07
> **xyzzyman said:**
> You have to type autonuke for it to do anything like what you described. If all you pressed was enter, you'd have to select the drives and press F10. You must have typed autonuke.

EDIT: Unless it was because of multisystem... When I use multisystem, Ubuntu goes straight to a live desktop, instead of giving me the option to install or 'try ubuntu'... It's possible that multisystem is automatically sending you straight to autonuke!

The question is though, why were you even running something as dangerous as dban in the first place? lol

Haha your right, it was late at night and I thought I'd just test a the new version (of Dban) and like I said I didn't expect it to start wiping straight away. Admittedly it was a poor decision, but as I said it was late and I just had one of those "what's the worst that could happen" moments lol. Lesson learned and well I've also discovered how good and powerful a tool, Testdisk is. :D

*********************************************UPDATE:*********************************************************

Linux Mint partition successfully recovered.

---

### Post by xyzzyman on 2012-04-07
I've wiped out important partitions at 3am by typing an f instead of a g. I've also gotten tired of the time to resize an ntfs partition and cancelled the resize in gparted... Oops. lol

---

### Post by Mi11z on 2012-04-08
> **xyzzyman said:**
> I've wiped out important partitions at 3am by typing an **f** instead of **a g**. I've also gotten tired of the time to resize an ntfs partition and cancelled the resize in gparted... Oops. lol

Do I detect sarcasm? :D There's no need for that. We all make mistakes! :)

God xyzzyman. :lolflag:

I'm just yanking your chain, if your yanking mine.....da da da that's not rhetorical. ;)

---

### Post by xyzzyman on 2012-04-09
No, I was just saying I've made stupid mistakes also and wiped drives. I bet alot of people who've been around the block with OS's over the years have done it one way or another. I got excited and kicked my desk once, and watched my external HDD in slow motion tip over and land on my router. It was just enough of a shock to kill the HDD. Unlike the other times I wasn't able to salvage that data! Pictures and documents regularly get burned to DVD though, so I only lost 120GB's of music and 300-400GB's of movies.

And yes, the onerous is upon you even though multisystem seems to like to skip ahead on things somehow. You were playing with a loaded gun and you shot yourself. :) (I apologize if anyone has lost a family member to an accidental shooting.)

---

### Post by Paddy Landau on 2012-04-09
> **xyzzyman said:**
> I bet alot of people who've been around the block with OS's over the years have done it one way or another.
Too true. I don't remember my last major mistake, but it must have been serious; for many years, I have been extremely careful about making backups!

---

