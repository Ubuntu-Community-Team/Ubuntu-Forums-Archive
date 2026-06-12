---
title: "Is your firefox 3 graying out? I might Have the fix for you!"
date: 2009-08-01
forum: General Help
---

### Post by mwillams73 on 2009-08-01
I didn't know whether to put this in General help or Desktop environments so i put it here, @mods feel free to move this to whichever category is most helpful. 

I had this problem with firefox 3 and after searching the forums couldn't find a solution, so , I took the initiative and fixed it myself.

Technically this Only helps people using Hardy with compiz enabled, Although it could also work with other distro's.

My problem was that Firefox 3 would gray out and or freeze also timing out for as much as a few minutes. This happened at MY Yahoo, Myspace, Face Book, and even a few sites that dont use java or any flash at all. It would happen on one site but not another then it would happen at another site but not the first one. Note that it didn't do it at all when compiz was turned off (no effects selected in appearances).

Now normally I would just turn off compiz and be done with it, but I had another problem with the Volume OSD not showing the correct percentage level when not using compiz, Example The speaker has three parenthesis marks coming out of the speaker when turned up to full volume, two parenthesis marks at 2 thirds, one parenthesis marks at low volume and finally the red X for mute. this how its supposed to work normally, In my case though it was either 100% (three parenthesis marks) or muted X mark.

The volume went up and down as it is supposed to, only the OSD was acting up. I'm picky about things like that because when I'm showing off my system it should look as good as I've told people it does. Anyways, still havnt fixed that yet it only works properly if I have compiz turned on, which brings me back to the Firefox 3 graying out issue.

I completely uninstalled all firefox entries in synaptics(full removal including config files) and then went to my home folder and pressed cntrl and H to get to hidden folders, I then navigated to the .mozilla folder and deleted it and its contents.

I then rebooted and reinstalled firefox 3, after importing my bookmarks and installing some add ons (yahoo toolbar,adblock,mouse gestures redox,downthemall) I noticed the graying out returned.The odd thing is that the graying coincided with the install of mouse gestures redox, as soon as FF3 restarted and loaded my yahoo it started graying out again, So I disabled mouse gestures redox and restarted FF3 again and guess what? No more graying out!!!

I really hope this helps anyone in solving their issues with FF3, if you need more detailed instructions or if you can help me with my Volume OSD issue feel free to comment or add to this thread so that maybe all of us can get FF3 back to its glory while using compiz and without it also!!

PS: I told people how to do it the GUI way out of preference, If you want to post the terminal way That would be fine too, Ive noticed that newcomers are afraid of the terminal and gave them a way to do it that they might be more comfortable using. Happy browsing!!!!

---

### Post by CatKiller on 2009-08-01
> **mwillams73 said:**
> Note that it didn't do it at all when compiz was turned off (no effects selected in appearances).

The fade windows plugin (which makes the window grey when it is unresponsive to the window manager) is provided along with Compiz. It is still possible for a window to become unresponsive without it, you just won't get the indication.

Glad you've got your problem sorted out, though.

---

### Post by Raffles10 on 2009-08-01
A more common solution that people have found is:

open the gconf-editor (alt+f2), then go to:

apps > compiz > general > allscreens > options /ping_delay

Change the value to something higher. (eg: 6000, 7000, 8000 etc)

To see the range in which you have to work, highlight 'ping_delay' and look in the description window at the bottom..

I've found that 10000 works for me. :D

---

### Post by mwillams73 on 2009-08-01
Awesome! Thanks you guys! Im going to try those suggestions out here in a lil bit. So far my fix has been working well. Now we actually have some real answers to fix this too. Im glad theres a way to do it in config editor, I looked but couldnt figure out what i was supposed to do, So Again many thanks to you!!!!!

---

### Post by mwillams73 on 2009-08-01
I totally forgot to add that when you uninstall Firefox it also removes sunjava-6, so if you need that id suggest reinstalling it because it doesnt get reinstalled with firefox3 It comes with the ubuntu restricted extras pack. Although Ive found without sun java my FF browser is much more responsive and faster all the way around. So its up to you. 

On another note: I highly suggest getting Aptoncd, Its in the repos and you can navigate to add/remove programs and download it from there, saves a lot of hassle when youve borked your system and you have to do a fresh install. 

Once downloaded you can find it in System/Administration. It should be the first on the menu. just open it up and it asks if you want to make a cd or dvd and then shows you a window with all your installed programs clik next or foward or whatever and it makes an ISO when its done it asks if youd like to burn that ISO with your favorite burning program. Upon Insertion of the cd/dvd it promptly asks if youd like to open synaptics and install all those programs.

What I like about it is that i have a really slow internet connection (8/kbs per second) so its a pain when i have to fresh install after tweaking or trying to fix something. With Aptoncd its a breeze. Itook less than 5 minutes to put my system back the way it was before it screwed up.

Sorry but i had to add this for those who try this and something goes wrong, It basically backs up any installed programs and the updates to those programs. The saying Goes : Back Up Often And You'll Have No Problem Moving Forward.

---

