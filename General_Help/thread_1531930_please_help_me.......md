---
title: "please help me......"
date: 2010-07-15
forum: General Help
---

### Post by marvin04 on 2010-07-15
i am currently using ubuntu 10.04 ....
i really like because it is really fast..
but i've got set of problems...
first.. i cannot watch videos from youtube, or anime websites like, animefreak.tv, crunchyroll.com, anime-media.com etc. i don't know what's the problem because i think i've already tries almost everything i can find in the web that can help me, i tried installing the flash player "APT for Ubuntu 9.04+" , "tar.gx" installing it creating a folder to put it in.. and its already frustrating me.. 
i really like linus so pls help me on this,,,

---

### Post by bobcollard on 2010-07-15
> **marvin04 said:**
> i am currently using ubuntu 10.04 ....
i really like because it is really fast..
but i've got set of problems...
first.. i cannot watch videos from youtube, or anime websites like, animefreak.tv, crunchyroll.com, anime-media.com etc. i don't know what's the problem because i think i've already tries almost everything i can find in the web that can help me, i tried installing the flash player "APT for Ubuntu 9.04+" , "tar.gx" installing it creating a folder to put it in.. and its already frustrating me.. 
i really like linus so pls help me on this,,,
As you have determined the problem is flash player.  Open Synaptic Package Manager and enter "flash" w/o quotes as the search term.   You need to install flashplugin-installer and flashplugin-nonfree  That should do the trick.

---

### Post by marvin04 on 2010-07-16
> **bobcollard said:**
> As you have determined the problem is flash player.  Open Synaptic Package Manager and enter "flash" w/o quotes as the search term.   You need to install flashplugin-installer and flashplugin-nonfree  That should do the trick.

i am really new here dude.. so i hope you don't mind me following up a question.. how will i install flashplugin-installer and flash plugin-nonfree.. when i open the synaptic package manager flashplugin-installer and flash plugin-nonfree is already there does that mean its already installed??

---

### Post by Samulus on 2010-07-16
Try going to the menu, then accessories, then go to terminal, then type sudo apt-get install adobe-flashplugin into the terminal and hit enter, you should be promted for your password but it won't show you entering your password.

---

### Post by smardi on 2010-07-16
[I]i am really new here dude.. so i hope you don't mind me following up a question.. how will i install flashplugin-installer and flash plugin-nonfree.. when i open the synaptic package manager flashplugin-installer and flash plugin-nonfree is already there does that mean its already installed??
[/I]


You will have to select the check box opposite to the software you like to install and click on apply on top tool bar.

You have another option by going through command line.

Thanks

---

### Post by Yarui on 2010-07-16
> **marvin04 said:**
> i am really new here dude.. so i hope you don't mind me following up a question.. how will i install flashplugin-installer and flash plugin-nonfree.. when i open the synaptic package manager flashplugin-installer and flash plugin-nonfree is already there does that mean its already installed??
The list that shows up is a list of available programs.  You know that it is installed if the square to the left of the name is green.  If it isn't, click on the square and click "mark for installation", and then hit the apply button at the top of the window.

Aside from the flashplayer plugin, I would also recommend installing the package ubuntu-restricted-extras.  Either do it through synaptic or in the terminal use
```
sudo apt-get install ubuntu-restricted-extras
```
This package installs several popular plugins and video/audio/dvd playing codecs.

---

### Post by marvin04 on 2010-07-16
tnx tnx for the rply.. but it just doesn't work.. i've already done what you told me to do.. and as i check it in synaptic package manager it is already installed.. the box beside it is already marked as installed.. another thing that confuses me is that i was able to watch some (very few like 3 or 4) video from youtube.. are there video formats that my ubuntu can play and cannot?? but still i can't watch anything from anime sites...

---

### Post by Nick_Jinn on 2010-07-16
> **marvin04 said:**
> i am currently using ubuntu 10.04 ....
i really like because it is really fast..
but i've got set of problems...
first.. i cannot watch videos from youtube, or anime websites like, animefreak.tv, crunchyroll.com, anime-media.com etc. i don't know what's the problem because i think i've already tries almost everything i can find in the web that can help me, i tried installing the flash player "APT for Ubuntu 9.04+" , "tar.gx" installing it creating a folder to put it in.. and its already frustrating me.. 
i really like linus so pls help me on this,,,


As long as you dont live in a country where this is illegal...ahem...In some places it is perfectly legal to install Medibuntu, which should take care of all your media needs.


Try this. You wont regret it.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


I currently use mint which IS Ubuntu + a few unique tools and codecs, but those small tweaks make it really easy to use compared to Ubuntu proper.....If you continue to have trouble with Ubuntu, try Linux Mint.


Nobody, and I mean nobody will get in trouble for using Medibuntu as an individual user....however, there are licensing issues for SHIPPING and SELLING commerical PCs without paying a few cents a piece for these codecs and drivers or the licensing or whatever. You can pay for these extras or you can install medibuntu and do everything Windows can do and a lot more.


