---
title: "(all varients) FIX the AVAST error engine failure after update."
date: 2010-04-07
forum: General Help
---

### Post by linuxgeek77 on 2010-04-07
Hello guys for those who dont have avast Linux here is the link to get it:
[[HTML] http://www.avast.com/linux-home-edition#tab4 [/HTML]]("http://www.avast.com/linux-home-edition#tab4")

get the .deb file for Ubuntu/kubuntu/xubuntu


ANyhow lately Avast has been crashing with engine errors. what i found out was that the problem was due to the fact that the size of the virus definitions database reached a system limit. it was a messup from avast linux team. that they overlooked this. Anyhow here is a quick way to fix it that will take you 30 seconds :)

[B]NOTE: KUBUNTU USERS USE KATE (instead of gedit) 
          XUBUNTU USERS USE MOUSEPAD (instead of gedit)[/B]

1) open the terminal
2) a)type this command to open the file you need to edit: 
        ```
sudo gedit /etc/init.d/rcS
```    b) type your password and hit enter

3) when the text file opens add the line:

    ```
sysctl -w kernel.shmmax=128000000
```4) make sure the line you added is before: 

```
exec /etc/init.d/rc S
```5.- This is how it should look like:
 ```
 #! /bin/sh
    #
    # rcS
    #
    # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
    #

    sysctl -w kernel.shmmax=128000000

    exec /etc/init.d/rc S
```6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST WILL WORK 100%


THANK YOU. please report back if it works for you :) 

I personally find avast to be one of the best Linux A/V available to scan windows partitions and/or incoming emails

credits go [here]("http://forum.avast.com/index.php?topic=57775.15")

WOrks with linux mint. AS i use linux mint. :)

---

### Post by ibbill on 2010-04-07
oops no luck still the engine failure rechecked all again have the same as you but no luck.

thanks

---

### Post by ibbill on 2010-04-07
oops slaps self 3 times  reboots computer duh  it worked perfectly thanks ever so much.

---

### Post by bradshawd on 2010-04-07
The reboot did it..

Happy bunny once again..

Many Thanks for this fix.

D

---

### Post by linuxgeek77 on 2010-04-07
> **bradshawd said:**
> The reboot did it..

Happy bunny once again..

Many Thanks for this fix.

D

your welcomed :D

---

### Post by Pesmontis on 2010-04-10
It worked nicely (Ubuntu 9.10, avast! antivirus 4 v1.3.0-2_i386),
very good of you to post this fix :-)

---

### Post by slumbergod on 2010-04-14
Thanks, the fix worked for me (Xubuntu 9.10)

---

### Post by P4man on 2010-04-22
Can you please update your post and change

```
sudo gedit /etc/init.d/rcS
```

into 

```
**gk**sudo gedit /etc/init.d/rcS
```
?

Sudo is for console commands, gksudo for graphical ones. Doing it the wrong way may cause havoc on your file permissions. More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

(coming to post here after [someone rendered his machine unbootable]("http://ubuntuforums.org/showthread.php?t=1460227") after following your how to, and I think this *might* be related).

---

### Post by linuxgeek77 on 2010-04-24
> **P4man said:**
> Can you please update your post and change

```
sudo gedit /etc/init.d/rcS
```into 

```
**gk**sudo gedit /etc/init.d/rcS
```?

Sudo is for console commands, gksudo for graphical ones. Doing it the wrong way may cause havoc on your file permissions. More info here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

(coming to post here after [someone rendered his machine unbootable]("http://ubuntuforums.org/showthread.php?t=1460227") after following your how to, and I think this *might* be related).

I have always used sudo. why would i need a gui front end to enter my password? i never used gksudo. i never understood why people would need a gui front end. just eneter pass in the terminal and keep going!!! but if anyone is confortable to use gksudo then they can be my guest.

---

### Post by P4man on 2010-04-25
Its not just that you get a gui front end to enter the password. If you use sudo for graphical apps, you can end up with configuration files in your home folder like .Xauthority being owned by root, giving all sort of problems, including being unable to log in. Im not making this up:
[I]
Graphical sudo

