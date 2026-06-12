---
title: "ibus randomly switches to korean"
date: 2010-10-23
forum: General Help
---

### Post by rudeboyskunk on 2010-10-23
I've been using ibus as my input method for Korean/Hangul for about a year now, and it's always worked fine. However, after doing a fresh install of Maverick, ibus will randomly switch to Korean without me pushing any button. It will also not allow me to add English as an input method, so my key that is designated to switch to Korean is simply used to turn input method on and off, rather than switch between languages.

Any ideas/suggestions?

---

### Post by rudeboyskunk on 2010-10-24
*bump*

---

### Post by kumaryu on 2010-10-24
When you refer to "English as an input method", do you mean Ispell? English normally doesn't require an "input method" as such. Admittedly, I've not had random activation of an input method such as what you describe (Ubuntu Maverick).

I use Ibus with Anthy as an input method for Japanese but turn it off (keys assigned in Ibus Prefs; "Enable or diable...") for English.

---

### Post by ambeginnersearchinginfo on 2010-10-24
Could you please more precise,
what key exactly is it?
(my key that is designated to switch to Korean)
Thank you.

---

### Post by rudeboyskunk on 2010-10-25
> **ambeginnersearchinginfo said:**
> Could you please more precise,
what key exactly is it?
(my key that is designated to switch to Korean)
Thank you.

The key is to the right of the space bar. It is the "Han/Yeong" key (Korean: &#54620;/&#50689;). I'm not accidentally hitting it, because at first I thought that's what it was, but after some careful attention I noticed that's not what it is.

---

### Post by rudeboyskunk on 2010-10-25
> **kumaryu said:**
> When you refer to "English as an input method", do you mean Ispell? English normally doesn't require an "input method" as such. Admittedly, I've not had random activation of an input method such as what you describe (Ubuntu Maverick).

I use Ibus with Anthy as an input method for Japanese but turn it off (keys assigned in Ibus Prefs; "Enable or diable...") for English.

When I had 10.04, it listed Ispell with a big "E" in the list of languages/alphabets/whatever to switch between as my English option, so I could first turn input on/off by doing ctrl+space, then switch between using Han/Yeong (Korean: &#54620;/&#50689;).  Sorry for the confusing explanation, it's like 11:30pm here in Korea and I'm ready to go to bed (I'm an American here teaching English...)...

---

### Post by kumaryu on 2010-10-25
1. There is, supposedly a context sensitive IBus invocation available to apps developers. Not sure whther its relevant but have you noticed what applications are active when the "switching" occurs? Have you tried using:
  im-switch -l
to determine your IBus setup?

2. You should be able to add EN Ispell from IBus preferences.

3. If you are using English and Hangul only, you could try switching IBus on/off as required using keybd shortcuts

---

### Post by rudeboyskunk on 2010-10-26
I can't install EN Ispell because it's not listed. Under Ibus Prefs, in Input Method, the "Select an Input Method" menu has three options - Korean, Chinese, or Other (under Other is only "compose").  So my only input method that I have installed is Korean - Hangul.  So, when I switch between English and Korean/Hangul, I am turning ibus on and off, instead of keeping it on and switching (which I would prefer).

It's all very confusing, I know. It mostly switches when I use Firefox and Openoffice Word Processor (that I know of).

---

### Post by ambeginnersearchinginfo on 2010-10-27
Thank you for your answer!
Do you mean the right Alt key also called Alt Gr key by saying "Han/Yeong" key?
I reviewed the thread and I understand, that you can indeed write Korean characters,
is this correct?
I am already trying to get Korean characters (hangul) on the screen using keyboard input for several months without any success, only English. Even if I have Korean system language and Korean keyboard layout as the unique keyboard layout without any English keyboard layout I get only English. I tried everything, Kubuntu 10.04, kubuntu 10.10, I read what ibus and ispell is, what the menue key etc. is,tried all key combinations mentioned anywhere, found ibus as chosen etc., but no result, only English. And there is so little information about language input in ubuntu/kubuntu on the intternet.
I have no idea what the problem is. I can write Japanese Kana and I tried many other languges successfully, but Korean won't work.
I don't know, why  other languges work and if   I do the same thing in order to get Korean there is no effect, only English. I use Kubuntu and KDE.
I would kindly ask you to give a detailed explanation how did you manage to get Korean characters on the screen by typing on the keyboard.
Thank you very very much!!!

---

### Post by rudeboyskunk on 2010-10-28
Well, I haven't used KDE in about 7 years, so I'm not sure how it would work under Kubuntu.

In Ubuntu using Gnome, I go to System>Administration>Languages (or lang preferences, something like that, I'm booted into Windows atm).  From there, I just install Korean and make sure all the options under Korean are selected.

After that's finished, I go to System>Preferences>[Keyboard] Input Method and go to Preferences, and select Korean/Hangul as an input method.  I then set the &#54620;/&#50689; key (also known as AltGr on some keyboards) as the trigger to either turn ibus on/off or to switch between English and Hangul (which I currently can't do, because it won't list English Ispell as an option to use).

That's how I did it.

---

### Post by ambeginnersearchinginfo on 2010-10-28
Thank you for your answer!
I am not familiar at all with gnome and ubuntu, and here I can't download and burn it in order to see what it looks like for the time being. I burned a kubuntu CD and tried for two months to get Korean input on the screen without any success.
Anyway thank you very much for your answer.

---

### Post by G2k on 2010-10-28
Japanese/Korean were working perfectly for me with the last Ubuntu release but now that I've downloaded the latest Ubuntu my ibus is all messed up and giving me headaches.
Is there some known issue with ibus as of now? I can hardly switch input methods and when I do, I can hardly switch back to English it's driving me insane...

---

### Post by ambeginnersearchinginfo on 2010-10-29
Did you read
[http://ubuntuforums.org/showthread.php?t=1489023&page=5](http://ubuntuforums.org/showthread.php?t=1489023&page=5)
?

---