Always check local laws to make sure you are not doing anything illegal. Only take my advice if you live in a country where this is legal.

---

### Post by Yarui on 2010-07-16
I'm sure you probably don't, but you wouldn't happen to have any javascript blocking plugins in your browser, would you?  If so these could conflict with your ability to play videos.

Other than that I'm not sure.  Videos have always worked for me as soon as I successfully installed flash.

For youtube you can choose to opt into the html5 beta version of youtube here:

[http://www.youtube.com/html5](http://www.youtube.com/html5)

but this won't solve your problem with those other sites you mentioned.

---

### Post by marvin04 on 2010-07-16
> **Nick_Jinn said:**
> As long as you dont live in a country where this is illegal...ahem...In some places it is perfectly legal to install Medibuntu, which should take care of all your media needs.


Try this. You wont regret it.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


I currently use mint which IS Ubuntu + a few unique tools and codecs, but those small tweaks make it really easy to use compared to Ubuntu proper.....If you continue to have trouble with Ubuntu, try Linux Mint.


Nobody, and I mean nobody will get in trouble for using Medibuntu as an individual user....however, there are licensing issues for SHIPPING and SELLING commerical PCs without paying a few cents a piece for these codecs and drivers or the licensing or whatever. You can pay for these extras or you can install medibuntu and do everything Windows can do and a lot more.


Always check local laws to make sure you are not doing anything illegal. Only take my advice if you live in a country where this is legal.

is this one just like any plug ins? i mean it sounds as if its another version of linux.. will it not corrupt some files in ubuntu?? sorry if i sound like i don't trust your reply only it is so different from the others... hope you don't mind..:p

---

### Post by marvin04 on 2010-07-16
> **Yarui said:**
> I'm sure you probably don't, but you wouldn't happen to have any javascript blocking plugins in your browser, would you?  If so these could conflict with your ability to play videos.

Other than that I'm not sure.  Videos have always worked for me as soon as I successfully installed flash.

For youtube you can choose to opt into the html5 beta version of youtube here:

[http://www.youtube.com/html5](http://www.youtube.com/html5)

but this won't solve your problem with those other sites you mentioned.

oh so there are javascript blocker plug in?? i don't really know if i have one.. you mind if i ask how will i know if i have one or not.. and how will i remove it?.. tnx...

---

### Post by Yarui on 2010-07-16
> **marvin04 said:**
> is this one just like any plug ins? i mean it sounds as if its another version of linux.. will it not corrupt some files in ubuntu?? sorry if i sound like i don't trust your reply only it is so different from the others... hope you don't mind..:p
That link he gave was to a page of the official ubuntu documentation, so I'm pretty sure it is Ubuntu-compatible.  The only reason the repo isn't included by default is because of laws in some countries, as stated above.

---

### Post by Yarui on 2010-07-16
> **marvin04 said:**
> oh so there are javascript blocker plug in?? i don't really know if i have one.. you mind if i ask how will i know if i have one or not.. and how will i remove it?.. tnx...
If you don't know, you don't have one.  It's something you would have to add to your browser intentionally.  The most popular one I know of is called noscript.  It is a program that blocks all javascript from sites that are not marked as trusted.

---

### Post by marvin04 on 2010-07-16
> **Yarui said:**
> If you don't know, you don't have one.  It's something you would have to add to your browser intentionally.  The most popular one I know of is called noscript.  It is a program that blocks all javascript from sites that are not marked as trusted.

oh ok.. tnx yarui.. anyways, i tried the code you gave, still i cant watch anything.. the video in you tube is still pitch black..

---

### Post by Yarui on 2010-07-16
> **marvin04 said:**
> oh ok.. tnx yarui.. anyways, i tried the code you gave, still i cant watch anything.. the video in you tube is still pitch black..
If you are referring to the html5 link I gave you, that's a little surprising.  Maybe your video drivers aren't properly set up.

EDIT:  Oh, actually, if you are running Firefox 3.6, it might not have html5 support.  Maybe check your browser version and find out if it supports html5.  You could try using the Chromium browser to view the html5 page.

---

### Post by Nick_Jinn on 2010-07-16
> **marvin04 said:**
> is this one just like any plug ins? i mean it sounds as if its another version of linux.. will it not corrupt some files in ubuntu?? sorry if i sound like i don't trust your reply only it is so different from the others... hope you don't mind..:p


No, its a repository of software and plug-ins and contains many different files and codecs. It has everything you need for seamless media viewing in just about any format, even non free ones.

In Mint (especially the DVD version) everything works out of the box, but you can do it in Ubuntu as well with a little more tweaking. Just cut and paste the commands into the terminal....its not scary once you get the hang of it. Just remember that in the terminal you cant use control V, you have to right click and click 'paste'. You can however use control C to copy the original text.

You might also want a program called Devede. It allows you to take videos that you might download with torrent in AVI or DivX formats and convert them into formats for standard DVD and video CD formats.

Ubuntu is awesome, though I find that the 'Control Center' in Mint opened me up to a whole new world of customizing my desktop to enable eye candy that I never even knew existed after 4 years of using regular Ubuntu....and its basically still Ubuntu, only it should play your videos out of the box. I use the DVD version, 32 bit for PCs with less than 3gb of ram, and 64 if they support more ram and have a 64bit chip.



Also......after searching for 'restricted extras' and enabling them, or medibuntu which is even better, try restarting your computer. A lot of effects dont work until you reboot.

Also, maybe install the drivers for your video card...the controls in mint are a little different, but for me I go to 'Control Center', hardware drivers, then click on the most recent drivers....it wont work until I reboot.


I cant believe I am the one giving advice. now You learn a lot about computers using linux.

---

### Post by marvin04 on 2010-07-16
tnx nick.. anyways. i already went to the site you gave.. i copy pasted every code there.. still i am not being able to watch anything.. this is really frustrating but i am still willing try... so i just need to copy paste the code right.. then it will automatically run.. i already run the code at the terminal, will there be any bad effect if i run it again???

---

### Post by Nick_Jinn on 2010-07-16
You did it properly? You didnt copy the $ did you?

Why dont you cut and paste what it said in the terminal and maybe that will give us some clues to what you did wrong.

Or, if you just add the keyring you can add it from Synaptic Package Manager, which is the easiest way.

OR.....Medibuntu is already included in Mint 9 Isodora. Its basically Ubuntu with training wheels, but it can pretty much do everything Ubuntu can.

---

### Post by AceRoom on 2010-07-16
@Freaky. You will get banned for that sort of thing.

---

### Post by SnickerSnack on 2010-07-16
> **freaky88 said:**
> oh crap i didnt know =\ my bad

Uh-huh.  Is that why all of your other posts are like that?  A simple mistake, right? :rolleyes:

---

### Post by smardi on 2010-07-16
> **marvin04 said:**
> is this one just like any plug ins? i mean it sounds as if its another version of linux.. will it not corrupt some files in ubuntu?? sorry if i sound like i don't trust your reply only it is so different from the others... hope you don't mind..:p

this may help

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by DrDevice on 2010-07-16
I found this post early on, and it saved me a lot of time setting up multimedia aspects of my installation:

[[COLOR="Blue"][all variants] Comprehensive Multimedia & Video Howto - Ubuntu Forums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Just follow the directions for your version, most of it is simple copy & paste.

---

### Post by savaan on 2010-07-17
i'm having the exact same problem. been trying for days to get my flash to work. in the package manager i've installed flashplugin-installer and flashplugin-nonfree. if i try to get it through the terminal i get

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I'm lost :/

---

### Post by Bradj47 on 2010-07-17
[http://ubuntuforums.org/showthread.php?t=1369839](http://ubuntuforums.org/showthread.php?t=1369839)

---

### Post by tee_snipes on 2010-07-17
Hi,
Have you tried to install maybe youtube or any of the other site from the videos that you are trying to watch from the terminal? I mean i'm new to ubuntu also but i would try to start there though. Give me a day or so and i will ask my professor about that and i will get back to you with a solution if you like?

---

### Post by savaan on 2010-07-17
eh, i've been doing this for days. every time i try to get the adobe plugin it tells me it can't find something else. its only firefox...i just installed seamonkey and have no issues at all

---

### Post by Nick_Jinn on 2010-07-18
Yeah, firefox....

Have you tried viewing it in Opera? Opera is so much better than it used to be. It surprised me. I think its even better than Chromium now.

---

### Post by marvin04 on 2010-07-18
> **tee_snipes said:**
> Hi,
Have you tried to install maybe youtube or any of the other site from the videos that you are trying to watch from the terminal? I mean i'm new to ubuntu also but i would try to start there though. Give me a day or so and i will ask my professor about that and i will get back to you with a solution if you like?

tee_snipes... yeah, plss, plss, plss, do ask it to your proffesor... and tnx in advance.. anyway, how will i watch the videos from the terminal??

---

### Post by marvin04 on 2010-07-18
> **DrDevice said:**
> I found this post early on, and it saved me a lot of time setting up multimedia aspects of my installation:

[[COLOR=Blue][all variants] Comprehensive Multimedia & Video Howto - Ubuntu Forums[/COLOR]]("http://ubuntuforums.org/showthread.php?t=766683")

Just follow the directions for your version, most of it is simple copy & paste.
  gawd!!!! tnx much!!! the site totally helped me.. and i'm ok now!!!!!! again, tnx so much!!!!!

---

### Post by digitalcitizenx on 2010-07-18
> **marvin04 said:**
> gawd!!!! tnx much!!! the site totally helped me.. and i'm ok now!!!!!! again, tnx so much!!!!!

I would suggest marking this as solved but........

---

### Post by AceRoom on 2010-07-18
@digitalcitizenx, what do you mean exactly by:
> **[COLOR=Red]Remember[/COLOR]** - if Ubuntu breaks you get to  keep **BOTH** pieces. 			

Do you mean that you can recover the data easily? Just curious :)

---

