---
title: "Ready to delete the whole kit and kaboodle"
date: 2010-04-25
forum: General Help
---

### Post by hours_wasted on 2010-04-25
[FONT=Century Gothic][COLOR=navy]Hello dear forum people, users and tech experts...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]This is my final shot before I delete Ubuntu from my computer and probably never try it again so I am quite disappointed in myself and the system.[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I am not great at computers, being self-taught, but I am not a stupid noob who doesnt even know how to work things - eg. I know a command prompt and how to use it etc...  (oh no that aint bragging, I just wanted to say I can handle tehnical language, read and apply information in manuals and help files... maybe I should've just said that for your info).[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I downloaded Ubuntu yesterday as I am sick to the eyeballs of Microsoft's and Apples domination of my computer... downloading unecessary updates which are for products I don't want - even when I have turned them off except for security updates.... making using itunes hard to use when I no longer have an iphone.... (yes I play my music with VLC but it's still not quite my music any longer...)[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I like the look and feel of Ubuntu.  I downloaded a Getting Started Guide from the Ubuntu team and another manual called Ubuntu Kung Fu.  Great.  I read them.... but nothing quite works...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I connect my wired network.... but sessions time out just going to google home page...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I get the printer to recognise the computer and vice versa... but the test page won't print... despite the printer window in ubuntu saying it has printed and seeing the printer reading information from the computer...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]Finding my music files through the windows partition was hard but I worked it out... but the Ubuntu player won't play them... presumably the &^%$$% apple mp4 format...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I was already wondering if I wanted to lose the functionality of IE8, the ability to use Dragon software for speech to text, and some of the brill features in Word 2007....  but I was willing to give it a go...  but I can't get the simplest thing right in Ubuntu.[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]So this is my last shot... can anyone please please (remember I already have read and followed the instructions in manuals) tell my why the heck Ubuntu won't work for the net and printing...  can anyone help me get this OS working to my needs (I know voice to speech isnt an option yet)....  because I really am going to have to delete the whole thing if I can't get it working.... I've been up all night and I can't waste any more time...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080]I'm sorry... I could've summed that up quickly... but this is a rant as much as a question isn't it... I'm very frustrated and I really want things to work...[/COLOR][/FONT]
[FONT=Century Gothic][COLOR=#000080][/COLOR][/FONT] 
[FONT=Century Gothic][COLOR=#000080]Thank you all, in anticipation!!  :P[/COLOR][/FONT]

---

### Post by 3rdalbum on 2010-04-25
This is your first post asking for help; please don't get too frustrated yet. Ubuntu is so much different to anything you've used before.

For your network, you might need to add DNS information that allows the system to convert the name "www.google.com" into an actual IP address. Usually this happens automatically, but in some cases it doesn't on non-Windows systems, depending on what modem and ISP you have.

Go to the Network Manager applet and right-click on it. Go to Edit Connections. Under the Wired tab you'll see your connection. Click on it and click Edit. Go to the IPv4 Settings tab. Change the "Method" to "Automatic (DHCP addresses only)". Put your ISP's DNS addresses into the DNS field; if you don't know these, then put this generic DNS address in:

208.67.222.222

Save changes and Apply and whatever else you need to do. Disconnect and reconnect and you should have connectivity.

2. What printer do you have?

3. Ubuntu doesn't play MP3s and AACs by default, because those formats are patented and it's against Ubuntu's policy to ship patented components. You can easily add support for those formats now that you've got an internet connection - just use Synaptic Package Manager to install the "ubuntu-restricted-extras" package (you might need to hit the Reload button first to get an up-to-date package list from the server).

If those music files are DRM-encrypted then nothing except iTunes on Windows will play them, but fortunately all music downloads from iTunes these days are not encrypted.

You really can't give up after less than a month, IMHO, because Linux is a vastly different operating system. I mean, I know very little about Windows and I can't get a Windows system up-and-running and productive in less than a day... a FULL day. And I've certainly got more Windows experience than you've got Linux experience.

---

### Post by steveneddy on 2010-04-25
You will get better help by posting in the default font and size.

You really need to either search the forums and if no luck finding a solution to your issue, don't hesitate to start a thread with one issue each.

Dumping all of your issues will get you and others frustrated while trying to help you.

You only have one day into Ubuntu and you are ready to give up now?

Linux and Ubuntu are NOT Windows and will probably not support Windows applications the way that you wish them to be supported.

If you rely on Windows apps so heavily, I suggest that you go back to Windows and simply run Ubuntu in a virtual machine like VirtualBox. 

I believe that you will be happier running in this manner while you get used to this new OS. it is different and may take a while for you to get used to something this different.

Good luck.

---

### Post by QIII on 2010-04-26
Your frustration is not uncommon, and we are all here voluntarily on our own time to help.  (It's a lot easier to do that one question per thread, though...)

German kids grow up speaking German and you might spend years in College trying to sort it out.  You can't learn it overnight.

But you speak English just fine.

For you, Microsoft is English.  Linux is German.  That doesn't make Linux bad.  Just different.

I agree with the idea of using both side by side until you learn Linux and come to grips with the fact that it does not act like Windows because it isn't.  The software you may be used to was written to work on Windows, but will likely not work in Linux.  Windows <> Linux.  OEMs write their hardware drivers to work with Windows and give Linux short shrift.  We make do, but it is not always easy.

Besides virtualizing, you can also dual boot and run each OS natively.  Virtualization can be problematic because the virtual machine will have its own virtual scheme for video output, networking, USB devices, etc.

Dual booting creates entirely separate environments where each OS is loaded and operated natively on your hardware without ever "knowing" that the other OS even exists.  But only  one can run at a time, so to switch to the other you have to shut your machine down and select the other when the machine restarts.

About bed time for me, but I'll see if I can get back with the URL for a good, step by step tutorial.  It's not really hard at all.

If you do that, then  you can ask one question at a time, get resolution on that (there is almost always a resolution already contained in a thread here) and move on to the next issue.  You won't be learning German in one class, but over a series of semesters spread out over a reasonable amount of time.  And you can still speak English the rest of the time to get done what you need to get done.

Eventually, you'll be teaching the classes.

---

### Post by hours_wasted on 2010-04-26
Dear 3rd Album,  
1.  Thank you for your helpful response.  In some ways I am glad - I had already done the things you suggested - so I am not so stupid... in other ways... well... no point having done those things if the dang thing still won't work.  I had made the suggested alterations to the Ipv4 settings tab, including my ISPs DNS addresses, but I can only open the firefox ubuntu homepage....  I take your point about having to type the entire name.... so added www in front of google... still no response... a loading timeout as before.
2.  I have a Canon MP630, which ubuntu recognises and is 'properly' loaded.  When I print either a test page or something from openoffice doc the page sends to the printer, the dialogue window tells me the page is printed.... the printer screen receives the file from the computer... but no output...  I printed your answer before rebooting back into ubuntu... so it's not the printer or connections.
3.  I didnt know ubuntu didnt even play mp3's, however I planned on downloading VLC at some time so I guess when I get that going I'll be able to listen to my music files...  (and my itunes files are DRM'd because I run an old version of itunes that won't update... ergo looking for another option).
 
I agree I shouldnt give up so easily... I just like the basic things to work in new apps or technology or whatever I am using so that I can then have some time to play around to figure out other things... I dont mind learning... but not even getting a net or printer connection seem too basic for words... 
 
If you have any other advice... i will gratefully appreciate it...  and thank you for your respectful and complete answer...
 
dear steveneddy,
thank you for your reply.  I have 'assistive issues' with my computer so use a different font and color to assist readability... I dont see how this could affect the quality of any replies??  strange answer from you...  additionally.. please know... I have printed off 2 ubuntu  manuals and searched this forum.... but nothing worked... that's why I posted one post in final frustration prior to deleting the whole thing....  I wouldnt disrespect anybody such to just not read available information and expect them to use their time helping me anyway...  I believed my one issue was just getting the basics right... that's why I posted one thread.... and yes, I know windows and ubuntu arent the same... of course??  I did explain that??  please... I do respect you and your knowledge... please respect me as well as per my points above?  this answer isnt meant to make you angry... just to show you there are reasons people do things which doesnt make them wrong...
 
Dear q111,
thank you for acknowledging my frustration.  Your analogy is pertinent and hopefully to me when I get frustrated in the future.... I would only add that even in learning German one could learn hello, goodbye, please, have a nice day... in one class... and that is really only what I am seeking with starting ubuntu...  open a net connection that works quickly and print help documents to work through issues using ubuntu...  not too much german for the first class?  LOL...
 
mmmmm... well..... I guess I'll wait to see if there is anymore assistance I can receive... otherwise I will have to go back to the devil aka windows.... sigh... and thanks again to posters to my thread.

---

### Post by spoon_ on 2010-04-26
Why not post the steps you take to get your internet connection to work in Windows (i.e. on a fresh Windows install), then someone can tell you how to replicate those steps in Ubuntu.

---

### Post by hours_wasted on 2010-04-26
Hi Spoon... hmmmm... with windows I take a 'try this and this and then this' approach when loading a new ISP until something works!...  I havent added a new ISP for so long, however, I would only know that I would go to 'network and sharing centre' and go from there... so not different enough to ubuntu in that way...  thanks for your idea and post.

---

### Post by spoon_ on 2010-04-26
> **hours_wasted said:**
> Hi Spoon... hmmmm... with windows I take a 'try this and this and then this' approach when loading a new ISP until something works!...  I havent added a new ISP for so long, however, I would only know that I would go to 'network and sharing centre' and go from there... so not different enough to ubuntu in that way...  thanks for your idea and post.

Ok, can you post a screenshot of this dialog in Windows?:

[IMG]http://support.hubris.net/configuration/screenshots/network_xp/cap004.gif[/IMG]

It might give people some idea of how your network needs to be configured.

---

### Post by luctor on 2010-04-26
Don't give up !
It took me a whole week to figure out what was wrong with my wired network.
Finally solved it.
[http://ubuntuforums.org/showthread.php?t=1452615](http://ubuntuforums.org/showthread.php?t=1452615)

---

### Post by Rubi1200 on 2010-04-26
I agree. Anything new takes a bit of getting used to, including a lot of frustration sometimes, and, in my case, reinstalling Ubuntu about 4-5 times till I got it right. Search the forums, use Google, and ask questions. In most cases, there is an answer.
Good luck!
:)

---

### Post by Rubi1200 on 2010-04-26
I found this site to be quite helpful for a number of things:
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)

---

### Post by hours_wasted on 2010-04-26
> **spoon_ said:**
> Ok, can you post a screenshot of this dialog in Windows?:

[IMG]http://support.hubris.net/configuration/screenshots/network_xp/cap004.gif[/IMG]

It might give people some idea of how your network needs to be configured.
thank you spoon.... my dialog box looks exactly the same as the one you copied... obtain an IP and DNS server address automatically....

---

### Post by hours_wasted on 2010-04-26
Thank you very much Rubi...  I'm still trying suggestions and reading links at the moment.... but but but... !!!
 
:]

---

### Post by hours_wasted on 2010-04-26
> **luctor said:**
> Don't give up !
It took me a whole week to figure out what was wrong with my wired network.
Finally solved it.
[http://ubuntuforums.org/showthread.php?t=1452615](http://ubuntuforums.org/showthread.php?t=1452615)
LOL Luctor....  I see a whole thread where I have tried the things you did... reset router etc... but your fix isnt then included in the thread...  not an insult or having a 'dig'... just find that funny... isn't it the way... phew... thank god that one's fixed... move one... next problem!!  chilli was good to you hey...

---

### Post by hours_wasted on 2010-04-26
ok.... so should I delete and reinstall Ubuntu then?  could this reallly help?

---

### Post by hours_wasted on 2010-04-26
OH, and just to let you know... I installed ubuntu directly from the ubu website... using a tool... from memory called wubi or something like that... so it was all automated and only took about 20 minutes...

---

### Post by Rubi1200 on 2010-04-26
Sometimes if things get messed up a reinstall is the best option. I have no experience using Wubi (although I have heard it is decent), because I completely dumped Windows and moved over to Linux. Can I assume you are now dual-booting with Windows? Maybe there is a hardware or other conflict that is not necessarily the fault of Ubuntu. Additionally, I personally suggest you install Ubuntu from the CD and not via Wubi.

---

### Post by hours_wasted on 2010-04-26
thank you Rubi... you've been very good and your links and answers have been helpful...  so... since there is only a couple of days to go til the next Ubuntu version.... I am going to uninstall the current version... undo everything... then install using a boot CD as you say... it does seem safer... yes, I am dual booting with windows because atm I have to use speech-to-txt software (dragon) which ubuntu doesn't yet provide/support...  not for day to day stuff, but I am doing an undergrad degrees and a masters... and working... so need the support of Dragon to keep me going...
thanks again... I hope you have a great week, full of all good stuff...

---

### Post by nothingspecial on 2010-04-26
While I appreciate the time and effort the developers of wubi have spent on the project, I have often heard of problems with it.

I suggest you download a ubuntu iso and burn it to a cd. Then boot from the cd. Test your network connection and printer.

If they work, install ubuntu in a dual-boot setup along side windows.

Bear in mind that a new version of ubuntu is to be released in a couple of days. You could either download the release candidate now, or wait until it is officially released. Each version of Ubuntu includes more and more hardware support.

---

### Post by Rubi1200 on 2010-04-26
Thanks for the kind words and good luck going forward. I agree with nothingspecial that you should wait for the official release of Lucid Lynx, get the CD or iso image and first try everything using the LiveCD. If it works, go ahead and install to the hard drive. If not, ask more questions and then decide if you really want/need Ubuntu (or Linux in general). I waited 3 years before taking the plunge and getting rid of Windows after I had tried various live distros, read up about networking, and Linux in general. I have to say that no OS is perfect and Linux has its quirks, but I can do everything in Ubuntu that I could in Windows and then some.
Have a great week too!
:)

---

### Post by fenririx on 2010-04-26
I spent a week trying to get a decent copy of the .iso file. Some of the mirrors for download are incomplete or corrupt. I'm currently deployed and can first hand say the kuwait download was no good but the saudi was complete. Many issues can come up trying to get it to work. Surprisingly to me, my wireless network card came right up on the network. Areinstall may be all you need.

---

### Post by Rubi1200 on 2010-04-26
Yes, I noticed this too; what a pain!

---

### Post by steveneddy on 2010-04-26
Most of your issues are from Wubi, a fact that you neglected to tell us in your first post.

Either run Ubuntu in a VM or partition your drive and install Ubuntu on it own partition.

Wubi has issues and is really for a trial of Ubuntu, not a full fledged working version of Ubuntu.

from a link in my sig:

> Wubi (Windows-based Ubuntu Installer), an officially supported dual-boot installer that allows Ubuntu to be run mounted in a virtual-disk within the Windows environment (which can cause a slight degradation in performance). Because the installation requires an intact functioning Windows system, **it is recommended to install Ubuntu in this manner for short-term evaluation purposes only**. **[COLOR="Red"]A permanent Ubuntu installation should be installed in its own partition, with its own filesystem, and should not rely on Windows[/COLOR]**.

But it's your computer - I don't recommend Wubi ever.

"Trying" Ubuntu from a live CD is a better alternative than Wubi IMHO.

---

### Post by hours_wasted on 2010-04-27
Hey Rubi and Fenririx.... yep... hey... one day to go... I've uninstalled the previous Ubuntu and am gearing up for my next forage into the next version... and certainly running the ISO from CD sounds like the way to go... thank you both for your help and supportive comments...  I hope I'll be back on here in a day or so with fingers burning to tell you that it's a brilliant wonderful day full of an OS that isn't Windows (spit, gag from saying the word)!... lol... thanks again...
 
hey steveneddy....  your answers are helpful... but but... a tad discourteous...  this is the second time you have had a dig at me because I didn't post something in the way you would have preferred... and whilst (again) I can see your point and agree with you...  I must also ask you to have a little more patience in your responses...  neglect is a harsh word to use for someone who was an hour old noobie with Ubuntu...  it wasn't strictly neglect...  I just didn't know the difference, or that it was important to the 'story'... and I had read heaps and heaps and heaps and nowhere had I read anything other than Wubi was a good way to load Ubuntu....*shrug*  same as I didn't think it was important it was raining at the time....   please please be a little more tactful... cos obviously you are a great user of the product and know so much...  maybe you have forgotten how strange and difficult new things are now....  but that doesnt make a person stupid if they don't know something... only ignorant if they don't want to learn...?...  and I dont have a thin skin... I just like to treat people with the best respect and courtesy and understanding of their 'peopleness'... until they prove they don't deserve the respect of course... (and no, you certainly are not in that latter category)...
have a great day... see you on the other side of the 29th... possibly even posting from Ubuntu 10.4!

---

