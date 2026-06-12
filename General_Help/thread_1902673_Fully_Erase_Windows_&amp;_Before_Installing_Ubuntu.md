---
title: "Fully Erase Windows &amp; Before Installing Ubuntu"
date: 2011-12-31
forum: General Help
---

### Post by nick roto on 2011-12-31
I have an old desktop and an old laptop, both running XP but seldom used. I would like to give these extended life; then give one away and install the other in a holiday cottage for general use. I want to ensure there are no possible remnants of any confidential data that might be recoverable. There is no data that I actually need.
I considered Darik's Boot and Nuke to clean the HDDs, then install Ubuntu but wonder whether I may loose anything vital for the new installation. I already have Eraser but can I be sure I've covered everywhere that could possibly contain personal data?
I'd welcome recommendations for the best procedure.
So far I have only used the Try It function to run Ubuntu from CD. What are the disadvantages of installing alongside Windows for now until I am more familiar with Linux, apart from wasted HDD space?

---

### Post by 73ckn797 on 2011-12-31
Formatting and running DBAN or similar tools will over write the drive. May consider running several passes and then repartition and format, then perform the install.

Using gparted from a Live CD you can delete the drive partition(s) and create a new one covering the entire drive.

Installing alongside Windows, the installation will handle that.

---

### Post by nick roto on 2012-01-02
Thanks. But what I really wanted was advice on the best way to proceed given that I want the best performance from my old hardware AND be confident that it contains no recoverable, personal data. If I simply install Ubuntu with the maximum partition size I assume the new OS will take over the whole HDD but will not acyually overwrite the existing data and hence destroy it. If I nuke the HDD first with DBAN would I lose anything the Ubuntu install might need?

---

### Post by decrepit on 2012-01-02
As far as I'm aware linux needs nothing on the hd apart from somewhere to install the MBR and somewhere for the data. I'm fairly sure any cleaning software won't interfere with this.

---

### Post by Mark Phelps on 2012-01-02
> **nick roto said:**
> What are the disadvantages of installing alongside Windows for now until I am more familiar with Linux, apart from wasted HDD space?

To answer this question -- NONE.  The two OSs will run independent of each other.  All you lose is some hard drive space.

---

### Post by nick roto on 2012-01-02
Thanks for the replies so far. I am proceeding cautiously for now, checking whether Ubuntu will do all that I need, so I am still running from CD while I check a few applications. Firefox and LibreOffice (which I'm familiar with anyway) are fine. I tried YouTube which was fine after I downloaded Flash, as prompted.
I tried playing some stored clips but Media Player and Banshee couldn't play any of them (.avi, .wmv, .flv, .mpeg, .mpeg). In some cases I got an error and in others an offer to search for the required plugin, which it then couldn't find. I downloaded VLC and that works. So I'm well on the way to taking the big step!
At one point the OS hung (possibly because I responded to the prompt, "Add VLC Media Player to Launcher?" whilst it was installing). None of the CNTRL+ALT+ combinations freed it - what should I do if this occurs (I had to resort to the power button)?
Perhaps I should re-post that questions.

---

### Post by 73ckn797 on 2012-01-02
Check this link out for media codex: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Have you installed ubuntu-restricted-extras from the repositories?

---

### Post by MG&amp;TL on 2012-01-02
If they were running XP, chances are that they're not gonna be too happy about Unity (Ubuntu's interface), so you might want to have a look at some lighter, faster alternatives to Ubuntu, but still running around the same base, so same apps, etc.

