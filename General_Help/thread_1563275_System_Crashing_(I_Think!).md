---
title: "System Crashing (I Think!)"
date: 2010-08-28
forum: General Help
---

### Post by Rachel5000 on 2010-08-28
Hello,
I am a new user - I did a full install of Ubuntu 10.04LTS 5 days ago. On a Dell Diminsion 2350. The reason was: I Hate Windows and there's just got to be a better way, so I got a hard copy and installed it. Here's what's happening: The whole thing just locks up. I get a message and then the screen will flash something that looks like piano keys across screen. Here's the message (Always the same)
 
***Speech-dispatcher configured for user sessions (OK)**
***Starting common Unix Printing System: cupsd**
***PulseAudio configured for per-user sessions**
**Enabling Additional Executable**
**Binary Formats binfmt-support**
**Checking Battery State**
**(OK)**
 
As I attempted to repair this on the advise of others, I changed out the monitor - Someone said it was an **Nvidia Driver** that needed to be removed or disabled, so change monitor first. Another person said to re-format, so I did. Yesterday. It's still happenig, and with greater frequency. There are a few other problems, but this is the worst. When this happens the only remedy is to shut off power. One more thing - This problem usually happens when OS is executing a command - Starting Firefox, Opening Office or Movie Player. Or, it happens as soon as desktop loads. 
 
Sorry if I'm a bit convoluted here - I just found out about Linux/Ubuntu a few weeks ago and have NO CLUE what I'm doing. If anyone knows how to repair this, they are more than welcome to connect remotely and do so. - I cannot pay as I am included in "The Poor" Robin Hood was going on about...
 
Thanks,
Shell

---

### Post by Smart Viking on 2010-08-28
Have you installed the proprietary nvidia drivers that ubuntu probably asked you to install?
What graphics card do you have?
Do you use 32 or 64Bit?
Will be easier to help you if we know that information. :)

---

### Post by tejashs on 2010-08-28
does it come to a command line mode? if so try typing "startx"

---

### Post by Rachel5000 on 2010-08-29
Have you installed the proprietary nvidia drivers that ubuntu probably  asked you to install?
What graphics card do you have?
Do you use 32 or 64Bit?
Will be easier to help you if we know that information.

[SIZE=2][FONT=Franklin Gothic Medium]Dear Mr Viking,

I cannot find the Nvidia Drivers. When I open the Synaptic Package Manager, there's NOTHING there. I've looked in Installed software, proprietary software and lots of other places and cannot find these things.

I have no idea what graphics card I have. Can you tell me how to locate that information? I also don't know about 32 - 64. How do I locate that info? 
I guess I need more information. 

I tell you what, I did a forum search on the phrase "Crash" today, and most of the references were about Ub 10.04 LTS (Is it OK to Abbreviate??) Then I did the same with Ubuntu 10.04LTS, and you know what? 
From what I've read today, and that was plenty - This version is not very good. (Should I duck and cover now?) I may just bow out gracefully, go to Amazon and get an earlier version software pkg. 

When I would run across a potential remedy or solution for crashes today I would try it and nothing's worked. It still shuts off. 

[I]**Does anyone know what the error message I posted in the start of this thread means? **(See 1st message in thread) It would be wonderful if someone else has seen this.

I tried to install a dif browser - someone said Firefox may be the problem, and the thing froze up in the middle, and now I can't go back to start install over because system is trying to complete the original install. This has been going on for about 1.5hrs.

Thank You All for listening to me whine. I'm certain I will make this work. Either with Ubuntu 10.04 or an earlier version.

:guitar: Rachel
[/I][/FONT][/SIZE]

---

### Post by varunendra on 2010-08-29
Hi Rachel!

I got to this thread through your post on the Welcome thread. One of the most amusing posts I've come across :).

