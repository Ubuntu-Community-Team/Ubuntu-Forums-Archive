---
title: "Horizontal streaks across the screen?"
date: 2010-05-21
forum: General Help
---

### Post by 8jwong14 on 2010-05-21
In my Ubuntu 10.04, I have strange streaks across parts of my screen.  The interesting thing is that the streaks don't seemed to be in random locations but appear to the left of certain images show on the screen.  I.E.  If Firefox it appears to the [COLOR=Red][COLOR=Black]right[/COLOR][/COLOR] of icons and text and not in blank white spaces.  I forgot when they started to appear but it was recently.  I am sure it is not some sort of affect I set.  Also, I'm sure it is not my monitor since I can take screenshots of my desktop while still preserving the locations of the streaks on the screenshot.  I've also tested my PC with another monitor.  

I'd appreciate help.  :)

Update: Sorry for the confusion but I meant the streaks are appearing to the  right of things not the left as I said before.  My bad.

---

### Post by ryan858 on 2010-05-22
I don't see any streaks... When you screenshot them, can you move the image and they are "stuck" on the image while moving it?

---

### Post by Copperline on 2010-05-22
Hi - unfortunately I can't see any streaks either. However, if you are certain that it isn't your monitor, cables or connections at either end, I think you should check your graphics driver and also check to see if the card/ chip itself is being properly cooled (or not overheating). It is usually possible to find out this information in the BIOS...mine is under PC Health Status. You could also try checking inside the case just to make sure fans are spinning etc. It doesn't take much of a rise to produce distortion as the cooling is often borderline. Does it get worse if you run graphics-intensive software such as a game? Google should tell you what temperatures are the norm but I'd be concerned if mine were 40C or above. Its worth checking anyway just to make sure as it's quick and easy.

Try booting from a LiveCD to see if the streaks are being caused by driver or special effect issue...the LiveCD won't load your effects or your graphics driver and so you'll get a 'clean' install to check if they still appear. If they don't it's an effect or driver issue. If they do, I'd check your cooling on your graphics chip/ card. It is important to note if the streaks are all one colour and if they follow a specific pattern too. 

Also, if you run a system test - System > Administration > System Testing and skip through to the display, you can run a pixel check which will check the consistency of the output from your graphics chipset.

Copperline

---

### Post by 8jwong14 on 2010-05-22
> **ryan858 said:**
> I don't see any streaks... When you screenshot them, can you move the image and they are "stuck" on the image while moving it?
Yeah.  When I move the screenshot, the streaks are on the same part of the image moving with as my desktop which is strange.  Also, as the streaks appear everywhere, on Firefox, streaks often appear to the right of pictures and text not blank spaces.  When I would scroll, the streaks follow and stay in the same position so eventually, the streaks get block out as it is covered by Firefox's toolbars.  This is really strange as from what what I've heard, streaks only occur and stay stationary on screens.

---

### Post by 8jwong14 on 2010-05-22
> **Copperline said:**
> Hi - unfortunately I can't see any streaks either. However, if you are certain that it isn't your monitor, cables or connections at either end, I think you should check your graphics driver and also check to see if the card/ chip itself is being properly cooled (or not overheating). It is usually possible to find out this information in the BIOS...mine is under PC Health Status. You could also try checking inside the case just to make sure fans are spinning etc. It doesn't take much of a rise to produce distortion as the cooling is often borderline. Does it get worse if you run graphics-intensive software such as a game? Google should tell you what temperatures are the norm but I'd be concerned if mine were 40C or above. Its worth checking anyway just to make sure as it's quick and easy.

Try booting from a LiveCD to see if the streaks are being caused by driver or special effect issue...the LiveCD won't load your effects or your graphics driver and so you'll get a 'clean' install to check if they still appear. If they don't it's an effect or driver issue. If they do, I'd check your cooling on your graphics chip/ card. It is important to note if the streaks are all one colour and if they follow a specific pattern too. 

Also, if you run a system test - System > Administration > System Testing and skip through to the display, you can run a pixel check which will check the consistency of the output from your graphics chipset.

Copperline
Thanks for the info.  I tried booting from the LiveCD using the try Ubuntu feature and it still had streaks.  Also, now, Grub 2 also has the streaks appearing to the right of text.

---

### Post by 8jwong14 on 2010-05-22
Sorry for the confusion but I meant the streaks are appearing to the right of things not the left as I said before.  My bad.

---

### Post by 8jwong14 on 2010-05-22
Sorry for posting so much in a row.  

Now I can confirm the streaks are NOT Ubuntu's problems.  I have a dual-boot system and the streaks are also plaguing Vista.  The streaks appear in the same way as in Ubuntu.  