You should **never** use normal sudo to start graphical applications as root. You should use gksudo (kdesudo on Kubuntu) to run such programs. gksudo sets HOME=~root, and copies .Xauthority to a tmp directory. This prevents files in your home directory becoming owned by root. 
[/I]
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kherring7383@yahoo.com on 2010-04-25
After installing Avast several times and getting the same errors, I came across this post and gave it a try and it worked great. Thanks!

---

### Post by Meow27 on 2010-04-29
thanks so much. it worked for me!

---

### Post by nicks27 on 2010-05-01
Thanks for the fix.

As an alternative to editing the [FONT=Courier New]/etc/init.d/rcS[/FONT] file, I made the edit in the [FONT=Courier New]/etc/sysctl.conf[/FONT] file by adding the line:
[INDENT][FONT=Courier New]kernel.shmmax = 67108864[/FONT]
[/INDENT](Thanks to thread [http://ubuntuforums.org/showthread.php?t=601484](http://ubuntuforums.org/showthread.php?t=601484) ).
Don't forget to reboot after making the edit.

... and if you want to know the current value of [FONT=Courier New]kernel.shmmax[/FONT] then the command:
[INDENT][FONT=Courier New]cat /proc/sys/kernel/shmmax[/FONT]
[/INDENT]or:
[INDENT][FONT=Courier New]sysctl kernel.shmmax[/FONT]
[/INDENT]will tell you.

---

### Post by 73ckn797 on 2010-05-02
Thanks for the fix.

---

### Post by zveroboy on 2010-06-23
Thanks a lot.  Worked for me on Ubuntu 8.04.

---

### Post by Elmer Fudd on 2010-06-26
10.04 - worked for me. Thanks.

It's June. This is an easy fix.
Why not incorporated yet - in the install ??

---

### Post by Zenzibar on 2010-07-25
Thanks much! Your solution worked flawlessly on my Ubuntu 10.04 system/avast Home Linux v. 1.3.0.

---

### Post by ZenStephanie on 2010-07-30
Is there any way to fix this problem without rebooting?
 
I'm trying to do a virus scan using the Ubuntu live CD, and feel nervous about partitioning my drive to install Ubuntu.
 
I'm frustrated because someone posted an easy "how to" use the live CD to scan and clean viruses and I can't get it to work because of something that could be fixed by the above but that I can't do without using a HD install instead of the live CD because nothing you do sticks after a reboot with a live CD #-o

---

### Post by quocthylb on 2010-07-31
Thanks a lot for the fix. It work perfect for me, Ubuntu 10.4.

---

### Post by lance bermudez on 2010-08-14
to fix the avast errror on a live cd run from the command line

sudo sysctl –w kernel.shmmax=128000000

then avast will run with out errors

---

### Post by upadhyaygautam on 2010-08-26
> **linuxgeek77 said:**
> Hello guys for those who dont have avast Linux here is the link to get it:
[[HTML] http://www.avast.com/linux-home-edition#tab4 [/HTML]]("http://www.avast.com/linux-home-edition#tab4")

get the .deb file for Ubuntu/kubuntu/xubuntu


ANyhow lately Avast has been crashing with engine errors. what i found out was that the problem was due to the fact that the size of the virus definitions database reached a system limit. it was a messup from avast linux team. that they overlooked this. Anyhow here is a quick way to fix it that will take you 30 seconds :)

[B]NOTE: KUBUNTU USERS USE KATE (instead of gedit) 
          XUBUNTU USERS USE MOUSEPAD (instead of gedit)[/B]

1) open the terminal
2) a)type this command to open the file you need to edit: 
        ```
sudo gedit /etc/init.d/rcS
```    b) type your password and hit enter

3) when the text file opens add the line:

    ```
sysctl -w kernel.shmmax=128000000
```4) make sure the line you added is before: 

```
exec /etc/init.d/rc S
```5.- This is how it should look like:
 ```
 #! /bin/sh
    #
    # rcS
    #
    # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
    #

    sysctl -w kernel.shmmax=128000000

    exec /etc/init.d/rc S
```6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST WILL WORK 100%


THANK YOU. please report back if it works for you :) 

I personally find avast to be one of the best Linux A/V available to scan windows partitions and/or incoming emails

credits go [here]("http://forum.avast.com/index.php?topic=57775.15")

WOrks with linux mint. AS i use linux mint. :)

