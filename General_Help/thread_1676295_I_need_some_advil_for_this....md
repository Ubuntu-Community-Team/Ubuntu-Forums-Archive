---
title: "I need some advil for this..."
date: 2011-01-27
forum: General Help
---

### Post by W-Unit on 2011-01-27
Hi there,

I just managed to successfully install Ubuntu 10.4. After much rejoicing (getting it installed was enough of an ordeal in and of itself), I was disheartened to see that so much still needs work.

Btw, I'm working on a degree in Computer Engineering at a highly recognized university, with a 3.8 GPA ... I do have limited *nix experience as I've avoided it like plague up until this point, but my point is I do know my way around a PC. So why is everything SO DIFFICULT?

I had to look up a roughly 2 and a half page long "tutorial" just to install ATI Catalyst. This makes sense to you guys!? Shouldn't an installer just do it all for you? Why am I constantly having to edit this and that config file, chmod this (still no clue what chmod does, and no online source seems willing to give up its mystical secrets) and sudo that? Ugh.

Enough complaining though. Here's the problems I'm looking at right now.

1) I have a very high performance machine which is not performing well at all, particularly in the video department. In Firefox, scrolling up and down a webpage causes vsync issues, where a horizontal line appears on the screen, and one half of the screen will refresh quite noticeably before the other (maybe off by 5ms I would guesstimate). Chrome makes it *almost* unnoticeable. Additionally, dragging any window around the desktop causes this issue 100 times worse - the window takes a good half-second to "follow" the cursor, whereupon the bottom half of the window will appear at its location before the top half.
I have a Radeon HD 5850 GPU. With a little overclocking it runs Crysis maxed out at 30 fps. But it can't drag some windows around on Linux... :P

2) How the hell do I install Flash? It says Chrome comes pre-packaged with it, and that I only have to enable it, but when I try to follow its instructions for enabling it, the "Flash" plugin that supposedly comes prepackaged doesn't show up. In Firefox, I downloaded the .apt file and upon running it was told that it was a virtual package. Whatever that is this apparently means that it simply doesn't work. So how do I get Flash then?

3) Let's say I install a new program. After installing it, I want to run it. In Windows, I would simply open the install directory and find an executable file. However, in Linux, you apparently don't get to know where things are installed to, and even if you do manage to find it, it's all spread out across a ton of different cryptic folders and filenames.
So my question is, is there a general procedure to follow for "finding" something you just installed? How can I not feel like such a dunce? :confused:


Sorry if I come off as narcissistic... I am not accustomed to being beaten by machines :P

I really do appreciate your time and any help you can provide.

---

### Post by amra.sonntag on 2011-01-27
If you are making a degree in computer engineering, it is most likely a good idea to get used to Unix like systems.

3) Things get usally installed into /usr or /usr/locale. But since you aren't supposed to manually mess around in those folders - the executable files should end up in /usr/bin, /usr/locale/bin,... However - the common paths for executable files are set in your shell environment. So you don't have to worry about finding the programm - you just type in the name!

2) While Ubuntu provides a one-click solution for adobe flashplugin. It might not install the right plugin for your cpu architecture. I believe there was a firefox add-on to do the job for you. Or a script for it.

1) This might be a problem with your ATI gpu. The opensource drivers and in most cases also the drivers ATI and Co. provide for linux - just ....
To find a workaround - post in the Hardware section. If you are lucky somebody knows how to fix your issue.

Good luck :P

---

### Post by NightwishFan on 2011-01-27
For the issue with laggy graphics, why not check System -> Administration menu for a program to enable hardware drivers and try the ATI driver from there. In Debian based systems like Ubuntu, handling software is 90% of the time done from repositories, such as the Ubuntu Software Center under applications. Simply search and install flash from there or even just click here (not sure if it works in chrome):
[Install Flash Plugin]("apt://flashplugin-installer")

---

### Post by cascade9 on 2011-01-27
> **W-Unit said:**
> Btw, I'm working on a degree in Computer Engineering at a highly recognized university, with a 3.8 GPA ... I do have limited *nix experience as I've avoided it like plague up until this point, but my point is I do know my way around a PC. So why is everything SO DIFFICULT?

