---
title: "Ubuntu 12.04  cannot install Tor"
date: 2012-05-03
forum: General Help
---

### Post by bulldoze on 2012-05-03
I gave up on Ubuntu a couple of years back as I just got so frustrated trying to install stuff and went back to windows.

I have to use linux at work now and I forgot how refreshing an operating system it is. so I am really onside and hope I can get on with it this time!

last time the final straw was trying to install Tor and I gave up in the end.

My first task on installing 12.04 was to have another crack at Tor and guess what? failed at the first hurdle again!!

I tried to install from a few online guides but could not get it to work - some messages about incorrect directory and vidalia exited abnormally.

well i found this post by jim_deadlock

That tutorial is WRONG! Firstly, the Tor FAQ has always said NOT to install Tor from the repositories because the package is permanently out of date. Secondly, it is no longer necessary to install Tor, all you need to do is download the Tor browser bundle and run it, no installation is necessary.

Tor Browser Bundle

So I tried to delete tor and vidalia and used the tor browser bundle - I installed it exactly as the tor project suggested following the tutorial stage by stage but I still get this message:

Vidalia exited abnormally: Exit code 127

Please help!

---

### Post by bulldoze on 2012-05-03
bump - anyone? please?

---

### Post by rigel4 on 2012-05-06
This link explains how to get set up 

