---
title: "Rob's Project: Getting Ubuntu Doing What He Needs"
date: 2010-08-13
forum: General Help
---

### Post by IMAGinES on 2010-08-13
Hi, everybody. Sorry for not posting in a while.

A month ago, I blew my stack over some issues I was having with my current desktop PC setup. At the moment, I run a dual-boot of Windows XP SP3 and Linux Mint. There are some basic tasks I do in one OS that I seem unable to do in the other, and resetting the computer several times a day is winding me up.

I'm hoping that you fine folks might (if you have the time, of course) give me some advice on getting one operating system doing as much of what I want as it can. Although I'm currently running Mint, I'm more than happy to skip back to Ubuntu should Linux wind up being the basis for my system.

Now, I must warn you that I'm still very much a novice to the terminal and the like, and while I'm willing to learn, I'm still leery of solutions that seem overly technical, like OS emulation.

Anyway, to kick things off, here's what I want from my PC, with some notes on how it's working (or not) right now:

- I'm starting to get back into serious writing at the moment, so this is the main thing I want from my PC. I use OpenOffice under Windows as well as Linux and I've been using Dropbox to ensure I'm working on the most current version no matter which boot I'm running. However, if I want to use my Brother MFC-465CN multifunction unit (printer, fax, scanner) I have to boot under Windows; I have no idea how to set it up under Linux and naturally Brother's website isn't the most helpful.

- While I'm writing I'd like to be able to listen to music. My main music collection is on Windows, managed by iTunes, which also manages my podcast subscriptions and syncs with my 8GB iPod Nano. I've bought a couple of tracks from the iTunes Store but I'm not too fussed if I lose access to these.

- Naturally, I browse the web. In theory I can do this under either boot, but I've noticed that Windows seems to manage the multimedia side of the web a little better, especially when I'm trying to play high-def content.

However, since mid-last year, Windows XP has had serious browsing issues. No matter whether I use Firefox or IE, it's a coin-toss as to whether any given site I go to will actually load:

    * Sometimes the browser will load the page title then sit and think.
    * Sometimes it'll partway load the page then sit and think.
    * Sometimes it will give me a 404 or similar for a site other than the one I was trying to get to.
    * Sometimes it'll load the page source, sometimes for an entirely different site than the one I was trying to get to.
    * Sometimes it'll load a single graphic from the page and insist that that's everything.

Stopping the load and refreshing rarely works, either.

Oddly enough, this problem started recurring within a week of the last time I reformatted my hard drive and reinstalled everything.

- I use Thunderbird under Mint, but it's still version 2 and I have no idea when the Mint folks will be updating Mint 8 (Helena). I was starting to like using Version 3 under Windows, but I'm a little paranoid about having my correspondence under that platform.

- I'd like to use Skype a bit more often than I do, as I can't get Linux to recognise the microphone that plugs into my SoundBlaster Audigy 4 and I have no idea whether there's some switch tucked away in alsamixer that I need to flip.

- My mobile phone is a Motorola RAZRv9. In my ideal computing world, I'd like to be able to sync its address book up with Thunderbird, which I can't even do under Windows. I'd also like to access (and maybe even edit) the .amr format voice notes I can make on the phone.

- The last thing I do with my PC is play games, like Dawn of War II, Left 4 Dead and Team Fortress 2. Between writing and my Xbox 360 becoming my main gaming centre, this is becoming less and less of a priority .

Ultimately, I'd like an “at my fingertips” computing experience, where everything I want to do is a handful of clicks and a smattering of seconds away at any given moment. I'd be willing to tolerate a dual-boot setup if all I used Windows for was gaming, though.

So what do you think? Can I accomplish my dream? What will I need to do?

Cheers, folks,

Rob

---

### Post by mastablasta on 2010-08-13
I think - why not stick with Win?
 
> **IMAGinES said:**
> 
However, since mid-last year, Windows XP has had serious browsing issues. No matter whether I use Firefox or IE, it's a coin-toss as to whether any given site I go to will actually load:
 
* Sometimes the browser will load the page title then sit and think.
* Sometimes it'll partway load the page then sit and think.
* Sometimes it will give me a 404 or similar for a site other than the one I was trying to get to.
* Sometimes it'll load the page source, sometimes for an entirely different site than the one I was trying to get to.
* Sometimes it'll load a single graphic from the page and insist that that's everything.
 
Stopping the load and refreshing rarely works, either.
 
Oddly enough, this problem started recurring within a week of the last time I reformatted my hard drive and reinstalled everything.

 
You scanned for viruses? Try reinstalling the broswer? Have you called your ISP?
 
> 
- I use Thunderbird under Mint, but it's still version 2 and I have no idea when the Mint folks will be updating Mint 8 (Helena). I was starting to like using Version 3 under Windows, but I'm a little paranoid about having my correspondence under that platform.
 
It's already updated. Mint 9 is out. Also you can get free encryption tools that will make you much less paranoid.
 
> 
- I'd like to use Skype a bit more often than I do, as I can't get Linux to recognise the microphone that plugs into my SoundBlaster Audigy 4 and I have no idea whether there's some switch tucked away in alsamixer that I need to flip.
 

 
You need to increase mic volume in alsamixer. also mine doesn't work if i use digital sound so i need to use analog duplex for the mic to work. try changing it in the sound preferences.

---

### Post by Drenriza on 2010-08-13
> Naturally, I browse the web. In theory I can do this under either boot, but I've noticed that Windows seems to manage the multimedia side of the web a little better, especially when I'm trying to play high-def content.

On my clean install of Ubuntu Netbook edition i run High def better then on my GF,s windows machine.

> I want to use my Brother MFC-465CN multifunction unit (printer, fax, scanner)
I'm fairly sure this is possible.
edit: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-465CN](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-465CN)
LPR Driver: [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc4800lpr-1.1.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc4800lpr-1.1.2-1.i386.deb&lang=English_lpr)
cups wrapper driver: [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc465cncupswrapper-1.0.1-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/mfc465cncupswrapper-1.0.1-1.i386.deb&lang=English_gpl)

> I use Thunderbird under Mint
Having no problems using this under ubuntu.

>  I'd like to use Skype a bit more often than I do, as I can't get Linux to recognise the microphone that plugs into my SoundBlaster Audigy 4 and I have no idea whether there's some switch tucked away in alsamixer that I need to flip.
Uhm i dont know alot about this, what microphone are you using?

> The last thing I do with my PC is play games, like Dawn of War II, Left 4 Dead and Team Fortress 2. Between writing and my Xbox 360 becoming my main gaming centre, this is becoming less and less of a priority .

Dawn of war II = No
Left 4 Dead = Yes
Team Fortress 2 = Yes

---

