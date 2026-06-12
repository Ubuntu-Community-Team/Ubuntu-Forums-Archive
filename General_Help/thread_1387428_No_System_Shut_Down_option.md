---
title: "No System Shut Down option"
date: 2010-01-21
forum: General Help
---

### Post by Speshio on 2010-01-21
My new box: Toshiba T135-S1309, running 9.10 from usb stick.

I'd like to reboot from my first session now after my apparently failed initial attempt to use ndiswrapper to bring my onboard Realtek RTL8191SE to life, but there's no Shut Down option in the System menu.

The system doesn't seem to respond to the 3-finger salute.

Used terminal, sudo halt.

Not an auspicious beginning.

---

### Post by mörgæs on 2010-01-21
But is there a shut-down option in the menu in the top right corner?

---

### Post by Speshio on 2010-01-22
Yes, it's there. I'm sure I tried to click on on it repeatedly earlier in my shake-down session, because that was my initial assumption, but the touch pad on that laptop is not as sensitive as my older anvil, or perhaps it was simple operator error. 

In any event, I read Help & it said use the System menu to shut down.  

Thanks for helping out.

---

### Post by n0dix on 2010-01-22
You can try this in console:
```
sudo init 0
```

---

### Post by Speshio on 2010-01-22
Thanks n0dix

Well, you're certainly quite right about the best way to seek information. It was a bit rash of me to start a new thread on such a trivial issue. But now that it's here...

In the (before) first light of a new day with a fresh cup of coffee, I've regained my enthusiasm for this task at hand, and that is to see if the T135-S1309 will let me make it into a workable Ubuntu (Studio) box with perhaps XP on another partition, and I'd even keep Win7 around too, if possible, just to have it for troubleshooting. 

Obviously I need wireless. Then there is the issue of my wacom tablets. If I can get those going, life would be very sweet.

This box (HP zv5000/amd64) has Mepis 6.2 on the other partition. Getting the wireless to work was a several-day ordeal, but I ultimately failed to get my wacom tablets to function properly under Mepis. Now it's in its death throes (the box, not Mepis) and that's why I'm here under XP while I try to get the wireless going on the new Toshiba.

So, long story, cut to chase. End of 3rd day with this machine on this quest. Success getting machine to boot into 9.10 from usb stick after several failures. Failure on first attempt to blah blah read above.

Let me just say, however, that Ubuntu 9.10 is beautiful on the little Toshiba.

After spending 20 minutes testing the touchpad this morning, I see that it occasionally doesn't respond to tapping, or seems to require more force. Using the left button is much better, but the left and right mouse buttons on the T135's touch pad both reside on the same bar, which is a kind of rocker panel, and there's been a lot of griping about it over on the toshiba forums. It seems if you press in the center rather than at either end of the bar, the touchpad goes haywire.

Did I mention Ubuntu is beautifu? 

Did I mention the Toshiba T135-S1309 is a gorgeous little black razorblade of a laptop with truly astonishing battery life (8-9 hours), a dual-core processor, a usable keyboard, and a brilliant little 13" display?

Were talking big-time Internet Cafe Envy in a sea of glowing apples.

This, on a sub-$500 box.

:D
 
Thanks again for pitching in. There are no doubt many ways to skin a cat in terminal, and I've got a few to learn.

---

### Post by Saiko Berry on 2010-01-22
.. I'm sorry, what?

---

### Post by Speshio on 2010-01-22
Your question?

---