Xubuntu-[http://www.xubuntu.org/]("http://www.xubuntu.org/")

Lubuntu-
[http://lubuntu.net/]("http://lubuntu.net/")

I personally would go with Lubuntu, but that's my personal prejudice.

Running the installer formats the disk, so run DBAN, then run the installer,and it should be fine.

Welcome to *buntu!

---

### Post by nick roto on 2012-01-03
Being completely new to Linux I'm still getting to grips with terms like "repositories" and "ubuntu-restricted-extras". Still, I was practically ready to make the leap, completely discarding (nuking) Windows and forcing myself to learn all I need to know (with help from you guys if necessary).
Then the suggestion to try Lubuntu has intrigued me. I want the lightest (fastest) OS and least cluttered interface. The Unity i/f looks potentially elegant but is unfamiliar and may confuse other, casual users. Do Libuntu and other derivatives keep pace with base upgrades in all important respects?
Thanks for your help so far, I'm (almost) on my way.

---

### Post by MG&amp;TL on 2012-01-03
> **nick roto said:**
> Being completely new to Linux I'm still getting to grips with terms like "repositories" and "ubuntu-restricted-extras". Still, I was practically ready to make the leap, completely discarding (nuking) Windows and forcing myself to learn all I need to know (with help from you guys if necessary).
Then the suggestion to try Lubuntu has intrigued me. I want the lightest (fastest) OS and least cluttered interface. The Unity i/f looks potentially elegant but is unfamiliar and may confuse other, casual users. Do Libuntu and other derivatives keep pace with base upgrades in all important respects?
Thanks for your help so far, I'm (almost) on my way.

Of course, think of *buntu as ubuntu with a different interface and different default applications. 

However, you can install all and any package you choose (assuming you have internet) , and updates will come through at the same time. In fact, Lubuntu uses the same mirrors an U, Ku, and Xu buntu.

On the 'confusing others' front, Lubuntu is good, as it has a "start menu" and a window list. :D

---

### Post by nick roto on 2012-01-04
OK, I'm ready to go - goodbye Windows, welcome Ubuntu!
Note I'm going with Ubuntu, not Lubuntu for now. Downloading Lubuntu seems straightforward but the bit about checking your iso and CD plunged right into command lines and I'm not ready for complications* like that until I've passed my Linux driving licence test. I'll give Lubuntu another thought when I feel qualified, my old laptop has 512MB of RAM, 20GB HD, 2.2GHz Celeron processor so I assume it will cope in the meantime. My old desktop, the next to convert, has 1GB RAM and two HDs (200GB and 120GB).
When I'm comfortable with whichever Linux I end up with I'll dump Vista on my new(er) laptop - can't wait, it's horrible! Then I'll think about a dual-boot system for my current (Win7, quad processor) desktop.
Thanks everyone for getting me to the start line.

*[Ubuntu doesn't worry me with this, perhaps the Lubuntu guys might give it some thought. I'm no computer geek but I've been using computers since 1966, even writing system software (e.g. compilers) until 30 years ago. I'm at least an "average" computer user I'd say.]

---

### Post by nick roto on 2012-01-04
Great, the install crashed! That was after I selected to use the entire drive and REPLACE Windows. Apparently a bug report will be sent somewhere. No idea whether or not old laptop is now a heap of scrap.

---

### Post by nick roto on 2012-01-04
It's OK. I tried again and it installed fine. A bit of a mystery but I'm up and running.

---

### Post by nick roto on 2012-01-04
... and my first impressions are that it's pretty slow. I had hoped for a big improvement on an old XP system (which had slowed with age, like they do) but, although I haven't run any direct comparisons (too late now) it doesn't feel quicker. Maybe I will need Lubuntu.
I installed VLC without problems but then tried "Ubuntu restricted extras" as that looked like it would do Flash and other stuff I'll want - it stalled 80% into the install (unless it's just incredibly slow). So, not great so far but I'll stay with it for now.

---

### Post by MG&amp;TL on 2012-01-04
> **nick roto said:**
> OK, I'm ready to go - goodbye Windows, welcome Ubuntu!
Note I'm going with Ubuntu, not Lubuntu for now. Downloading Lubuntu seems straightforward but the bit about checking your iso and CD plunged right into command lines and I'm not ready for complications* like that until I've passed my Linux driving licence test. I'll give Lubuntu another thought when I feel qualified, my old laptop has 512MB of RAM, 20GB HD, 2.2GHz Celeron processor so I assume it will cope in the meantime. My old desktop, the next to convert, has 1GB RAM and two HDs (200GB and 120GB).
When I'm comfortable with whichever Linux I end up with I'll dump Vista on my new(er) laptop - can't wait, it's horrible! Then I'll think about a dual-boot system for my current (Win7, quad processor) desktop.
Thanks everyone for getting me to the start line.

*[Ubuntu doesn't worry me with this, perhaps the Lubuntu guys might give it some thought. I'm no computer geek but I've been using computers since 1966, even writing system software (e.g. compilers) until 30 years ago. I'm at least an "average" computer user I'd say.]

Ubuntu is probably very heavy on your hardware, especially if you got the latest version.

I have a ex-XP (:lol:) PC that I'm typing this on, running Lubuntu, it boots about three times as fast as Windows if that helps in any way.

Checksums are **NOT** compulsory in any way, they might be a good idea if you're paranoid, but it's essentially non-essential. If I'm honest, I never do it. Btw, you're meant to with Ubuntu too, so not a consideration for Lubuntu. You're meant to for any Linux distribution, it checks you haven't downloaded or burnt the thing badly.

Hope this helps matters.

---

### Post by nick roto on 2012-01-04
MG&TL,
Thanks, you've been especially helpful, and patient.
It looks like Lubuntu will be essential for me then on the old laptop. I guess I'll be OK with the old desktop (AMD Athlon XP2600+ 2GHz processor, 1GB RAM, 200GB main drive).
Sorry to trouble you but is it best to start again with a fresh install of Lubuntu or can it modify what I have, including apps (VLC, etc)?

---

### Post by nick roto on 2012-01-04
Hmm, it may not have stalled. When I eventually closed the Software Centre window I found another requesting I accept a licence for some fonts. I'm not used to such windows being hidden like this. I don't want to compare (against Windows) and complain though this does seem a little odd. I will shut up with new problems while I get used to the system. I guess I need to post new questions in the Absolute Beginner or General categories from here.

---

### Post by MG&amp;TL on 2012-01-04
> **nick roto said:**
> MG&TL,
Thanks, you've been especially helpful, and patient.
It looks like Lubuntu will be essential for me then on the old laptop. I guess I'll be OK with the old desktop (AMD Athlon XP2600+ 2GHz processor, 1GB RAM, 200GB main drive).
Sorry to trouble you but is it best to start again with a fresh install of Lubuntu or can it modify what I have, including apps (VLC, etc)?


Well, you *can* install the "lubuntu-desktop" package, then remove all of the apps that came with ubuntu, but if I were you, it's probably more user-friendly to use a fresh install. Although we can help you either way. :D

Sorry the Lubuntu website isn't very clear, it hasn't had much attention up until now, it was only a proper *buntu this release.

About the hidden terminal window,

a) it's very easy (especially on laptops to click something you shouldn't, and it's not as immediately obvious as on XP, so I might suggest you clicked the software centre window by accident, bringing it to the front?

b) Secondly, ubuntu-restricted-extras is restricted for a reason, we can't legally put it in by default. The curses interface (that's what you saw, sort of text with buttons) is a license agreement you must sign to install the restricted extras. It's really designed for those using a terminal (i.e. it fills your terminal), although it, as you discovered, can be installed from the software centre.


