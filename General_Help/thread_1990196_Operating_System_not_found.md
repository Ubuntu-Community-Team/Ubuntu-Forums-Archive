---
title: "Operating System not found"
date: 2012-05-29
forum: General Help
---

### Post by bedpotato on 2012-05-29
I dropped my laptop on the floor. :( When I picked it up again, things all appeared to be still working at first, but then after a few minutes things froze up. I could not get any response from the screen, so I just turned it off and back on again. 

When I turned it back on, it wouldn't launch Ubuntu but just went to a black screen with white writing saying the Operating System was not found and something about checking a media cable.  (I am assuming this is probably due to the laptop having been dropped on the floor, and not due to me not having shut things down properly, because I've had to turn it off abruptly before in the past and never got this error message until now).

I have now been able to start up using the LiveCD but what can I do to get Ubuntu back on my laptop permanently? Perhaps I just have a damaged harddrive due to dropping it on the floor and need to buy a new hard drive. Or is this somehow fixable? Should I try re-installing Ubuntu? Or just take my laptop back to the shop and ask them to try and mend my hard drive?

Before I try any of these things, please can somebody expert advise me if there are any commands I should be typing into a terminal in order to find out if things can be fixed?  (I am not very expert at all, and don't know what to do). 

Thank you

Bedpotato xx

---

### Post by fantab on 2012-05-29
Contact your laptop vendor or Service... some cable could have lost footing. Or if you can do it yourself check all cables especially cables that connect to the HDD.

---

### Post by 2F4U on 2012-05-29
Was the operating system running at the time you dropped the laptop? Then the hard disk is likely damaged. If the operating system was not running, you may be lucky. Can you mount the hard drive from the liveCD? If yes, the first thing that I would do is to make a backup of your data.

---

### Post by anonymous5 on 2012-05-29
> **bedpotato said:**
> I dropped my laptop on the floor. :( When I picked it up again, things all appeared to be still working at first, but then after a few minutes things froze up. I could not get any response from the screen, so I just turned it off and back on again. 

When I turned it back on, it wouldn't launch Ubuntu but just went to a black screen with white writing saying the Operating System was not found and something about checking a media cable.  (I am assuming this is probably due to the laptop having been dropped on the floor, and not due to me not having shut things down properly, because I've had to turn it off abruptly before in the past and never got this error message until now).

I have now been able to start up using the LiveCD but what can I do to get Ubuntu back on my laptop permanently? Perhaps I just have a damaged harddrive due to dropping it on the floor and need to buy a new hard drive. Or is this somehow fixable? Should I try re-installing Ubuntu? Or just take my laptop back to the shop and ask them to try and mend my hard drive?

Before I try any of these things, please can somebody expert advise me if there are any commands I should be typing into a terminal in order to find out if things can be fixed?  (I am not very expert at all, and don't know what to do). 

Thank you

Bedpotato xx

You get "Operating OS not found" when there's no OS in the hdd or where there's no hdd, so the problem is definitely the hdd. With the liveCD try accessing the hdd, opening files, creating files...
Or open up disk utility in ubuntu and see if the hdd is detected. If it is you can even try running some tests and viewing smart data. Also, can you hear the hdd spinning ?

---

### Post by Mark Phelps on 2012-05-29
Only a few "hardened" laptops can actually survive being dropped -- and you would know if you had one of those.

The laptop continued to work briefly because it was running from code cached in system memory.  But, when you went to use the hard drive, the laptop failed.

It's also very likely that you suffered a "head crash" on the hard drive when you dropped the laptop.  If that happened, the likelyhood is that nothing is going to be recoverable -- at least,  not using any methods available to you.

Professional recovery services actually disassemble the hard drive, repair the hardware, and reassemble it -- all in "clean room" environments.  Which is one reason they charge THOUSANDS of dollars to recover a drive.

The "shop" is NOT going to be able to fix your drive -- if it suffered a head crash -- no matter what they tell you.

So basically, you most likely need a new drive.

---

### Post by bedpotato on 2012-05-29
> **fantab said:**
> Contact your laptop vendor or Service... some cable could have lost footing. Or if you can do it yourself check all cables especially cables that connect to the HDD.

I don't know what you mean. Thank you for replying though.


[quote=2F4U] Was the operating system running at the time you dropped the laptop?  Then the hard disk is likely damaged. If the operating system was not  running, you may be lucky. Can you mount the hard drive from the liveCD?  If yes, the first thing that I would do is to make a backup of your  data.     [/quote]

Yes it was running while I dropped it. 

I don't know if I can mount the HD from the LiveCD or not because I don't know how to do that.

My data is already backed up on an external HD. There is only one file I hadn't updated some changes to, but I can't seem to find it. (I had a similar problem a while ago on a different thread, and somebody explained to me how to locate my data when accessing Ubuntu via the LiveCD, so I have done that before and ought to know how to do it, but I can't find the data this time. Either I do not know where to look, or perhaps the data has been damaged somehow).

Here is WInh8r's explanation of how I should be looking for it:

[http://ubuntuforums.org/showthread.php?t=1923379&page=4](http://ubuntuforums.org/showthread.php?t=1923379&page=4)

but I can't see "Devices" anywhere this time. 

                                [quote=anonymous5] You get "Operating OS not found" when there's no OS in the hdd or  where there's no hdd, so the problem is definitely the hdd. With the  liveCD try **accessing the hdd, opening files, creating files**...
Or **open up disk utility in ubuntu and see if the hdd is detected**. If it  is you can even try **running some tests** and **viewing smart data**. Also, can  you hear the hdd spinning ?     

[/quote]

Thank you but I'm not sure I know how to do the things in bold. Please can someone not only tell me what to do, but also how to do it? I am a beginner. Thank you. 

I can hear a whirring noise on my laptop. I don't know if that's the HD spinning. I call it a "thinking" noise. It always does a lot of "thinking" when I run Ubuntu via the LiveCD. Will that be the HD?

---

### Post by PeterP24 on 2012-05-29
if the LiveCd is working then most likely you have a problem with your hdd. The best you can do is to check from your LiveCd session if your old hard drive is still alive. I speak from experience - 1 year ago, I dropped an external (mechanical) hdd and suffered because of it. Best choice is to go with a non mechanical one in the future in order to avoid this sorts of things.

---

### Post by bedpotato on 2012-05-29
OK I managed to find Disk Utility and opened it. The following things are there:

Local Storage (Ubuntu@localhost)
SATA Host Adaptor
CD/DVD drive
Peripheral Devices
700 MB File filesystem.squashfs

Is any of them the HD?

:(

---

### Post by bedpotato on 2012-05-29
> **PeterP24 said:**
> . The best you can do is to check from your LiveCd session if your old hard drive is still alive..

Thanks but please elaborate and **tell me how **to do that.  I'm a beginner. Please don't assume I know what I'm doing!Thank you very much everyone for trying to help me.

 >  Best choice is to go with a non mechanical one in the future in order to avoid this sorts of things. 

I had no idea there was any such thing as a "non-mechanical" hard drive. That's interesting. :o

---

### Post by fantab on 2012-05-29
It is possible that the cable that connects to HDD may have come loose, its not plugged in properly after the fall.

Use LiveCD and when you get to the desktop open nautilus or File Manager and from the left column click on the HDD or Ubuntu Partition to mount it. You can also use Disk Utility from the desktop to see how your HDD appears or not.

---

### Post by anonymous5 on 2012-05-29
> **bedpotato said:**
> OK I managed to find Disk Utility and opened it. The following things are there:

Local Storage (Ubuntu@localhost)
SATA Host Adaptor
CD/DVD drive
Peripheral Devices
700 MB File filesystem.squashfs

Is any of them the HD?

:(

Under SATA Host Adapter should have your hdd. If not, then it's not detected. Either it has been disconnected by the impact and/or (I hope not) it's broken.
At this point, you should open the laptop to check if the hdd is correctly connected. If you're afraid of voiding the guarantee or something, contact the manufacturer.

---

### Post by bedpotato on 2012-05-29
> **anonymous5 said:**
> Under SATA Host Adapter should have your hdd. If not, then it's not detected. Either it has been disconnected by the impact and/or (I hope not) it's broken.
At this point, you should open the laptop to check if the hdd is correctly connected. If you're afraid of voiding the guarantee or something, contact the manufacturer.


Oh dear. I don't know how to do any of this... :(

I think I will just have to take it back to the shop. They have a workshop there.

---

### Post by bedpotato on 2012-05-29
Is there no way of me accessing that file? I've got copies of everything else but just hadn't updated the changes to that one. :(

---

### Post by PeterP24 on 2012-05-29
> **bedpotato said:**
> Thanks but please elaborate and **tell me how **to do that.  I'm a beginner. Please don't assume I know what I'm doing!Thank you very much everyone for trying to help me.

 

I had no idea there was any such thing as a "non-mechanical" hard drive. That's interesting. :o

When you go on a LiveCD session, you have access to your hardrive (whose partitions are mounted usually under /mnt/media directory). Check with a live CD if you can see your suspected faulty harddrive.

By non mechanical, I meant hard drive that don't have spinning parts. They are less likely to defect during mechanical shocks. You know, sort of like SSD's.

---

### Post by deadflowr on 2012-05-29
If you are hearing a new buzzing or whirling sound, that is not consistent with what your cd drive sounds like, chances are that sound is comming from the hard drive, if that's the case, the hard drive is probably busted. It can be quite unfortunate as you'll need to replace it. You're smart to have backed up your data externally, though.

---

### Post by deadflowr on 2012-05-29
Two questions. 
First what model laptop is it?
And second, is it under warranty still?
If it is still under warranty, then contact the maker and get it fixed.
 If it is not under warranty, then hopefully the maker has documenation support, which will show you how to remove the hdd. I've found removing hdd from laptops to be the second easiest after removing the battery. If you decide to go this route, when you actually remove the drive, signs of any internal damage should be very apparent, as it will probably rattle like something broken.
Hopefully though, it sounds as if your system has only lost its hdd, and not other components such as graphics cards or cpu or ram of power supply.

---

### Post by bedpotato on 2012-05-29
No I am not hearing a "new" whirring sound. As I explained, when booting up via LiveCD it made the usual "thinking" whirring sound. I don't know what it really means so I have always jokingly said that when the computer makes that noise it's finding something a bit hard and is stopping to think before executing a command. It makes that noise when doing something big: e.g. downloading software, booting via CD. Is that the HD noise?

It's a Fujitsu Siemens Lifebook AH530. It should still be under warranty because I only bought it last Dec. However, I had assumed that warranties did not cover damage due to careless handling (as opposed to faulty components.) It's my fault it got dropped on the floor, not theirs. Will the warranty cover it, do you think? I'd be surprised if so. I will not lie about it, as that goes against my beliefs. I will tell them honestly that I dropped it by accident.

---

### Post by PeterP24 on 2012-05-29
> **deadflowr said:**
> Two questions. 
First what model laptop is it?
And second, is it under warranty still?
If it is still under warranty, then contact the maker and get it fixed.
 If it is not under warranty, then hopefully the maker has documenation support, which will show you how to remove the hdd. I've found removing hdd from laptops to be the second easiest after removing the battery. If you decide to go this route, when you actually remove the drive, signs of any internal damage should be very apparent, as it will probably rattle like something broken.
Hopefully though, it sounds as if your system has only lost its hdd, and not other components such as graphics cards or cpu or ram of power supply.

Nice idea but - I think he should try to recover the data from the (broken?) hdd. Usually data recovery isn't covered by any warranty and it is regarded to be the user responsibility. Sadly, I speak from experience here. Second - dropping a laptop, isn't exactly a fault covered by most of the warranties also: from my experience it usually reduce to: "it was your fault, not ours: pay the repair!". I admit that there are manufacturers like toshiba that can offer you warranties for accidents - or you can buy extra warranties but from what I've encountered, the shops usually don't repair your stuff if it is broken due to an accident.

---

### Post by PeterP24 on 2012-05-29
> **bedpotato said:**
> No I am not hearing a "new" whirring sound. As I explained, when booting up via LiveCD it made the usual "thinking" whirring sound. I don't know what it really means so I have always jokingly said that when the computer makes that noise it's finding something a bit hard and is stopping to think before executing a command. It makes that noise when doing something big: e.g. downloading software, booting via CD. Is that the HD noise?

It's a Fujitsu Siemens Lifebook AH530. It should still be under warranty because I only bought it last Dec. However, I had assumed that warranties did not cover damage due to careless handling (as opposed to faulty components.) It's my fault it got dropped on the floor, not theirs. Will the warranty cover it, do you think? I'd be surprised if so. I will not lie about it, as that goes against my beliefs. I will tell them honestly that I dropped it by accident.

Well, if you go that route and if it is nothing to be done about the internal hdd, then you must expect to loose all the data on it and to pay for a new hdd (plus additional repair fees). A hdd is not so expensive these days - probably your lost data from the hdd worths more.

---

### Post by bedpotato on 2012-05-29
I'm a she, not a he. 

My "helpless clueless female" vibe ought to be a dead giveaway. :D Plus not many men I know quote Anne of Green Gables.

PeterP24: there is no "lost data" because I have everything copied to an external HD and USB, with the exception of one file I'd been working on, whose recent changes I don't think I copied but the gist of it is still there.

---

### Post by PeterP24 on 2012-05-29
> **bedpotato said:**
> I'm a she, not a he. 

My "helpless clueless female" vibe ought to be a dead giveaway. :D

My apologies. We all were clueless at some point. 
Um, the LiveCD method didn't help you to establish if the hdd is faulty or not?

---

### Post by bedpotato on 2012-05-29
Well apparently it was not showing up on Scan Disk. Apparently that's not good. Edit: oops, I mean Disk Utility. I don't know the names of all the things. Sorry. 

I have switched it off now and am on my smartphone...Is there something else I should have tried before switching it off?

---

### Post by PeterP24 on 2012-05-29
Unfortunately that's not good. The remaining possibilities are to either ensure that hdd is connected properly or to go to repair the laptop. But I wouldn't recommend that you check for a proper connection of your hdd in your laptop. There are very little chances that this is the cause of your malfunction - as sata mechanical spinning hdd's are usually tightly secured inside the laptop. Besides, you might ruin your warranty - you should check with the shop (from were you acquire it) policies. 
From a similar experience, I can tell you that if you have important data on the hdd you should:
- demand the repair shop to remove in proper conditions the faulty hdd (if indeed is the hdd)
- go to a data recovery company - they can do wonders, but it can be also very expensive. You might be lucky though - if it is a simple mechanical fault, they will repair it for a reasonable fee. If it is a more serious fault then they would charge you an arm and a leg since they have to open your hdd and move the disk to another hdd using specialised equipment. It really depends on how much you need the lost data but usually for diagnose and for telling a price, those companies don't charge anything. At least here in Romania.

---

### Post by bedpotato on 2012-05-29
Thank you very much for taking the time to try and help me but you seem to be misunderstanding the aspect of data. I've already explained twice that there is no lost data. Everything was backed up save for recent changes to one particular file. This thread is quite long now so maybe you haven't read the part where I explain the data was backed up.  Perhaps you only read the part where I mentioned that one particular file and hence the misunderstanding. 

I know absolutely nothing about the insides of computers so even if I could open it I would be none the wiser. I  will take it to the repair shop tomorrow. Thanks everyone.

---

### Post by PeterP24 on 2012-05-29
> **bedpotato said:**
> Thank you very much for taking the time to try and help me but you seem to be misunderstanding the aspect of data. I've already explained twice that there is no lost data. Everything was backed up save for recent changes to one particular file. This thread is quite long now so maybe you haven't read the part where I explain the data was backed up.  Perhaps you only read the part where I mentioned that one particular file and hence the misunderstanding. 

I know absolutely nothing about the insides of computers so even if I could open it I would be none the wiser. I  will take it to the repair shop tomorrow. Thanks everyone.

I am sorry I missed that. I am relieved you didn't lose any data. Hope it turns out ok for you.

---

### Post by bedpotato on 2012-06-01
Update: the HD cable had come loose. The repair man fixed it for me. All OK now. Hooray!

Thanks for all the advice. 

Bedpotato xx

---

### Post by fantab on 2012-06-01
Thats very fortunate that the cause was not Major. And the issue is solved.

---