I had to look up a roughly 2 and a half page long "tutorial" just to install ATI Catalyst. This makes sense to you guys!? Shouldn't an installer just do it all for you? Why am I constantly having to edit this and that config file, chmod this (still no clue what chmod does, and no online source seems willing to give up its mystical secrets) and sudo that? Ugh.

Its difficult because you are used to windows. If you were used to using unix/linux/BSD moving to windows would be just as hard. 

A tutorial for ATI catalyst? Hmm, dont take this the wrong way, but thats a perfect example of what I was sayign above. You are used to windows, doing things the windows way. So when you want video drviers, you go to ATI (OK, AMD), go through the selecting what catagory, product line, product model, then OS, thenn d/l the filel. Thats where you started hitting things like chmod (which basicly changes permissions for the file). 

[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

The easy way is just to go system-> administration-> hardware drivers. (this is ubuntu specific BTW). A lot easier than with windows. ;)  

> **W-Unit said:**
> 
Enough complaining though. Here's the problems I'm looking at right now.

1) I have a very high performance machine which is not performing well at all, particularly in the video department. In Firefox, scrolling up and down a webpage causes vsync issues, where a horizontal line appears on the screen, and one half of the screen will refresh quite noticeably before the other (maybe off by 5ms I would guesstimate). Chrome makes it *almost* unnoticeable. Additionally, dragging any window around the desktop causes this issue 100 times worse - the window takes a good half-second to "follow" the cursor, whereupon the bottom half of the window will appear at its location before the top half.
I have a Radeon HD 5850 GPU. With a little overclocking it runs Crysis maxed out at 30 fps. But it can't drag some windows around on Linux... :P

Thats probably a driver issue. I've got machines with far less video card than that and dont have any problems moving windows around, etc.. I've heard of issues with ATI cards and that problem, but how much of that is due to the old 'people only pop up to complain', wrong or bad drivers, or user error I really dont know. 

I cant help you with chrome. I wont use a google proprietary browser (apart from a test every now and again to see how its going) .  

> **W-Unit said:**
> 3) Let's say I install a new program. After installing it, I want to run it. In Windows, I would simply open the install directory and find an executable file. However, in Linux, you apparently don't get to know where things are installed to, and even if you do manage to find it, it's all spread out across a ton of different cryptic folders and filenames.
So my question is, is there a general procedure to follow for "finding" something you just installed? How can I not feel like such a dunce? :confused:

Why do you need to find the program you just installed? It should be in the menu. 

You can find where things are installed, if you have a bit of knowledge about where linux puts the programs.

---

### Post by weedeater64 on 2011-01-27
Too sleepy to read the whole post, but here is an excellent explanation of chmod and ls, and how to use them together.

