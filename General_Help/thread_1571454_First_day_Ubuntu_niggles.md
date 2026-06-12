---
title: "First day Ubuntu niggles"
date: 2010-09-09
forum: General Help
---

### Post by Paul4763 on 2010-09-09
I've been using Ubuntu for 2 days now and getting used to it but just wanna get a few little niggling things out the way. I'll number them for ease:

1. I'm running 10.04 and I just tried to open "Terminal" for the first time and it just crashed. Is this a common problem? And doesn't Linux keep a log of errors or something?

2. My ASUS notebook has hotkeys obviously designed for windows for volume control and brightness. They worked at first but the last couple of boots have been very sporadic. Firstly the "Fn" key just didn't detect for brightness but worked for volume. Then neither of them worked and when I went to change hotkeys for Ubuntu, it wouldn't even detect the Fn key. Yet it works fine on Windows. Also, running Ubuntu now, it worked for volume and not brightness upon boot but neither are working at time of writing.

3. I usually get speeds of about 500kB+ for P2P torrent-ing on Windows, as do my flatmates sharing the same connection. But using Transmission I get 70kB max, is this common/can it be resolved...?

4. Why does backspace not go back a page on Firefox?!?!?!?!?!

5. Added in last minute. Just tried to watch some YouTube videos and the mouse won't work. I click pause or volume or along the stream but doesn't react or very laggily reacts later?

Thanks

---

### Post by p.s. on 2010-09-09
4. Alt + <left or right arrow> is normally set as forward and back in Firefox. Of course, you can change any of the keys if you want.

---

### Post by Paul4763 on 2010-09-11
Bumpage

---

### Post by DeMus on 2010-09-11
3. Go to [Download]("http://www.ubuntu.com/desktop/get-ubuntu/download") and download the Ubuntu iso file. See if your speed is slower than while using Windows. Using Torrents is not a good way to determine your download speed since you depend on others.

---

### Post by howefield on 2010-09-11
> **DeMus said:**
> 3. Go to [Download]("http://www.ubuntu.com/desktop/get-ubuntu/download") and download the Ubuntu iso file.

Why would he do that ? He is already running 10.04.

@ OP 

For number 4, no it isn't common, but there are several threads on these forums that you can search out or try going to google.com and using something like

```
slow torrents ubuntu site:ubuntuforums.org
```

for your search terms. 


For number 5, have a browse here...

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by hawthornso23 on 2010-09-11
system preferences keyboard shortcuts  

is the place to look for the keyboard issue.  You can configure this stuff a lot more easily in ubuntu. All those weird extra buttons on your keyboard can be made to do basically whatever you want.

---

### Post by DeMus on 2010-09-11
> **howefield said:**
> Why would he do that ? He is already running 10.04.
Just to see how fast is his download from a big server, compared to downloading using torrents. Not to install the software, just find out how fast can he download.

---

### Post by ptptaylor on 2010-09-11
1.
Does it always freeze when you open the terminal or has it only happened once? Like the first time you used it?

2. 
You might want to try and select the keyboard layout in the system -->preferences/administration.

3.
This doesn't sound like a transmission problem. It could depend on a number of factors - try again at a different time of day/different torrent. I have never had any issues with it. Are you connected wirelessly if so is the connection good? What is the max download speed from a standard server?

4. 
Take a look in the history menu in firefox, it tells you the shortcut there.

5. 
You might need to enable/install your video driver. Check the hardware drivers in system-->administration to see if you can enable one or use an updated driver.

---

### Post by Paul4763 on 2010-09-11
1. Terminal has only froze once and that was the very first time I opened it. Seems to be fine now.

2. I've had a play around and now the Fn key seems to work fro everything except the brightness control. I've even customised it so when I press Fn and some other key my mail/browser/app will open. There's just no brightness control in the keyboard options.

3. I've tried a couple of different torrents and the speeds were improved but still not great but then I remembered I've forwarded the ports on Windows but not on Ubuntu. How do I go about opening ports on for Transmission on Ubuntu?

4. Got it!

5. Still a major problem. I went to System--->Admin--->Hardware Drivers, but nothing at all came up. Is it a compatibility issue or do I have download the latest flash or somthing?

Thanks again.

---

### Post by Sin@Sin-Sacrifice on 2010-09-11
The flash thing has a decent work around. Press and hold right click while left clicking what you want to watch. Works for me anyway.

You can open ports using ufw or the gui version gufw.

---

### Post by Paul4763 on 2010-09-11
> **Sin@Sin-Sacrifice said:**
> The flash thing has a decent work around. Press and hold right click while left clicking what you want to watch. Works for me anyway.


Just tried that and the video loaded about 3 seconds before looping those 3 seconds and crashing the whole system altogether :P