Thanx
it worked for me

---

### Post by upadhyaygautam on 2010-08-26
Thank you very much
Avast was just installed and stopped working after first update
Your fix  made it work again
thanx a lot

---

### Post by 73ckn797 on 2010-08-27
This fix made the error go away but now the program simply will not start-up.

---

### Post by linuxgeek77 on 2010-08-28
that is weird can you post output you get when running from teh terminal. RUN with from the terminal by simply typing avast in the terminal.

---

### Post by linuxgeek77 on 2010-08-28
> **73ckn797 said:**
> This fix made the error go away but now the program simply will not start-up.

can you run it in the terminal? and post the output? please

---

### Post by 73ckn797 on 2010-08-29
> **linuxgeek77 said:**
> that is weird can you post output you get when running from teh terminal. RUN with from the terminal by simply typing avast in the terminal.

It runs from terminal but goes into a full scan, no graphical start-up. I am not at the desktop where it is installed right now. When clicking on the Avast icon  from the menu the computer grinds for a few seconds then nothing.

---

### Post by linuxgeek77 on 2010-09-03
try reinstalling avast. this has nothing to do with changing the shmax of your system ... if not try a different shmax configuration like this: sysctl -w kernel.shmmax=64000000  or sysctl -w kernel.shmmax=75000000

---

### Post by linuxgeek77 on 2010-09-03
> **73ckn797 said:**
> It runs from terminal but goes into a full scan, no graphical start-up. I am not at the desktop where it is installed right now. When clicking on the Avast icon  from the menu the computer grinds for a few seconds then nothing.

look at my previous post .. either try reinstalling or changing teh shmax value 


you can also try shmax 512000000  if you have more than enough memory

---

### Post by 73ckn797 on 2010-09-03
> **linuxgeek77 said:**
> look at my previous post .. either try reinstalling or changing teh shmax value 


you can also try shmax 512000000  if you have more than enough memory


When running from terminal Avast goes into a complete scan of my /home folder. No warning messages. You do not want me to paste in the terminal output due to the length.

When running from the menu selection, Avast does nothing. I just re-installed and it says it is already installed. I had to create a menu launcher to try a normal start-up into the gui.

I have changed the "shmax" values.

I know that I do not really need to have Avast. The laptop only has Ubuntu installed. Clamscan is installed. I only want it to scan attachments to emails.

---

### Post by linuxgeek77 on 2010-09-04
I think there is something wrong with our avast installation itself. Here is what to do. Remove it completely. that is look for it in apt-get and pu7rge it or remove it completely. go to you home folder > show hidden files (CTRL + H) and remove either (.avast /  or .avast4workstations or both if you have both. Remember to remove the file from there - its important, that is why its giving you the "already installed error". after you completely remove it  go to the avast site and redownload it and install it from scratch. and when you do that keep shmax value 128000000. and tell me if that works for you.

---

### Post by linuxgeek77 on 2010-09-04
> **73ckn797 said:**
> When running from terminal Avast goes into a complete scan of my /home folder. No warning messages. You do not want me to paste in the terminal output due to the length.

When running from the menu selection, Avast does nothing. I just re-installed and it says it is already installed. I had to create a menu launcher to try a normal start-up into the gui.

I have changed the "shmax" values.

I know that I do not really need to have Avast. The laptop only has Ubuntu installed. Clamscan is installed. I only want it to scan attachments to emails.

sorry read my reply above this post

---

### Post by 73ckn797 on 2010-09-05
> **linuxgeek77 said:**
> I think there is something wrong with our avast installation itself. Here is what to do. Remove it completely. that is look for it in apt-get and pu7rge it or remove it completely. go to you home folder > show hidden files (CTRL + H) and remove either (.avast /  or .avast4workstations or both if you have both. Remember to remove the file from there - its important, that is why its giving you the "already installed error". after you completely remove it  go to the avast site and redownload it and install it from scratch. and when you do that keep shmax value 128000000. and tell me if that works for you.

I realized that the start-up command is: ```
avastgui
```. The program runs just fine. The installer was not creating a menu selection and I forgot the gui command. My fault!

---

### Post by linuxgeek77 on 2010-09-05
> **73ckn797 said:**
> I realized that the start-up command is: ```
avastgui
```. The program runs just fine. The installer was not creating a menu selection and I forgot the gui command. My fault!

Okay so i am guessing its working but you have no menu entry. Do you know how to add your menu entry? Just edit the menu and add the entry manually.

---

### Post by 73ckn797 on 2010-09-05
> **linuxgeek77 said:**
> Okay so i am guessing its working but you have no menu entry. Do you know how to add your menu entry? Just edit the menu and add the entry manually.

Memory lapse about the correct command. I know how to add menu entries, Thanks.

---

### Post by bookcrazy on 2010-09-07
> **linuxgeek77 said:**
> Hello guys for those who dont have avast Linux here is the link to get it:
[[HTML] http://www.avast.com/linux-home-edition#tab4 [/HTML]]("http://www.avast.com/linux-home-edition#tab4")

get the .deb file for Ubuntu/kubuntu/xubuntu


ANyhow lately Avast has been crashing with engine errors. what i found out was that the problem was due to the fact that the size of the virus definitions database reached a system limit. it was a messup from avast linux team. that they overlooked this. Anyhow here is a quick way to fix it that will take you 30 seconds :)

[B]NOTE: KUBUNTU USERS USE KATE (instead of gedit) 
          XUBUNTU USERS USE MOUSEPAD (instead of gedit)[/B]

1) open the terminal
2) a)type this command to open the file you need to edit: 
        ```
sudo gedit /etc/init.d/rcS
```    b) type your password and hit enter