So before you get offline, here's a command that will give a detailed list of your hardware:
```
sudo lshw
```Open terminal (Applications>Accessories>Terminal) and enter the above command. It will ask for your password. Type it (it won't show up while typing, just type correctly & 'enter'). Select the output of the command, copy it and paste here in your new post.

Then highlight (only) the pasted output text and click on the # icon on the top of the edit box. This will put it in [ code] marks making it easier to read.

After getting your hardware specs, we can assist you more precisely.

(hope you're still online. I'm suffering extremely irritating connection speed, so maybe I won't be able to reply soon!)


**EDIT:**
I just realized that the output of this command [COLOR=DarkRed]**may**[/COLOR] get overflowed. In that case (if the output goes out of the terminal limit), try this command (in the terminal of-course :)):
```
sudo lshw >~/Desktop/hw.txt
```

This will create a[COLOR=DarkRed]** hw.txt **[/COLOR]named file on your desktop. Just attach it with your post.

---

### Post by varunendra on 2010-08-29
Okay, my conn. seems a bit stable now, so I'll first try to explain a few things with my extremely limited knowledge. Please keep in mind that I may be wrong at any of the points.
> **Rachel5000 said:**
> 
***Speech-dispatcher configured for user sessions (OK)**
***Starting common Unix Printing System: cupsd**
***PulseAudio configured for per-user sessions**
**Enabling Additional Executable**
**Binary Formats binfmt-support**
**Checking Battery State**
**(OK)**These aren't error messages. It all seems just routine configuration process that usually happens in the background while loading the OS. If you are seeing these then I guess your X-session (the session of X-Server that provides the **Graphical** Interface) is crashing for some reason and after that- all you are left with is these messages that were actually loaded during startup.

If you are able to type commands on the screen after this 'crash', then see if this command returns something:-
```
dmesg | tail
```But of-course if it completely freezes (so that you aren't able to even type commands & restart remains the only remedy to be able to do **anything **again) then the above tip is worthless.

 > **Rachel5000 said:**
> Someone said it was an **Nvidia Driver** that needed to be removed or disabled, so change monitor first.
Wrong! Monitor has nothing to do with a VGA driver.

> **Rachel5000 said:**
> If anyone knows how to repair this, they are more than welcome to connect remotely and do so. - I cannot pay as I am included in "The Poor" Robin Hood was going on about...lol..! Don't worry, on this forum, no one's going to ask you to pay for 'anything' they do as troubleshooting/support.
 
> **Rachel5000 said:**
> [SIZE=2][FONT=Franklin Gothic Medium]
I have no idea what graphics card I have. Can you tell me how to locate that information? I also don't know about 32 - 64. How do I locate that info? 
I guess I need more information. [/FONT][/SIZE]Here's your info on 'how to':
For only graphic card related info, try```
lshw -C display
```To get details of your OS version & whether it is 32bit or 64bit, you can see it in **System>Administration>System Monitor** under **System **tab, or by this command:[SIZE=2][FONT=Franklin Gothic Medium]
```
uname -a
```[/FONT][/SIZE]> **Rachel5000 said:**
> [SIZE=2][FONT=Franklin Gothic Medium]From what I've read today, and that was plenty - This version is not very good. (Should I duck and cover now?)[/FONT][/SIZE]..... you don't need to, I'm sure there are so many on this forum alone who would concur with your opinion. It's just that it (Lucid) is too good for some while for some others...... well..... you've already realized what. So yes, it's not anywhere 'near' perfection yet!


Now before trying anything else, I'd like to know how does it all go when using a Live Session, that is, when you boot from a Live CD and run the OS from there. Here I am assuming that your 'Hard Copy' (the CD) is a Live CD.

If it is, then boot from CD and instead of choosing 'Install Ubuntu', choose '**Try Ubuntu without making changes......**'
Then after the OS loads & becomes ready to use, open Firefox or whatever & see if it crashes there too.

[COLOR=DarkRed]**One last tip for you**[/COLOR] (which I'm sure you already know ;)):
Trying a Live CD is the best way to try **any** linux distro before actually installing it on the hard disk. This way you can makes sure if it is fully compatible with your hardware & whether you are safe to go with it!

---