---

### Post by TNT1 on 2010-09-11
> **Paul4763 said:**
> Just tried that and the video loaded about 3 seconds before looping those 3 seconds and crashing the whole system altogether :P

Yeah, don't worry though, it's probably a "feature", not a "bug"...;)

---

### Post by zbirdman777 on 2010-09-11
#5 happens to me too, it only happens with old flash videos, new ones work fine. I figure the problem will phase out soon anyway. Especially if flash really does disappear.

---

### Post by JBAlaska on 2010-09-11
Not sure why terminal would crash, you might try konsole:
```
sudo apt-get install konsole
```
Note: the above will install kde libs.

To fix the flash bug:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

**Add the following line [COLOR="Red"]before[/COLOR] the last line of text**

```
export GDK_NATIVE_WINDOWS=1
```

Save and exit the file.

Try Deluge for torrents:
```
sudo apt-get install deluge
```

---

### Post by Paul4763 on 2010-09-11
[[IMG]http://img830.imageshack.us/img830/5741/screenshotaor.jpg[/IMG]](http://img830.imageshack.us/i/screenshotaor.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

Like this for the flash bug? I don't wanna get it wrong :P

---

### Post by JBAlaska on 2010-09-11
Like this:
[img]http://img26.imageshack.us/img26/9817/flashbugfix.jpg[/img]

---

### Post by cgroza on 2010-09-11
Interesting experience you got there? In hardware drivers what do you expect to find? Video Drivers? What graphics card do you have?

---

### Post by demosthenese on 2010-09-11
Backspace in firefox:

in firefox put about:config in the url bar and <enter>

Answer yes to procede after the warning.

put backspace in the filter box

You will be presented with 

Browser.backspace_action

Rightclick->modify

Set to 0

May require restart of firefox.

---

### Post by Paul4763 on 2010-09-12
Cheers guys, backspace works a treat and now YouTube runs smoothly without any problems so thanks for that.

In the meantime, I set up uTorrenet via Wine and was able to forward the ports in the traditional sense although I haven't tested any downloading yet. But I will take a look at Deluge when I get the chance, I had a look at port forwarding on Linux and looks intimidating so I'll take a look in the near future.


> **cgroza said:**
> Interesting experience you got there? In hardware drivers what do you expect to find? Video Drivers? What graphics card do you have?

[http://reviews.cnet.com/laptops/asus-m51a-a1-core/4507-3121_7-33430942.html?tag=mncolBtm;rnav](http://reviews.cnet.com/laptops/asus-m51a-a1-core/4507-3121_7-33430942.html?tag=mncolBtm;rnav)

There's a link to my laptops specs on some website. Not actually too sure how to find specs out on Ubuntu but they are all there on that link.



New problems have arisen though, or should I say problem. Firefox won't stop crashing now. Every 1 in 4 websites I go on crashes it. I tried putting up an item for sale on eBay and every time I clicked the mouse it would hang, ask me to stop a script, then continue until I clicked again, and then hang again, until eventually it just kept crashing. And now it is crashing all the time.

So I tried to install Google Chrome, but upon installation it said that "the packages had already been installed" and when I tried to open google-chrome.lnk, it came up with an error regarding Windows.

Bare in mind I'm running Vista and Ubuntu, via Wubi (is that what it is called?) so they are essentially sharing the same hard drive and Chrome is installed on Vista. Also, on Firefox on Vista I run greasemonkey scripts, so because I'm running Wubi, would this mean there is some crossover and some of the scripts aren't translating well to the Firefox on Ubuntu?

I also made some changes via about:config on Firefox on Ubuntu and when I went on Vista those same changes had been applied.

Thanks again for all your help.

---

### Post by Paul4763 on 2010-09-12
Bumpage

---

### Post by ptptaylor on 2010-09-12
Hmmm, that sounds like a flash problem to me the crashing on random sites - or java script or something. 
Yes you need to install the 'chromium' browser in the ubuntu software centre, that is essentially google chrome for linux.
are you running the windows firefox or something in wine? i don't understand. If you use wubi, it creates 'another' hard drive inside the windows partition and doesn't use files from the windows partition. You should have a different installation for firefox in ubuntu and windows...?
Now I'm quite confused!

---

### Post by Paul4763 on 2010-09-13
Firefox seems to work ok after the YouTube problem was fixed, so once again it was probably a flash problem.

But I don't understand why Chrome won't open. I installed it and I have googlechrome.lnk, but when I try to open it, it says "no such file found" then "There is no Windows configured to opening this kind of file". I found it using the "Search for files..." tool, and all the google chrome files are in my Windows folders. As I said I think that Ubuntu and Vista are sharing one hard drive because I can access ALL of my Windows files.

---