3) when the text file opens add the line:

    ```
sysctl -w kernel.shmmax=128000000
```4) make sure the line you added is before: 

```
exec /etc/init.d/rc S
```5.- This is how it should look like:
 ```
 #! /bin/sh
    #
    # rcS
    #
    # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
    #

    sysctl -w kernel.shmmax=128000000

    exec /etc/init.d/rc S
```6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST WILL WORK 100%


THANK YOU. please report back if it works for you :) 

I personally find avast to be one of the best Linux A/V available to scan windows partitions and/or incoming emails

credits go [here]("http://forum.avast.com/index.php?topic=57775.15")

WOrks with linux mint. AS i use linux mint. :)
Thanks a million. Worked just fine.

Ubuntu 10.04 on ACER Aspire 5610Z

---

### Post by noa097 on 2011-01-24
The fix worked for me too on as acer 2920z running Maverick. Thank you.

---

### Post by harmor on 2011-02-08
> **ZenStephanie said:**
> Is there any way to fix this problem without rebooting?
 
I'm trying to do a virus scan using the Ubuntu live CD, and feel nervous about partitioning my drive to install Ubuntu.
 
I'm frustrated because someone posted an easy "how to" use the live CD to scan and clean viruses and I can't get it to work because of something that could be fixed by the above but that I can't do without using a HD install instead of the live CD because nothing you do sticks after a reboot with a live CD #-o
I did the steps in the first post but instead of rebooting I chose "Suspend". After My monitor turned off I unsuspended Ubuntu and launched Avast.

---

### Post by Chiffer on 2011-03-06
Hi,

just starting to learn the wonderfull world of Linux and got stuck on this issue until I found this forum. Solution worked perfectly, thank you so much.


-Chiffer-

---

### Post by MiniT on 2011-04-07
Hey all.

I'm semi-new to Linux.  Just set up a dual boot with Windows 7/Linux Mint Julia,
on an Inspiron mini10 netbook.

I've got klamav set up, but I'm trying to get avast! set up too.
Had the same problems descibed, followed directions above, and no luck.
I used gdebi to install avast last night, update, and ran a quick scan.  
Alot of stuff didn't get scanned.
Problem was "incorrect configuration" error, I think.

Real problem occurs after first reboot - avast dies.
Gone from menu, errors everything when run.
I uninstalled with synaptic, deleted ".avast" from home folder.
Reinstalled, followed directions with gedit - correcting the /etc/init/rcS file.
After restart, avast gone from menu, scans error - configuration error.
Same thing every time, and gdebi says avast is already installed, right after installing it.
That even after getting rid of the folder in Home: .avast

Anything else I should try before giving up on this great virus scanner?

Thanks for being there folks - you're awesome.  :)

---

### Post by ibbill on 2011-04-07
Hi Welcome