You can install any apps you have already in Lubuntu. Additionally, VLC may not be required, as ubuntu-restricted extras installs the necessary codecs to play most multimedia formats.

Interestingly, I think google chrome (default browser for Lubuntu) has inbuilt flash support, so you shouldn't have to install that either.

hope you have fun, and don't forget to post back with any issues you might have. If they're separate to this thread's objectives, though, best start a new thread. Thanks!

One thing: the software centre is not installed by default in ubuntu, as it's too heavy, so you may want to either install it, or use synaptic, which is a bit of a learning curve, but I managed to figure out what most of the buttons did on my own, back when I was a buntu newb. Ah, those were the days. :D Post if you need help.

---

### Post by nick roto on 2012-01-06
MG&TL, If you're still watching this thread I have installed Lubuntu now and is MUCH faster - thanks. I don't fancy unnecessary learning curves, is the software centre going to slow me down or just take a lot of HD space (20GB on board)? Is synaptic smaller, or faster or both?

---

### Post by MG&amp;TL on 2012-01-06
> **nick roto said:**
> MG&TL, If you're still watching this thread I have installed Lubuntu now and is MUCH faster - thanks. I don't fancy unnecessary learning curves, is the software centre going to slow me down or just take a lot of HD space (20GB on board)? Is synaptic smaller, or faster or both?

The software centre will only slow you down as you run it-all the other times (unlike MS Windows) it will not slow anything down.

It won't take up any more room than any other program, so no worries there. It's just too slow to be installed by default in Lubuntu, but if your 'puter will run it, go for it.

