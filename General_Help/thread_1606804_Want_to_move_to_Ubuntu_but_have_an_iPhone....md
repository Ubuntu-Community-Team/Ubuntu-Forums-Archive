---
title: "Want to move to Ubuntu but have an iPhone..."
date: 2010-10-27
forum: General Help
---

### Post by sammcj on 2010-10-27
I want to move to Ubuntu full time as I am studying for my RHCE, but have an iPhone.

I am aware you can easily sync music, but I'm worried about syncing:

-Notes
-Contacts
-Applications

I'm looking to move to an android based phone mid next year, but I need to keep working in the mean time.

I *could* VM a OSX86 install but it seems like a bit of a waste of resources / time.

Any ideas? (Other than selling my iPhone which I am considering)

**EDIT: I do use gmail - do you think syncing notes / calendar this way is a reliable option?**

---

### Post by NESFreak on 2010-10-27
I've found google apps to be sufficient enough. However, since at some point you'll still be needing itunes to upgrade to a newer version of ios, I'd still recommend to install itunes in a virtual machine. However osx86 would be a bit of overkill.

I think that virtualbox + [tinyXP]("http://techome.wordpress.com/2008/07/07/xp-is-dead-long-live-tinyxp/") + itunes would be a more resource friendly solution. With tinyXP the virtual machine disk image should stay as small as possible.

---

### Post by scouser73 on 2010-10-27
My suggestion is that you dual boot with Windows/Ubuntu.

---

### Post by sammcj on 2010-10-27
OK I was thinking about this last night,
And call me impulsive but...
I chucked my iPhone up for sale on TradeMe and got $700 for it!
I'm going out today to buy a Samsung Galaxy S 9000 android phone :)

---

### Post by Verbeck on 2010-10-27
> **sammcj said:**
> OK I was thinking about this last night,
And call me impulsive but...
I chucked my iPhone up for sale on TradeMe and got $700 for it!
I'm going out today to buy a Samsung Galaxy S 9000 android phone :)
$700 :shock:

@NESFreak
is that legal?

---

### Post by sammcj on 2010-10-27
> **Verbeck said:**
> $700 :shock:

@NESFreak
is that legal?

Sorry, NZ $700

So, US $520

---

### Post by NESFreak on 2010-10-27
> **Verbeck said:**
> @NESFreak
is that legal?

The link is safe. Its a link to a blogpost about tinyXP it's not a downloadlink.

As to the legality of using tinyXP that's up to you. Most people by now probably have a spare XP licence lying around these days anyway. Now if you were not to have a single XP licence at all, than using tinyXP would indeed be illegal.

---

### Post by sammcj on 2010-10-31
OK... so I really don't think much of Android, it's really un-streamlined and very, very awkward to used when compared to iOS. (Great idea, bad implementation).


-There are no where near enough settings to customise the OS.

-The Apps store is shockingly bad, very hard to find the decent apps (no real categories).

-The UI is (kind of) ugly - You can't change the font size or OS Theme.

-The UI lags at times and feels a bit jerky.

-It's very annoying the apps don't 'sleep' and they actually use resources in the background, which means you're constantly having to kill them off.

-There is no application syncing to your desktop!
-You can't change the bottom for icons.

-There is no 'number sensing' within the UI so you can't click on a phone number in an email.

-The default browser displays websites in their mobile form, doesn't seem to be anywhere you can disable this.

-The email browser often doesn't re-size emails correctly and you have to scroll around the screen to read them. (Pinch to zoom doesn't seem to do anything here).

-Syncing is no easier with Linux than with the iPhone at all!

-As far as the hardware: It felt 'Cheap' and the sound quality / call quality was terrible, not to mention you couldn't see the screen in sunny weather.


It may sound like I'm some sort of hyped up Apple fanboy that's just used to using an iPhone, but seriously, it was missing so many of the things that make a smartphone efficient and well... worth having!

Oh well, I've taken it back and just upgraded to an iPhone 4, which I will sync inside a XP virtual machine for the time being.


**EDIT**: A friend just emailed me this "I thought about this after I spoke to you on it the other day. You sounded like your voice was heavily distorted and then had the volume lowered afterwards. So you were both quiet and distorted"


Sorry to have a bit of a rage,
Most reviews of Android have been favorable, just thought I'd give my two cents.

---

### Post by jocko on 2010-10-31
> **sammcj said:**
> OK... so I really don't think much of Android, it's really un-streamlined and very, very awkward to used when compared to iOS. (Great idea, bad implementation).

Perhaps it's because you're used to iOS?
I have an HTC desire, and I find iOS awkward in comparison to android.