Go in Synaptic In the search bar type Avast and then a new list will appear .. right click and select mark for complete removal or in a terminal the following

sudo atp-get remove avast

picked this up from this thread.

[http://ubuntuforums.org/showthread.php?t=535031](http://ubuntuforums.org/showthread.php?t=535031)

As an X windows user could not wrap my head around no virus scanner no spyware scanner no defrag. Dam I miss sitting there for  2 hours watching all the scans being done. NOT. You have clam should be enough. I first had a virus scanner when I started using linux finally got rid of it. I was tired of never finding a problem.lol

Bill

---

### Post by MiniT on 2011-04-07
IBill - 

Thanks for the fast reply.
Yeah, I can nuke it I suppose.

Two questions before I finally give up and give in:
1) In the commands above, is everything spelled just right - for sure?
    A. including "shmmaxx" or whatever, those commands that have to go in the rcS file?
    B.  "rcS" or "rc S"  ?
2) When I do wipe avast (sigh) I will completely remove with Synaptic, and also get rid of the ".avast" file in Home if it is still there.  Anything else?

Thank you for your help.
You're awesome.

PS. If I'm really paranoid, I have thumb drives I can use to run AV progs from. - the internet is dirty.  :)

---

### Post by ibbill on 2011-04-07
going in to synaptic and removing avast is the best way I would suggest

Having 2 virus scanners on a computer is not really recommended.

If you like use AVG

 [http://free.avg.com/us-en/download.prd-alf](http://free.avg.com/us-en/download.prd-alf)

You may also want to read this [https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

You must use a little common sense on where you surf also.

There may be some more input by other members also. So keep your eye on this thread.

---

### Post by MiniT on 2011-04-07
Thanks much for all of that!  Ubuntu Forums has SOOO much info.
Good stuff.  Will do.
You rock, thanks for being around, IBill.

From above: nautilus-clamav.
Right-click scanning for clamav.  Very useful!

Thanks all!

---

### Post by MonkWy on 2012-03-14
I have Ubuntu 10.04.4 LST after following instructions to fix the AVAST error engine failure to update I restarted and the Ubuntu hung and wouldn't restart. I shut it down and loaded it again and the AVAST Antivirus program was gone and all the sound was slow and different Ubuntu didn't run correctly so I removed the virtual machine and am starting from scratch.

---

### Post by luckymiky777 on 2012-06-11
> **linuxgeek77 said:**
> Hello guys for those who dont have avast Linux here is the link to get it:
[[HTML] http://www.avast.com/linux-home-edition#tab4 [/HTML]]("http://www.avast.com/linux-home-edition#tab4")

get the .deb file for Ubuntu/kubuntu/xubuntu


ANyhow lately Avast has been crashing with engine errors. what i found out was that the problem was due to the fact that the size of the virus definitions database reached a system limit. it was a messup from avast linux team. that they overlooked this. Anyhow here is a quick way to fix it that will take you 30 seconds :)

[B]NOTE: KUBUNTU USERS USE KATE (instead of gedit) 
          XUBUNTU USERS USE MOUSEPAD (instead of gedit)[/B]

1) open the terminal
2) a)type this command to open the file you need to edit: 
        ```
sudo gedit /etc/init.d/rcS
```    b) type your password and hit enter

3) when the text file opens add the line:

    ```
sysctl -w kernel.shmmax=128000000
```4) make sure the line you added is before: 

```
exec /etc/init.d/rc S
```5.- This is how it should look like:
 ```
 #! /bin/sh
    #
    # rcS
    #
    # Call all S??* scripts in /etc/rcS.d/ in numerical/alphabetical order
    #

    sysctl -w kernel.shmmax=128000000

    exec /etc/init.d/rc S
```6) save it

7) Reboot
AND THE NEXT TIME YOU RESTART -AVAST WILL WORK 100%


THANK YOU. please report back if it works for you :) 

I personally find avast to be one of the best Linux A/V available to scan windows partitions and/or incoming emails

credits go [here]("http://forum.avast.com/index.php?topic=57775.15")

WOrks with linux mint. AS i use linux mint. :)

Works wow thanks!:KS

---

### Post by oldos2er on 2012-06-11
Old thread closed.

---

