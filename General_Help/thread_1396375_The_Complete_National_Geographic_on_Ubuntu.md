---
title: "The Complete National Geographic on Ubuntu?"
date: 2010-02-02
forum: General Help
---

### Post by Dedi Landsman on 2010-02-02
Hi, I wonder whether anyone had an experience of trying to use The Complete National Geographic on Ubuntu. In their web page [http://www.nationalgeographic.com/completeng/](http://www.nationalgeographic.com/completeng/)
it states system requirements with Windows and Mac, but how about Linux? I wrote to their support team, asking about it, the reply i got was  > 
We have had reports from consumers that the software will run on Linux (Ubuntu) OS, but the CNG Team has not tested the program on those systems.
Does any one here have had any experience with that CNG on Ubuntu?
Thanks for any help
[B][SIZE=4]
[/SIZE][/B]

---

### Post by SR_ELPIRATA on 2010-02-26
Hey Dedi!

My friend just got it this week and after getting an external DVD player we decided to get into the installation. I was kind of worried about the Adobe AIR installation but we decided to anyways try it. We tried this installation in 2 different system, a small laptop with a P3 1Ghz and 382MB of RAM and a Duron 700mhz clone with 768MB. Both have standard graphics.

You're gonna need Wine installed but dont install the one in the repositories, go to [www.winehq.org](www.winehq.org) and go to downloads, then Ubuntu and follow those instructions so that you get the latest Wine installed.

Then, we started on the P3, worried with the 512MB RAM requirement (as we had 382MB). The installation started, did the Air installation and got stuck there. At first we didnt knew what to do. I google'd and found that somebody had done it and that he said that he'd cancel the installation and try again untill it finished it, and to be honest, thats what did it for us too.

On the P3 we sort of gave up, we thought it was a memory problem. Then we moved on to the Duron system and we saw the same, stuck after the AIR installation. Decided to cancel and start over, the installer then asks if you want to update the AIR installation or continue without updating, which we did, then it got stuck again there for quite some time.

Using System Monitor we noticed the CPU was at 100% most of the time so we knew something was being done, eventually the Installer ended and asked to agree to the bla bla bla and soon after we were in the main interface. and we still noticed that it was slow, but we knew that the CPu wasnt up to the task, its below the requirements. We're yet to try this on the P3, which has the CPU required but a lot less RAM.

Something I wanted to mention... is... that even though the interface allows you to select which DVD you want to see (DVD #1 has the magazines for 1995-2008 ) you wont be able (untill someone comes with a solution for that) to switch DVD's because it won't let you do it. You'll see the "insert dvd#6 (or whatever) and click ok" but Ubuntu won't let you eject the DVD.

I guess one thing you can do is, knowing what data each DVD has... just insert the DVD you want to find data in and then double click on the desktop icon for the Interface. I've heard there's a way to put all the data (9gigs plus on each dvd) on the hard drive but I ain't got a clue on how the Interface will find that.

The good thing is that it works. And the last DVD, the bonus, its really interesting for National Geographic aficionados.

ELP

---

### Post by Dedi Landsman on 2010-02-26
Hi, Thanks very much for helping.
I don't have yet The Complete National Geographic CDs. i wanted to ask whether The Complete National Geographic requires Wine just because the abode air or because some additional software specific to the The Complete National Geographic? if it requires wine just because the Abode Air, there is Abode Air specially for Linux [http://get.adobe.com/air/](http://get.adobe.com/air/)
[I'm still a kind of Linux newbie]
Thanks for any help.

---

### Post by Mark Phelps on 2010-02-26
I just checked the Wine App Compatibility DB site --  and there's no listing at all for the Nat Geo product.  This usually means its not been tested.  

So, if it doesn't work, you're pretty much on your own.

---

### Post by JALindsay on 2010-03-08
I think all you should need to do to switch DVDs is to go into Nautilus and eject the DVD from there.  It is a bit of a kludge-- but it does work.

---

### Post by Dedi Landsman on 2010-05-08
Hi. finally i got the Complete national Geographic CDs. I have followed the directions given here, and was extremely happy to see it being installed and working on my Ubuntu [9.04], i guess now i can throw Windows for good out of my computer. Thank you very much for the suggestions i was given here. 
How about updating the software, has any of you got any experience in clicking the Update button? [the software works so nice,  I'm a kind of afraid to do that]
How about running the Complete national Geographic CDs on Ubuntu Lucid 10.04, does it works well as in 9.04?
Thanks for any help.

---

### Post by AiBo on 2011-01-12
I am looking for a solution too.  Running things thru wine rarely work out well for me ;)

I came across this [http://0xab.com/?p=154](http://0xab.com/?p=154)

Looks hopeful:

> If you’re thinking of buying a copy of the Complete National Geographic but are weary of having to run it under wine, despair no more. It’s written in Adobe Air and runs acceptably well. I used wine to install it so I could get at the air package inside, but it turns out NGM is nice and provided us with a handy download for the viewer. I couldn’t get it to run without unpacking it, something about an API version mismatch (originally I repacked it with the correct settings but that’s overkill). You can just unzip it in its own directory and run it with something like: /opt/AIR-SDK/bin/adl -nodebug /opt/AIR-apps/CNGViewer/META-INF/AIR/application.xml /opt/AIR-apps/CNGViewer &> /dev/null. Note that as with most Adobe technologies on Linux it’s needlessly CPU intensive, it pegs my CPU at 100% regardless of what frequency it’s set at.

---

### Post by AiBo on 2011-01-18
Works like a charm!  Nice to have CNG running natively!

---

### Post by sea-geek on 2011-11-07
This almost worked for me but after I follow all the directions at:
[http://bilbo.online.bg/~assen/cng.htm](http://bilbo.online.bg/~assen/cng.htm)

When I start the Complete National Geographic from the icon, 
it seems to start fine and I can browse the issues but when I try to select one I get this error:
"Please insert disc #1 (1888-2009) and click OK."

So it seems to know I've collected the disks into one location but cannot find it.

I've tried making symbolic links:
ln -s /media/Elements/CNG/disc1 /media/disk1
ln -s /media/Elements/CNG/      /media/DISK1
ln -s /media/Elements/CNG/disc1 /mnt/disk1

I put all the files on an external hard drive: /media/Elements/
Could that be the problem? I wasn't able to change the permissions on this disk as indicated in the directions.
Also, the directions indicated 

"...the application reveals that is simply probes for "disc1", "disc2" etc. in all first-level directories inside two popular mount points: /mnt and /media. If it finds one, it uses its number to figure out which disc is inserted. Therefore, all we need is set up a symlink under "/mnt" to the "disc1" directory"

so if I have more than one 'disk1' in /mnt or /media does it get confused?

If you got this working using the instructions above, any ideas on why mine does not?

Thanks!

---

### Post by Charlesproxenos on 2012-03-11
I followed the advice on [http://bilbo(dot)online(dot)bg/~assen/cng(dot)htm](http://bilbo(dot)online(dot)bg/~assen/cng(dot)htm) the only difference is I symlinked the directory that CNG wanted to download the discs into with a directory on my external hard drive.

I then copied disc 1-6 to my hard drive
I then merged all the info into disc1
I then adjusted the sqlite3 data base as per the instructions above.

Voila

My CNG also came with a 2010 update dvd, If anyone figures out how to install this in linux it would be helpful, I have tried just about everything and still unable to access those last 12 issues, hmmf

Cj

---

### Post by gleedadswell on 2012-03-28
Hrm...

Trying to follow

[http://bilbo.online.bg/~assen/cng.htm](http://bilbo.online.bg/~assen/cng.htm)

but I hit a barrier very quickly.  I got the .bin for installing Adobe Air 2.6 from 

[http://helpx.adobe.com/air/kb/archived-air-sdk-version.html](http://helpx.adobe.com/air/kb/archived-air-sdk-version.html)

I did chmod to set execute permissions.  With root privileges I tried to run AdobeAIRInstaller.bin.  After agreeing to the license it gave me the following error:

Adobe AIR could not be installed. Install either Gnome Keyring or KDE KWallet before installing Adobe AIR.

I checked and I've got the most up-to-date gnome-keyring package.  Any ideas?

---