> **sammcj said:**
> -There are no where near enough settings to customise the OS.
Not sure what you need to customize...

> **sammcj said:**
> -The Apps store is shockingly bad, very hard to find the decent apps (no real categories).I've never seen apples app store so I can't compare them, but no real categories? So which "real" categories are missing? And why are the available categories (18 categories of programs, 4 categories of games) not "real"?

> **sammcj said:**
> -The UI is (kind of) ugly - You can't change the font size or OS Theme.
I can change the theme on mine... But that only changes the wallpaper... so you may have a point here (but not a very important one in my book...).

> **sammcj said:**
> -The UI lags at times and feels a bit jerky.

-It's very annoying the apps don't 'sleep' and they actually use resources in the background, which means you're constantly having to kill them off.
This is a symptom of the same thing. If you don't let the os handle it's resources as it's supposed to, you can expect some lags. Once you exit a program it is sent to the background, where it is kept (sleeping) until you need it again or until another process needs the memory space... If you kill a program you also kill everything that depends on that program, so you will get a lag when those things needs to be re-read from the phone's internal memory or SD-card instead of from ram...
Pretty much like a combination of OS X (exiting a program by closing it's window just sends it to the background indefinitely until you terminate it yourself) and standard linux (exiting a program terminates it's processes, but keeps it in a ram cache until you need it again or something else needs the ram space).

> **sammcj said:**
> -There is no application syncing to your desktop!
-You can't change the bottom for icons.
At least on HTC phones there is a sync app (for windows). I've never used it myself as I don't have windows, and don't have any need for syncing anything except e-mail (but that's handled beatifully by gmail...).
And I'm pretty sure you'll find some other syncing apps in the market.

> **sammcj said:**
> -There is no 'number sensing' within the UI so you can't click on a phone number in an email.Here you are very wrong. If there is a phone number on a web page or in an e-mail, just tap it with your finger and the number is sent to the telephone app. At least that's what mine does.

> **sammcj said:**
> -The default browser displays websites in their mobile form, doesn't seem to be anywhere you can disable this.
Not sure if this is done the same way in vanilla android as in HTC sense, but this is how to access the setting in my browser:
Open up the browser, press the menu button, press "Settings", then untick the checkbox next to "Mobile view".

> **sammcj said:**
> -The email browser often doesn't re-size emails correctly and you have to scroll around the screen to read them. (Pinch to zoom doesn't seem to do anything here).Mine resizes the emails to the screen width. Perhaps that's another HTC sense thing that vanilla android doesn't do...

> **sammcj said:**
> -As far as the hardware: It felt 'Cheap' and the sound quality / call quality was terrible, not to mention you couldn't see the screen in sunny weather.Sunny weather is always going to be a problem with an LED (or any other backlight) screen. You just can't make an LED (or light bulb or any other artificial light) that comes anywhere near as bright as a clear day. But with full brightness on my screen I can see it clearly in anything but direct sunlight, so I don't see the problem.


> **sammcj said:**
> It may sound like I'm some sort of hyped up Apple fanboy that's just used to using an iPhone, but seriously, it was missing so many of the things that make a smartphone efficient and well... worth having!

Oh well, I've taken it back and just upgraded to an iPhone 4, which I will sync inside a XP virtual machine for the time being.


Sorry to have a bit of a rage,
Most reviews of Android have been favorable, just thought I'd give my two cents.
I still think most of your problems are because you are used to the iPhone... The rest would probably have been better if you had bought a HTC phone instead of a samsung, as most of the features you complain about are available by default in Sense (and I'm surprised if they are not available in vanilla android, at least they should be available in android market)...

---

### Post by sammcj on 2010-10-31
Sounds to me like the HTC version of Android is a bit better than the Samsung version.

The app store on mine only had three options, None of much had subcategories:

-Applications
-Games
-Downloads

The iPhone 4 is a lot better at dealing with sunlight than the i9000 was.


Mine definitely didn't detect phone numbers in the gmail client.

One other thing that really annoyed me about the Android was that when you got a txt or email, and you see the alert up the top, you swipe to bring down the notification then click on the thing that you're being notified about, read the txt or email / whatever and return to the home screen, at this point you'd expect the notification to clear... but no! you have to go back into the notifications panel and press the clear button! (or you could keep pressing the back button from the message you were in, but that's a pain when you're multi-tasking.)

---

### Post by Verbeck on 2010-10-31
> **sammcj said:**
> 
you have to go back into the notifications panel and press the clear button! (or you could keep pressing the back button from the message you were in, but that's a pain when you're multi-tasking.)

doesnt happen on my htc. but i'v got the sunlight problem and its really annoying :mad:

---