[http://catcode.com/teachmod/index.html](http://catcode.com/teachmod/index.html)

---

### Post by sidzen on 2011-01-27
See: [ http://linux.oneandoneis2.org/LNW.htm]("http://linux.oneandoneis2.org/LNW.htm")

---

### Post by clhsharky on 2011-01-27
W-Unit

Welcome to Ubuntu(linux), glad to see ya want to learn more about computers. Linux is every now days and is used by everyone even if the don't know it. I suspect you already know that.

Thinking a desktop should be like windows is what you were taught,
learning Linux will teach you even more.

Hang in there


Sharky

---

### Post by djeikyb on 2011-01-27
Linux is completely different from Windows. If you're used to windows (or osx), then linux will have a higher learning curve than if you were just encountering computers. I know you have problems, and you want them to just be fixed right now, but long term, you should read a few introductions to linux. Get used to the directory layout. Get used to the common commands. Read the manual. You had to do the same when you first picked up windows. It's just now, you have to learn a second language.

[http://tldp.org/LDP/intro-linux/html/](http://tldp.org/LDP/intro-linux/html/)
[http://info.ee.surrey.ac.uk/Teaching/Unix/](http://info.ee.surrey.ac.uk/Teaching/Unix/)

I love the how-to articles from tldp, the second link I just found on google. Maybe someone else has a favourite linux guide for noobs?

> **cascade9 said:**
> I've heard of issues with ATI cards and that problem, but how much of that is due to the old 'people only pop up to complain', wrong or bad drivers, or user error I really dont know. No, it really has been that bad. Otoh, since I installed xorg-edgers bleeding edge X, my puny Radeon x300 has been performing nearly as good as in Windows.

---

### Post by mastablasta on 2011-01-27
Hmm a computer engineer that just jumps into it without reading documentation? where is the world going these days?!
 
Anyway suggested read is at least Ubuntu manual or Ubuntu pocket guide (a bit older free e-book).
 
And if you want to learn more about commands there is another very good free e-book available at: [http://linuxcommand.org/](http://linuxcommand.org/)
 
You know for those of us that weren't born with the knowledge of OS commands.
 
chmod is sorft of like attrib in dos. you would have spotted it if you ever uploaded files via FTP to linux server.

---

### Post by migs73 on 2011-01-27
> **W-Unit said:**
> So why is everything SO DIFFICULT?

I think the word you are looking for is DIFFERENT, not difficult.

It is different because it is different, read the link from sidzen above, it won't make things easier for you, but could change you're expectations.

---

### Post by t0p on 2011-01-27
> **mastablasta said:**
> Hmm a computer engineer that just jumps into it without reading documentation? where is the world going these days?!

LOL!  Whenever I get a new device or toy to mess with, I usually throw the "destructions" into the corner with the packaging n stuff.  Then, after a few hours trying to make the damn thing work I'm on my hands and knees rooting through the trash looking for the damn documentation.

Linux documentation is available online.  It's a bit diffuse sometimes, but [The Linux Documentation Project]("http://tldp.org"), [help.ubuntu.com]("http://help.ubuntu.com") and these forums usually come up with the goods.  If not, well [Google *is* your friend]("http://bit.ly/bAHnK2").
 
Linux isn't harder than Windows, it's just *different*.  In many ways it's better - for instance, the Synaptic/apt-get way of installing software beats Windows method every time.  But you are used to the Windows way, and now you've got to learn another way.  Remember, you weren't *born* with Windows skills.

In the OP you say you're studying for a Computer Engineering degree, but you've been avoiding *nix like the plague.  I think you ought to get that seen to.  Linux, *BSD and the rest of it are all out there, beavering away behind a Windows front-end; if you want to work in computing I'd say a solid base in *nix-stuff will stand you in good stead even if you hate the stuff.  Bite the bullet - it ain't gonna hurt much.

Oh, one more thing: **Welcome to Ubuntu!**  Hope you stick around.

---

### Post by W-Unit on 2011-01-27
Thanks for all the replies, guys :) it's truly encouraging, really helps to offset my frustration with the whole process #-o

So in my original post I said that I had limited *nix experience... well, I do have some. At various times I've been required to use it to some degree (mostly to make sure that my C++ programs will compile on a *nix compiler), and just in general I've picked up what I feel like is a pretty good deal of knowledge about commands, a little bit about filesystem structure, etc. When I have to use an existing, already-set-up linux system to create, compile, and run programs, I'm just fine. And it's typically all command-line based so I feel fairly comfortable with that. In fact I feel far more comfortable using the command line on Linux than using its GUIs, because at least with the command line, I have some idea what I'm doing at each step of the way - the GUI just executes a batch of commands for you and doesn't tell you about it, then when it's all said and done it leaves what just happened a complete mystery.

What's frustrating to me is that, I'll find a Linux tutorial, and it will cover such topics as how to edit text files, navigate the filesystem, shell variables, etc etc... all of which I either already know or have no interest in (i.e. shell variables... if they ever come into play, I'll look them up then, but until then I couldn't care less).
The kind of topics that aren't covered? How to actually install linux when things don't go the way they're supposed to. Why things aren't going the way they're supposed to, or how to find out why. How to fix terrible video performance. How to get flash working. What a "virtual package" is and why that apparently means you've failed to do something. How to update drivers. How to install packages you download from the web or with a GUI program instead of through apt-get (there are clearly a number of different ways depending on how the package is.. er.. packaged) or some other command-line alternative.

In other words, I have trouble putting the information from Linux tutorials to practical use, because it all seems to address the problem of how to use a system that is working perfectly, but for me, the problem arises from the system not working right or needing some attention - if everything were going smoothly, I wouldn't be asking for help ;)

Thanks again for the speedy replies and information. I will of course still give those tutorials a look (I've already glossed over one or two) and hopefully learn something. God knows I've much to learn :)

Also here's a nice demotivational I found that pretty much expresses my feelings at this point... hopefully I can prove it wrong :D

---

### Post by QLee on 2011-01-27
[QUOTE=W-Unit]Thanks for all the replies, guys :) it's truly encouraging, really helps to offset my frustration with the whole process #-o
...[/QUOTE]

Well, if your "approach" had been different perhaps you would have received more sympathy and "hand-holding". You spent half of your first post telling us how smart you are and what a good university you go to and then insinuating that because of your intelligence Ubuntu should be easy for you, thus the problem must be with Ubuntu. You're doing this to an audience most of which is people who aren't necessarily high IQ and who did not attend a really good school but who can install and run Ubuntu just fine. 

I wonder what other useful aspects of your life did not require learning new things and a bit of experience before they became "easy". You are a student of computer engineering, you should have an expectation that you will have to learn something new. You don't know your way around a pc, you know your way around a Windows pc, there is a difference.

[QUOTE=W-Unit]Sorry if I come off as narcissistic... I am not accustomed to being beaten by machines :razz:[/QUOTE]

Sure, we recognise this, see it often, people who are adept with Windows are often the hardest to help because they are set in their methods and expectations. In GNU/Linux operating systems the differences often make more sense after one becomes familiar with how the system works.


[QUOTE=W-Unit] I really do appreciate your time and any help you can provide.[/QUOTE]

I hope that is true, I didn't write this to patronise you, just to spur your thoughts.


Here are a few links that could prove helpful in your understanding:

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows/Philosophy)
[http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Ownership and permissions of vfat / ntfs are set at the time of mounting.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Some people from the Ubuntu community have put in quite a bit of effort to produce this manual as an easy for a beginner to understand step-by-step, with pictures, for reference to common tasks.
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by irv on 2011-01-27
QLee, this part of your post caught my eye.

> Well, if your "approach" had been different perhaps you would have received more sympathy and "hand-holding". You spent half of your first post telling us how smart you are and what a good university you go to and then insinuating that because of your intelligence Ubuntu should be easy for you, thus the problem must be with Ubuntu. You're doing this to an audience most of which is people who aren't necessarily high IQ and who did not attend a really good school but who can install and run Ubuntu just fine. 

I agree with you because I am one of those guys who does not have a high IQ. In fact I didn't even finish High School, because I ended up in the military at 17 many many years ago. I did work my way up into a nice Job (when I was still working). Got into computer in the 70's. I go back to the days of DOS. After going with Win 3.0, 3.1 and all the rest of Windows OS's I moved on to Unix/Linux. Yes, there is a learning curve but once you see how much better *nix is to Windows you find yourself understanding computer at a much lower level. And this is a good thing. I find most guys and gals that know computers are self-taught because they have taken to computer like a duck takes to water.

I have a little advice for W-Unit, Don't get into Computer Engineering for the money or knowledge, but because you love what you are doing. When I was still in the work force I loved what I was doing and really enjoyed going to work everyday, and by the way I was one of those IT' guys. 
I wish you the best as you start out in life and Linux is a great way to start. Windows will be around for awhile, but so will Linux and I feel it will be the future, just look at all the devices coming out that are powered by Linux. And the product lines are growing day by day.

---

### Post by W-Unit on 2011-01-27
> **irv said:**
> I have a little advice for W-Unit, Don't get into Computer Engineering for the money or knowledge, but because you love what you are doing. When I was still in the work force I loved what I was doing and really enjoyed going to work everyday, and by the way I was one of those IT' guys.
Good news - I do love it :) I absolutely love programming and writing software. I started learning Java when I was 12 and wrote programs as a hobby up until my junior year of high school when I was finally able to start taking classes for it. I can't tell you how many times, in how many languages, I've written different implementations of Dijkstra's Algorithm, simply because I enjoy doing it.
Just because I was frustrated with Linux doesn't mean this isn't what I want to do ;)

> **irv said:**
> I wish you the best as you start out in life and Linux is a great way to start. Windows will be around for awhile, but so will Linux and I feel it will be the future, just look at all the devices coming out that are powered by Linux. And the product lines are growing day by day.
Thank you, and I agree entirely. Which is why I'm quite determined to learn Linux, however aggravated I might get along the way. Just yesterday I ordered a netbook online, which does not come with any preinstalled OS, and I plan to run Linux exclusively, at least for a while, the goal being to rather force myself to learn ;)

I do apologize for the negativity in my original post... I was rather furious at the time, however I want to be clear - I know my problems aren't Linux's fault but the fault of my own ignorance, and I'm rather determined to learn here :)
After all, there's gotta be SOME reason so many people love it... maybe I will, once I get it figured out :D

---

### Post by djeikyb on 2011-01-27
Heh. It's overwhelming for us too when we have a single post requesting help for several disparate problems. It's actually better to have several shorter posts with titles that reflect the general topic of the problem. I know, this is more talk and still not helping your list of aggravations. Gotta run to school, I try and help directly when I get back, if no one else has.

RE: Flash. I know 64bit flash has/had some weirdness. I haven't installed a 64bit distro on my machine yet, so I don't have direct experience. However, I found the best way to get flash working on my 32bit system is to download directly from Adobe. Some browsers function better than others regarding youtube in particular. Chrome > Firefox > Opera.

---

### Post by W-Unit on 2011-01-27
> **djeikyb said:**
> RE: Flash. I know 64bit flash has/had some weirdness. I haven't installed a 64bit distro on my machine yet, so I don't have direct experience. However, I found the best way to get flash working on my 32bit system is to download directly from Adobe. Some browsers function better than others regarding youtube in particular. Chrome > Firefox > Opera.
How do I properly do this? When I try, I get the "virtual package" problem described earlier. The version I'm trying to install didn't specify that it's 32bit, but I assume it is, because I didn't click on the "try the experimental 64bit version" link.


As regards the video card issue, I've created a separate thread for this:
[http://ubuntuforums.org/showthread.php?t=1676662](http://ubuntuforums.org/showthread.php?t=1676662)

Additionally, attached is a screenshot of what happens when I go to System > Administration > Hardware Drivers. I find this to be profoundly odd, since all it tells me is that I'm using a proprietary video card driver from ATI. There are also no visible configuration options as far as I can tell. What if I wanted information about other drivers? What if I want to configure drivers? :P

Thanks :)

---

### Post by NightwishFan on 2011-01-27
I never used ATI, but I know there is a catalyst control panel in the software center, named: "fglrx-amdcccle"

Though to my experience the open source driver is overall better. If you have problems you might want to try removing the proprietary driver, just see which of the two options is best for you.

---

### Post by mdshann on 2011-01-27
Maybe you should remove it and restart the machine, go back into hardware drivers and install the one listed as recommended. I have a HD2400 with 128 MB Ram and have no issues so I don't thinks it's a gpu problem but a driver problem... specifically if you had to use the command line to download and install from ATI directly instead of from the Ubuntu repositories. 

For Flash, go to System > Administration > Synaptic Package Manager and search for it. Pick the one from adobe, not gnash or whatever open source reverse engineered thing that comes up. You can also try the Software Center under Applications > Ubuntu Software Center. Much easier to use but not all packages are listed and not as powerful as Synaptic.

Another piece of advise is when you are trying to find out how to do something, make sure the reference or how-to you are using is for Ubuntu, and even better for the version you are using. Different distributions have different ways of doing things, and different versions of Ubuntu have different ways as well. If you have a question ask on the forum, but don't be put off by someone giving you instructions via terminal. This is because you may have a different GUI set up than the poster, such as KDE, Gnome, or XFCE.

---

### Post by djeikyb on 2011-01-27
RE flash: From ([http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)), I choose the .deb package even though it says Ubuntu 8.04. Reason being is I use Chromium which afaik doesn't handle the apt link, and I'd rather play with debs anyway. After downloading, run:
```
dpkg -i packagename.deb
```

---