[https://media.torproject.org/video/torbrowser-docs/How-to-download-and-use-TBB-in-Linux.mp4](https://media.torproject.org/video/torbrowser-docs/How-to-download-and-use-TBB-in-Linux.mp4)

---

### Post by jim_deadlock on 2012-05-06
> **bulldoze said:**
> So I tried to delete tor and vidalia and used the tor browser bundle - I installed it exactly as the tor project suggested following the tutorial stage by stage but I still get this message:

Vidalia exited abnormally: Exit code 127

Please help!

I'm afraid I'm baffled by this paragraph. The Tor browser bundle simply runs without any installation, so what exactly did you install? What "tutorial" are you talking about? All you need to do is extract the .tar.gz file, double-click start-tor-browser and wait a few seconds for it to automatically start vidalia and the browser.

You can even run a full Tor node using the browser bundle if that's your goal (via the Vidalia 'sharing' tab). Tor used to be quite tricky to install but that's all history since they did away with installation altogether. I don't understand why people are having so much trouble with it.

In a nutshell, you need to PURGE EVERYTHING related to Tor/Vidalia installations, then double-click start-tor-browser. Simples.

---

### Post by bulldoze on 2012-05-08
I mean I first tried to install Tor and vidalia via the command line this was unsuccessful. Once I realised that the way to do it was via Tor browser bundle I attempted to delete and purge Tor and Vidalia from my system.

I then went onto the Tor website where they had a video of how to download and install Tor browser bundle - i followed this to the letter.

but i still get the error message above.

---

### Post by Enigmapond on 2012-05-08
Purge TOR and Vidalia from your box. After that, although you can start it by just clicking the script, open a terminal and cd to where you have the folder and do start-tor-browser and list any errors you are getting in the terminal.

---

### Post by 23dornot23d on 2012-05-08
> 
I mean I first tried to install Tor and vidalia via the command line this was unsuccessful.


That is where the problem lies ..... and removal of anything you installed .... something will still be there ......

Fresh install 12.04 .... and do it again ..... is the simple option ......

Tracking down the things that may have been installed from the command line may be a pain ....

You could post your history or look through it to see if you can reverse what you did.

Fresh install is the simple option ...

---

### Post by Enigmapond on 2012-05-08
> **23dornot23d said:**
> That is where the problem lies ..... and removal of anything you installed .... something will still be there ......

Fresh install 12.04 .... and do it again ..... is the simple option ......

Tracking down the things that may have been installed from the command line may be a pain ....

You could post your history or look through it to see if you can reverse what you did.

Fresh install is the simple option ...
Simple yet overkill. Like buying a new car because your wiper doesn't work...neither TOR or Vidalia install anything else with them. So by purging both and then running the bundle...(you may have to reboot)..this should work. Make sure you don't have privoxy installed.

---

### Post by codingman on 2012-05-08
> **23dornot23d said:**
> That is where the problem lies ..... and removal of anything you installed .... something will still be there ......

Fresh install 12.04 .... and do it again ..... is the simple option ......

Tracking down the things that may have been installed from the command line may be a pain ....

You could post your history or look through it to see if you can reverse what you did.

Fresh install is the simple option ...

That is ridiculous. Why would some "be there", and even if there was, it would not affect it.

---

### Post by 23dornot23d on 2012-05-09
> 
I gave up on Ubuntu a couple of years back as I just got so frustrated trying to install stuff and went back to windows.

I have to use linux at work now and I forgot how refreshing an operating  system it is. so I am really onside and hope I can get on with it this  time!

last time the final straw was trying to install Tor and I gave up in the end.

[COLOR=Red]**My first task on installing 12.04 was to have another crack at Tor and guess what? failed at the first hurdle again!!**[/COLOR]

[COLOR=Blue]**I tried to install from a few online guides**[/COLOR] but could not get it to work  - some messages about incorrect directory and vidalia exited  abnormally.

well i found this post by jim_deadlock

That tutorial is WRONG! Firstly, the Tor FAQ has always said NOT to  install Tor from the repositories because the package is permanently out  of date. Secondly, it is no longer necessary to install Tor, all you  need to do is download the Tor browser bundle and run it, no  installation is necessary.

Tor Browser Bundle

[COLOR=Red][B]So I tried to delete tor and vidalia and used the tor browser bundle - I  installed it exactly as the tor project suggested following the  tutorial stage by stage but I still get this message:

Vidalia exited abnormally: Exit code 127[/B] [/COLOR]

Please help!
If the user had not installed TOR as his/her first task - as the first part in red implies then the way I would have sort this out would be to trace back through my history as I said ....

When I give two options to solve a problem - it is not so that other USERS can say one is like replacing the car when only a window wiper is needed to be replaced - without seeing the history - you do not know if the command line instructions included compiling something from source and how many other things the user did ..... if the user wants the more demanding method to solve the problem of tracking down exactly what went wrong - then that option is there - and can look through their history or someone else can to see if there is a easy option ...... 

> [COLOR=Blue]**I tried to install from a few online guides**[/COLOR]
if a window wiper was the only thing that was added - then that window wiper may need to be the only thing removed ( The history could show this ).

By typing history in a terminal will give the used all the commands previously attempted ...... type this in a terminal window and post back the results
[B]
history[/B]

Then we have a better understanding of what was installed in the command line attempts .......

This thread also has been open for 5 days ..... to me if it was simple it should have been solved in those 5 days ..... by removing said window wiper as the USER obviously tried to do from this quote

 > [COLOR=Red]**So I tried to delete tor and vidalia and used the tor browser bundle **[/COLOR]
Vidalia exited abnormally: Exit code 127
So removing said window wiper and replacing it did not work ?

[COLOR=Blue][B]This is where I took it that something maybe did not get removed as expected
[/B][/COLOR]
30 mins is the quicker solution in my mind and if as said the first thing they did was to try to get TOR working ..... 

Then if it was the first thing done - they should have nothing to loose by doing
a clean installation ...... 

( I agree normally when the USER has a system that has been worked on for some time - it is better to track the problem down and remove what caused the problem - if the install is new and takes 30 mins to replace - and I see that this could go on for sometime >>> then giving one option to re-install and the other option to track it down through the history  )

Its the first time I have felt the need to explain why I gave the advice the way I gave it
but as said ..... the two choices that I gave were not in anyway to make the USERs job
harder than it needs to be.

And to the two replies after mine ..... please read the full reply ...... re-installation was one of two options to take .

Hope this helps you to understand that when I give options they are though out .... only a few times I will say re-install - but in my mind it will be because I see that as the quickest and easiest way to get up and running quickly without having to worry too much about what may or may not have happened early in the sequence of events leading up to a problem.

Best of luck ....... ( now to look for the window wiper .... where did it go now ..... ah I removed it and added another and the dam thing is still not cleaning off my windows ...... ) screen clean is another option .....

---