Try synaptic and see if you can get along with it; essentially all you do is hit the search button and search for what you want; then click the boxes alongside the package and choose the option you want (install, remove, upgrade, etc.)

Alternatively, if you do want the software centre:

*LXMenu -> Accessories -> LXTerminal*

A black window will appear, looking a little like this:

```
nick@nickputer:~/$
```

type into the box:

```
sudo apt-get install software-center
```

It will ask you for your password (ensure the window is focussed, i.e. click on the title bar) then type your password. You can't see it, it won't look as if you are doing anything. Press the return key if you are done.

Then it will spit out a load of stuff (basically listing the stuff it needs to fetch so it can run), you just need to read it and press "y", then return.

After a while, and a lot of confusing messages which will become more familiar and interesting after a while, your software centre is installed. Enjoy! (probably under "system tools")

Yup, you just caught me!  ;)

---

### Post by nick roto on 2012-01-06
Thanks. I think I'm going to enjoy Lubuntu and it certainly works fine on my little old laptop, which is more than could be said for full Ubuntu (which I'm attempting to load on a spare disc of my main PC). Looks like I'll have to dismantle the hardware to be sure I know which disc I'm using - can't afford to overwrite Windows (yet?))

---

### Post by MG&amp;TL on 2012-01-06
> **nick roto said:**
> Thanks. I think I'm going to enjoy Lubuntu and it certainly works fine on my little old laptop, which is more than could be said for full Ubuntu (which I'm attempting to load on a spare disc of my main PC). Looks like I'll have to dismantle the hardware to be sure I know which disc I'm using - can't afford to overwrite Windows (yet?))

Well, as always, be careful, and backup stuff before starting. :D

Have fun, and sorry you had a rocky start. :)

---

### Post by nick roto on 2012-01-07
Actually, I wonder whether I might install Lubuntu on my main computer. Although having a 64-bit  quad-core processor at 2.5GHz and 4GB of RAM it should be man enough for  the "full" version it means mentally accommodating a third GUI, and Lubuntu ought to be amazingly fast. I assume Ubuntu itself just gives me a richer GUI and, by default, includes more applications, though nothing I can't add if I need it.
However, it seems (from [http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/](http://cdimage.ubuntu.com/lubuntu/releases/11.10/release/)) that my Intel processor won't run the 64-bit version. Would I be giving up any speed advantage?

---

### Post by nick roto on 2012-01-07
Ah, I see ([https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)) that my processor probably is OK.
P.S. I do a fair amount of video editing and understand 64-bit would be better for this.

---

### Post by MG&amp;TL on 2012-01-07
> **nick roto said:**
> Ah, I see ([https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)) that my processor probably is OK.
P.S. I do a fair amount of video editing and understand 64-bit would be better for this.
Yup, intel processor is fine as long as it's 64-bit. I have one running myself.

---

### Post by nick roto on 2012-01-11
If you're still watching this thread ... I have done almost all I need to utilise my old laptop at the holiday property. The only remaining thing is to launch Chrome at startup so that the property's home page (with its various helpful pages) is there when the PC is switched on. I have tried several things from threads here using the terminal function but they haven't worked. Can you help?

---

### Post by MG&amp;TL on 2012-01-13
> **nick roto said:**
> If you're still watching this thread ... I have done almost all I need to utilise my old laptop at the holiday property. The only remaining thing is to launch Chrome at startup so that the property's home page (with its various helpful pages) is there when the PC is switched on. I have tried several things from threads here using the terminal function but they haven't worked. Can you help?

Sure.

Do:

```
leafpad ~/.config/lxsession/Lubuntu/autostart
```

in a terminal, then type the following in the file:

```
chromium-browser
```

then save the file, login and out again. You should see a chrome window popup. :)

Note that this only works for one user, if you want it to work for all, post back here.

Sorry there isn't a GUI way yet, LXDE is still quite new.

---

### Post by nick roto on 2012-01-13
All working now. Thanks for your help, I hope to improve my knowledge now that I've got a useful system. Better close this thread now as we're way off topic. I'm grateful for the start you've given me.
Nick

---

### Post by MG&amp;TL on 2012-01-14
No problem whatsoever. :D

Would you mind marking the thread solved, up at the top, under 'thread tools'. Thanks!

---