I'm guessing the problem lies with my graphics card or video cards or something like that.

---

### Post by 8jwong14 on 2010-05-22
Thanks for helping me but now, the streaks have disappeared without any human intervention.  I just rebooted into Windows Vista where there were also streaks but then I rebooted again into Ubuntu and now the streaks are gone.  But for future reference, may you please tell me what you suspected went wrong?  However, some areas of my screen still have some blurriness.

---

### Post by Copperline on 2010-05-22
Goodness me...this is rather confusing :)

Your booting from the LiveCD and with Vista showed that the problem was/ is hardware related...rather than software related (because Vista and Ubuntu use different drivers) so I think some issue with your graphics card itself is causing the streaks. 

To my mind (which may be wrong of course and I may be writing a great deal about something wich is not the cause here!) this could be caused by the graphics card simply failing - but I would think based on what you write that this issue is likely due to a temperature issue. Distortion often appears on displays if the graphics chip is not receiving adequate cooling or is getting too hot for the cooling system to manage.

Graphics cards (both integrated chipsets and PCI slot cards) are either passively cooled (relying on air being blown past the heatsinks on them by the case fans) or actively cooled (with a heatsink and fan of their own). Depending on which one you have, it could be the case that cables/ ribbons are in the way of the airflow...dust can cause fans to lose efficiency...this sort of thing.

Graphics chips do also need thermal grease inbetween the heatsink and the chip...this is usually in the form of a thermal pad applied by the manufacturer and over time this can break down causing the thermal transfer to suffer and this can present itself as an intermittent fault.

In trying to sort out this issue, I would first check that the graphics chipset is being properly cooled and that air can get past and around it properly inside the case. If you have a card that plugs in to the motherboard, I would take it out of the slot and clean the copper contacts on the side of it as well as the slot on the motherboard (if possible) with a lint-free cloth and some isopropyl alcohol (cd cleaning fluid would work well if you have some). If not, simply blowing using an air-duster inside the slot would clean out any dust that could be causing a bad contact (I'm afraid I usually use the vacuum cleaner on mine). Thorougly cleaning the motherboard and inside the case would also be a good idea as dust causes all sorts of weird problems if it gets on computer components.

If the heatsink is removable...either on the motherboard or the card, I would clean off and replace the thermal grease on both the heatsink and the chip die (arctic silver ceramique is good for this as it is non-conductive and won't short any diodes close to the chip die if it gets on them). This isn't difficult and is cheap.

If any of this works, it was a temperature issue or a dust problem - if not and it is possible to do so, I'd then replace the card. If you would rather not go through the hassle of trying to fix the issue - you could of course replace the card anyway and see if the issue clears! 

If you don't have a card and you have an integrated graphics chipset - and free PCI express slot, you could try borrowing/ buying a simple plug-in card and seeing if the issue remains when using that. The system will choose the plug-in graphics card over the integrated in this case and you can turn off the integrated in the BIOS.

I'm sorry this sounds like such an epic...but tracing something like this is through process of elimination and it's good practice to start with the simplest, cheapest and most easy to solve things first. That said, if you do end up replacing the card, you are hoping that your motherboard is working properly (and that could be the cause of the fault as well!) so I'd rty and borrow one first if possible.

Apologies for the eaasy :) hope that it helps in some way though!

Cheers
Copperline

---

### Post by ryan858 on 2010-05-22
> **8jwong14 said:**
> Sorry for posting so much in a row.  
Just for future reference, there is an Edit button near the bottom right corner of your posts that you can click, so you don't have to keep making new posts, you can just add to the last one.

And as to what was causing this phenomenon, I believe it was either the monitor or the video card. More likely the card, because the streaks weren't in a fixed position on the screen.

---

### Post by 8jwong14 on 2010-05-24
> **Copperline said:**
> Goodness me...this is rather confusing :)

Your booting from the LiveCD and with Vista showed that the problem was/ is hardware related...rather than software related (because Vista and Ubuntu use different drivers) so I think some issue with your graphics card itself is causing the streaks. 

To my mind (which may be wrong of course and I may be writing a great deal about something wich is not the cause here!) this could be caused by the graphics card simply failing - but I would think based on what you write that this issue is likely due to a temperature issue. Distortion often appears on displays if the graphics chip is not receiving adequate cooling or is getting too hot for the cooling system to manage.

Graphics cards (both integrated chipsets and PCI slot cards) are either passively cooled (relying on air being blown past the heatsinks on them by the case fans) or actively cooled (with a heatsink and fan of their own). Depending on which one you have, it could be the case that cables/ ribbons are in the way of the airflow...dust can cause fans to lose efficiency...this sort of thing.

