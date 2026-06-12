---
title: "How to install CDemu in Ubuntu 9.10"
date: 2010-03-29
forum: General Help
---

### Post by trixa_13 on 2010-03-29
How do I install CDemu in Ubuntu 9.10? I've googled it and I found many instructions to install. But I can't seem to understand and I'm afraid that I might take a wrong turn in installing it. And I also found comments saying that, that instruction didn't work for them.

I'm looking for an easy instruction. Sorry because I'm new to Linux. Please bear with me. ;)

And anybody who has an idea how to mount .bin and .cue files? That's the main reason why I wanted to install CDemu.

---

### Post by trixa_13 on 2010-04-01
> **trixa_13 said:**
> How do I install CDemu in Ubuntu 9.10? I've googled it and I found many instructions to install. But I can't seem to understand and I'm afraid that I might take a wrong turn in installing it. And I also found comments saying that, that instruction didn't work for them.

I'm looking for an easy instruction. Sorry because I'm new to Linux. Please bear with me. ;)

And anybody who has an idea how to mount .bin and .cue files? That's the main reason why I wanted to install CDemu.

help!!!

---

### Post by varunendra on 2010-04-22
Hi buddy! At least you should have mentioned some links you found. Maybe they could have worked for me and then, me being a beginner as well, maybe I (or someone else) could have worked out some "easy set of instructions" ;) for you.

However, I'm also struggling at the moment with my quest for a virtual drive for linux and shall certainly update here "IIF (mathematically;))" I got cdemu working or found some other solution.

And btw, I need this to satisfy apps that recognise or accept only "actual" CDs/DVDs, not their mounted contents (like some games, bootable non-iso images for VirtualBox,....)

For instance, I currently need this to get a bootable .nrg image recognised by VirtualBox. I frequently work with such "non-standard" CD images & converting them to iso or simply mounting them anyhow to a 'folder' (even if it is /media/cdrom, VB won't recognise it as a CD) isn't a practical solution for me.:-k

---

### Post by towheedm on 2010-04-26
> **trixa_13 said:**
> How do I install CDemu in Ubuntu 9.10? I've googled it and I found many instructions to install. But I can't seem to understand and I'm afraid that I might take a wrong turn in installing it. And I also found comments saying that, that instruction didn't work for them.

I'm looking for an easy instruction. Sorry because I'm new to Linux. Please bear with me. ;)

And anybody who has an idea how to mount .bin and .cue files? That's the main reason why I wanted to install CDemu.

CDEmu can be easily installed with the Synaptic Package Manager.  Open it by clicking on System => Administration => Synaptic Package Manager.

Type [COLOR=Red]cdemu[/COLOR] in the search box.  There are currently 6 packages.  You may want select all or only those based on your needs.  Now click on Apply (the check mark).

Hope this helps.

---

### Post by joes7 on 2010-04-26
> **towheedm said:**
> CDEmu can be easily installed with the Synaptic Package Manager.  Open it by clicking on System => Administration => Synaptic Package Manager.

Type [COLOR=Red]cdemu[/COLOR] in the search box.  There are currently 6 packages.  You may want select all or only those based on your needs.  Now click on Apply (the check mark).

Hope this helps.
This should work just fine, if it doesn't feel free to PM me or to email me. Good luck!

---

### Post by varunendra on 2010-04-27
> **towheedm said:**
> CDEmu can be easily installed with the Synaptic Package Manager.  Open it by clicking on System => Administration => Synaptic Package Manager.

Type [COLOR=Red]cdemu[/COLOR] in the search box.  There are currently 6 packages.  You may want select all or only those based on your needs.  Now click on Apply (the check mark).

Hope this helps.
Umm....mmm le'me think.... :-k

