---
title: "Ubuntu NetBook Help for Complete n00b"
date: 2010-11-13
forum: General Help
---

### Post by Serson_Person on 2010-11-13
Hey All,

I've searched through many posts already on the subject but haven't found a solution.  I'm also a complete n00b when it comes to Ubuntu.  Although I have put Linux on my system many times before, mainly Ubuntu and Fedora, I often bail out because I can't figure certain things out.  I'd really like to keep Ubuntu on my Netbook.

My problem is the Shut Down issue.  Whether it's restart, shut down, close the lid, it freezes during every and any of those situations.  Like I said, I'm not a whiz so some of the other solutions that I found posted on the forums were beyond me.

I have a HP Compaq Netbook.

If there are any other details I can give just let me know.  Sorry to ask again if it's been asked a thousand times but I just really want this to work.  That's why I mentioned "n00b" in the title.  So hopefully you don't go too harsh on me.

:popcorn: Popcorn?

---

### Post by pizza-is-good on 2010-11-13
Harsh? No. We were all noobs at one point. In some areas, we all still are...
Anyway, welcome to the forums!

Can you please describe the freezes? Does the computer fix itself, or do you have to restart?
Do you have the graphics driver for your computer? Which Ubuntu are you running?


~pizza

---

### Post by Serson_Person on 2010-11-13
I'm running Netbook Remix 10.10 I'm fairly certain.  It's the freshest install available from the Ubuntu site as I just got it yesterday.

For the Shut Down or Restart freezes it will show the screen with the Ubuntu logo and the loading dots beneath.  It will get to about the third dot and then stop.  Then nothing will happen regardless of how long I wait.

For the Suspend/Hibernate when I close the lid the screen will be black with either just an underscore in the top left corner or an error message.

I'm not sure about the graphics driver or even the card.  If I knew which application revealed the details I could post them.

I've downloaded all of the Ubuntu updates as well.

Thanks

---

### Post by Win-Smash on 2010-11-13
I had the same problem on my Compaq presario 2500, when you close the top it goes in to hibernate but it would not wake up when you open it. In the Bios there is setting for it to auto hibernate when the lid is closed. Try uncheck this and use the Ubuntu setting to initiate hibernation and wakeup

---

### Post by pizza-is-good on 2010-11-13
Have a look at your power management (System>>Preferences>>Power Management). 

There could be something there that is messing you up.

Also, try this. To shut down, instead of using the icon, open up a terminal window and type ```
sudo shutdown -P now
```. It asks for your password. Type it (you won't see anything being typed).
Does the same problem happen?

---

### Post by Serson_Person on 2010-11-13
I just tried sudo shutdown and same error occurred...

i've been having to hold the power button and shut down the computer that way often in the past two days... do you think it's messing up my hard drive or anything inside the computer?

i'm worried now.  i hope it didn't make a mistake getting ubuntu, lol.  i just really wish i could have it and it worked.

---

### Post by dcstar on 2010-11-14
> **Serson_Person said:**
> I'm running Netbook Remix 10.10 I'm fairly certain.  It's the freshest install available from the Ubuntu site as I just got it yesterday.

For the Shut Down or Restart freezes it will show the screen with the Ubuntu logo and the loading dots beneath.  It will get to about the third dot and then stop.  Then nothing will happen regardless of how long I wait.
..........

You may want to try the 10.04 version if there is a compatibility issue with 10.10 and your hardware.

---

### Post by Serson_Person on 2010-11-14
Sounds good.  I was downloading 9.10, but if 10.04 may work I'll got for that.

---

### Post by Serson_Person on 2010-11-14
Actually,

There a suggestion floating around that you could shut down after logging off, and it works.  I initially dismissed it because somebody had posted after that it only works if you hadn't run a session.

Yet, I ran a session, installed new apps, did some word document stuff and then logged out and shut down fine.

My fingers will be crossed hoping that it stays working like this.

Sorry for any hassles guys, thanks for the help.

---

### Post by Serson_Person on 2010-11-16
Sorry to bother again, the problem has actually returned...

I think I got away with five good shut downs after logging out, but now it just freezes on the Ubuntu exit screen.  :(

---