Graphics chips do also need thermal grease inbetween the heatsink and the chip...this is usually in the form of a thermal pad applied by the manufacturer and over time this can break down causing the thermal transfer to suffer and this can present itself as an intermittent fault.

In trying to sort out this issue, I would first check that the graphics chipset is being properly cooled and that air can get past and around it properly inside the case. If you have a card that plugs in to the motherboard, I would take it out of the slot and clean the copper contacts on the side of it as well as the slot on the motherboard (if possible) with a lint-free cloth and some isopropyl alcohol (cd cleaning fluid would work well if you have some). If not, simply blowing using an air-duster inside the slot would clean out any dust that could be causing a bad contact (I'm afraid I usually use the vacuum cleaner on mine). Thorougly cleaning the motherboard and inside the case would also be a good idea as dust causes all sorts of weird problems if it gets on computer components.

If the heatsink is removable...either on the motherboard or the card, I would clean off and replace the thermal grease on both the heatsink and the chip die (arctic silver ceramique is good for this as it is non-conductive and won't short any diodes close to the chip die if it gets on them). This isn't difficult and is cheap.

If any of this works, it was a temperature issue or a dust problem - if not and it is possible to do so, I'd then replace the card. If you would rather not go through the hassle of trying to fix the issue - you could of course replace the card anyway and see if the issue clears! 

If you don't have a card and you have an integrated graphics chipset - and free PCI express slot, you could try borrowing/ buying a simple plug-in card and seeing if the issue remains when using that. The system will choose the plug-in graphics card over the integrated in this case and you can turn off the integrated in the BIOS.

I'm sorry this sounds like such an epic...but tracing something like this is through process of elimination and it's good practice to start with the simplest, cheapest and most easy to solve things first. That said, if you do end up replacing the card, you are hoping that your motherboard is working properly (and that could be the cause of the fault as well!) so I'd rty and borrow one first if possible.

Apologies for the eaasy :) hope that it helps in some way though!

Cheers
Copperline

Wow.  Thanks for taking all that time to type up all that.  :)  I'll take a look at my PC soon but like I now my screen is perfect again with no blurs or streaks.  If I ever have that problem again, I'll refer back to your post.  Thanks for your time and help.  :)

---

### Post by 8jwong14 on 2010-05-24
> **ryan858 said:**
> Just for future reference, there is an Edit button near the bottom right corner of your posts that you can click, so you don't have to keep making new posts, you can just add to the last one.

And as to what was causing this phenomenon, I believe it was either the monitor or the video card. More likely the card, because the streaks weren't in a fixed position on the screen.

Oops.  Sorry about the multi posts.  I'll be sure to use the edit button next time.  I tried reseting my monitor before and the streaks became less apparent but nevertheless still there.  However, they just disappeared.  In my 14 years of life, those kind of streaks that were not stationary and followed some sort of pattern (appearing to the left of prominent objects on screen such as images and text while not on blank spaces) were the strangest thing I've witnessed.  

Thanks for your help and time too.  :)  Like I said to copperline, I'll be sure to refer back to these posts if the problem reoccurs.  However, I'll open up my PC and take a look just in case.

---

### Post by Copperline on 2010-05-26
> **8jwong14 said:**
> Oops.  Sorry about the multi posts.  I'll be sure to use the edit button next time.  I tried reseting my monitor before and the streaks became less apparent but nevertheless still there.  However, they just disappeared.  In my 14 years of life, those kind of streaks that were not stationary and followed some sort of pattern (appearing to the left of prominent objects on screen such as images and text while not on blank spaces) were the strangest thing I've witnessed.  

Thanks for your help and time too.  :)  Like I said to copperline, I'll be sure to refer back to these posts if the problem reoccurs.  However, I'll open up my PC and take a look just in case.

Not a problem at all...I'm just glad that your problem seems to have resolved itself without much expense or inconvenience to yourself! I've often found it's been during those times that I've learnt things so I'm only too happy to help others! :)

---

### Post by 8jwong14 on 2010-06-01
> **Copperline said:**
> Not a problem at all...I'm just glad that your problem seems to have resolved itself without much expense or inconvenience to yourself! I've often found it's been during those times that I've learnt things so I'm only too happy to help others! :)

Hey again.  My monitor has the problem with streaks again.  I tried your solution and it stopped.  But a few days latter they appeared again.  However, now, they are much less apparent than the first time they even occurred.  I think I might need a new PC...  Oh dear...This is such a hassle with computer problems and so much school work to go with it...  

If it even means much, here is my PC's specs: [http://bit.ly/9v8IQG](http://bit.ly/9v8IQG)
I think that it is the "Intel Graphics Media Accelerator 3100"s fault as it isn't anything high-end nor mid ranging.

---