> **joes7 said:**
> This should work just fine, if it doesn't feel free to PM me or to email me. Good luck!
.... oh, thanx... really appreciate your generous help !8-[

Hey towheedm/joes!
First, I really appreciate your try to help the guy. BUT..... I think there's just a little problem (at least that I came across, then overcome it;))

I just got it working yesterday. But NONE OF THE PACKAGES WERE LISTED BY DEFAULT !

I searched on the net & found the following line to be added to the sources list:
> deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) intrepid  main(It was meant to be a solution for Ubuntu 8.10 Intrepid Ibex) However I made the following correction workable:
> deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) **jaunty**  main
*(...also tried- [deb [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) **karmik**  main] but it wasn't found)*Only after adding the above line, the cdemu packages showed up in synaptic (although on refreshing- I got a warning/notification about possible incompatibility of those packages, (since they originally belonged to jaunty))
Even after installing the packages, it needed some excercise (well... not so hard, and I must say, the program is worthy of it !)
Here's the manual procedure I followed:
> [http://www.my-guides.net/en/content/view/138/](http://www.my-guides.net/en/content/view/138/)
(the third method on this page)However, what worked for me was slightly different from what was instructed. For convenience, I'm sharing my experience in next post....

---

### Post by varunendra on 2010-04-27
[SIZE=4][COLOR=DarkRed]**_How I Got CDEmu Working_:**[/COLOR][/SIZE]

Here's the manual procedure I followed:
[http://www.my-guides.net/en/content/view/138/](http://www.my-guides.net/en/content/view/138/) (3rd method on this page)

(However, what worked for me was slightly different from what was instructed.)

Ok, here goes my story:-  (due to my extremely limited experience with Linux, I can't dare to call  it "set of Instructions"). Anyway, here it is:-

[LIST=1]
[*]I went to **system>administration>software  sources** (it asked my password, I supplied it)
[*]Got to "**Other  Software**" tab. Clicked on "**+Add..**"
[*]The typical  dialogue-box opened asking- "Enter the complete APT line....."
[*]In  the 'APT Line' field, I typed- > **deb  [http://ppa.launchpad.net/cdemu/ubuntu](http://ppa.launchpad.net/cdemu/ubuntu) jaunty  main**
[*]Clicked on "**Add Source**" to close the  box. Clicked again on "**Close**" on "Software Sources" box getting  this notification- "The information about available software is  out-of-date ...... blah-blah-blah...." Nothing to worry! Its usual.
[*]Clicked  on "**Reload**" & after refreshing repository, it returned  following error:- > An error occurred .... W: GPG error:  [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures  couldn't be verified because the public key is not available: NO_PUBKEY  423A2125D782A00F
 Again... Nothing to worry! It is usual too  when you add an unsupported repository source;)  (we added "jaunty", not "karmik"- remember?) However maybe someone can  provide us the "Public Key" also to keep Mr. Synaptic happy &  satisfied. I don't know the key, & didn't bother either.
[*]Just  clicked "Close" again on the error box. It took some time to disappear.
[*]Now,  I went to **SYSTEM>ADMINISTRATION>SYNAPTIC PACKAGE MANAGER**,  and typed "**cdemu**" into the "**Quick Search**" box.
[*]The  following packages showed up: **cdemu-client, gcdemu, cdemu-daemon,  vhba-dkms, cdemu-daemon-dbg, mirage-image-analyzer, libmirage2,  libmirage1**.
[*]Of these I selected only **gcdemu**, the rest  of the required packages ([COLOR=Red]**cdemu-daemon, vhba-dkms, libmirage2**[/COLOR])  got selected automatically as they were dependencies. Then I clicked "Apply Changes" & after confirmation, the packages were installed.
[*]Now time  for some final touch! I opened terminal and typed- > sudo /etc/init.d/cdemu-daemon start
[*]Rebooted (or just logout & log back  in- whatever works for you) and.... > Finally right click somewhere  on the panel and click Add to Panel. Find  gCDemu and click the Add button. If you see the applet grey it isn't  connected to the daemon. It should be blue-yellow. I had to restart  Ubuntu to make gCDemu work properly.(- qouted from the web page I  referred in the first link in this post) I also had to restart!
[*]Now...  guess what ! Even after restarting my gCDEmu applet didn't turn  blue-yellow, i.e., it wasn't connected to the cdemu-daemon. After some  more research, I got this working (I have to do it everytime I restart  my system, so follow it VERY CAREFULLY! Hey don't faint... it's JUST TWO  WORDS in terminal ;)):-
[*]The  applet doesn't automatically get active on startup. So everytime I wish  to use it, I have to supply the following command through terminal:-  > sudo cdemud I was asked for my password which I supplied and voila !! The applet I just added to the  panel turned blue-yellow ! Remember- after entering the "sudo cdemud"  command, the terminal will show something like-  > varun@varun-desktop:~$ sudo cdemud
[sudo] password for varun: 
Starting  daemon in local mode with following parameters:
 - num devices: 1
 -  ctl device: /dev/vhba_ctl
 - audio driver: null
 - bus type:  system

and leave a blinking cursor, won't return to  prompt where you can typ another command. It may seem to you as hung,  but it's the way it works:lol:.
[*]I  opened "Computer" & there was an extra cd drive just created.
[*]I  clicked the gCDEmu applet, selected the "now created" drive and a  browser window popped up asking me to select the image I wished to mount.  Need more instructions about what to do from now on..... ???
[/LIST]
I  opened Virtual Box, and in its drives list - to my utter surprise -  there was another cd drive showing up for the first time besides my  actual drive. I'm crazy guys... (well..... not really, only momentarily u  see !)

Oh! one more thing.... the device or the applet (gCDEmu  icon on panel) remains active only as long as I don't close the terminal  in which I typed the "sudo cdemud" command (....well, not a problem for  me). To stop the daemon, just press ctrl+c or simply close the  terminal.
If you wish to use the terminal while running cdemud, just  open another tab or a new terminal.

And yeah.... the list of the  supported cd/dvd image types is lo.....ng - really long.
For me,  except for the protection emulation thing, it's nothing less than  Daemon-Tools for Windows.

Rejoice!

-Varun

---

