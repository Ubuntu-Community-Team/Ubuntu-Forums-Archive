---
title: "Multiple Keyboard Layouts going postal..."
date: 2010-01-06
forum: General Help
---

### Post by b00nish on 2010-01-06
Hey There

As a KDE user I have to ask you for help with a problem I'm experiencing with a Ubuntu/Gnome installation I'm doing for a friend of mine.

The task sounds quite simple but it drives me crazy:

I want to have two keyboard layouts ("Thailand -> Thailand" and "Switzerland -> Switzerland German nodeadkeys") and being able to switch between them.

The Ubuntu installation already has two user accounts - one of them logs in with thai language (language, NOT keyboard layout!) by default, the other one with german language. This works great.

The keyboard layout which I used for the installation was "Switzerland -> Switzerland German nodeadkeys". Now I tried to add "Thailand -> Thailand" and the problems started...
Instead of two layouts I got three... it added "Switzerland -> Switzerland" as a third layout. I don't know why, I didn't cause anything like this. Having three layouts (of which two are nearly identical) is annoying because you now have to switch trough three instead of two layouts.

But that's just the beginning. Following problems:

- I'm unable to delete the unwanted third layout, it keeps reappearing after reboot/relog
- On the LogIn Screen it seems quite randomly which layout is selected for LogIn
- After LogIn it's randomly between which layouts I can switch. Sometimes the three are there, sometimes only two and sometimes only one. It seems that there is no way to determine, which öayouts will be there, it's a complete chaos!

The wohle thing is really distrubing me, since my settings (Preferences -> Keyboard) are mostly ignored and it's totally random after every reboot.


Since I can't even try to do it right by editing the xorg.conf (which is almost empty in Ubuntu 9.10 [I personally use Kubuntu 8.04 where I never have been confronted whit such problems]) I really need your help. I don't know how to reset this mess and I don't know how to do it correctly. 
The Keyboard Layout Configuration GUI provided by Gnome doesn't seem to be a big help since the settings I do there will be ignored respectively changed at random after every LogOut.

Thanks for your help!

---

### Post by mkvnmtr on 2010-01-06
On my Ubuntu Gnome there is a keyboard preference. It was pretty easy to get a spanish and english keyboard enabled. Then I put a switcher in the panel. Been a long time so I do not remember exactly. Why not open the panel and take a look and come back with what you find, Maybe even post a picture. I remember it being easy so when you get it opened you might not need more help

---

### Post by b00nish on 2010-01-06
Hey, thanks for your posting but I fear it doesn't help.

I already have the switcher in the panel and it allows me to switch between the enabled layouts. But unfortunately Ubuntu keeps losing the settings about which layouts should be enabled. As I said this seems to be quite at random... sometimes three are enabled (of which one is unwanted), sometimes two, often only one (and this isn't always the same).

Theoretically it should be totally easy (as you say) but the point is: It doesn't work properly. So I guess my problem is not that I don't know how to use the GUI but my problem is, that the GUI doesn't work. Or at least there is some issue that keeps confusing the settings after every LogOut.

Im currently unable to provide pictures since the computer whit the issue doesn't have internet connection at the moment.

---

### Post by rnerwein on 2010-01-07
hi 
i can't help you, but i can tell you that ubuntu 9.10 is able to hadle the layouts.
i have connected a thai keyboard on PS2 and a german on usb. got my panels. can switch every time.
my wife starts her login with thai language and german keyboard layout and switch to thai layout after login.
ciao

---

### Post by b00nish on 2010-01-07
Hi rnerwein

That what you describe is that what I want to have. That Ubuntu 9.10 theoretically is able to handle the layouts I've already seen.

But my problem is, that it keeps messing up the whole layout thing after every LogOut.

So what I need is a way to reset this chaos and then doing it right. 
Probably it would help me if someone could tell me where the corresponding config files are.

---

### Post by rnerwein on 2010-01-07
hi - first a fact. i have two accounts. one for me and one for my wife. that means:
on the login screen i choose lang. german (DE) and keyboard german too.
on the login screen my wife choose for her account lang. thai keyboard german (to type her passw. in and so i can login to her account too. after login see select on the panel keyboard layout --> thai
i add this to the panel by right klick -> add to panel -> keyboardindikator (tastaturindikator). it works
when i log in to her account i choose: both german . when the desktop comes up a window pops up and ask me to convert thai to german (i klick ye indeed that i can work). the window pops up on the next time when my wife logs in and see choose german to thai. this happens only once after i was i was loged in before. i can work with both keyboards. one is only german and the other is thai and english (where y = z and so but thats no problem i got a shell scrip myxmodmap to switch it). but sorry i don't know where are the config files.
i hope you will get rid of your problem - if i find more information i will post it
ciao

---

### Post by b00nish on 2010-01-07
Thanks for your answer again :)

Yes, what you have, is exactly the situation I want to have. And as I mentioned I have no problem with the two accounts, the language of the system or the switcher panel. All these things are working.
The only thing that is NOT working is the configuration of the keyboard layouts. I can configure them, but after every LogOut, the configuration is lost and replaced by a random configuration which varies with every LogIn. I know this doesn't sound like something a computer would do (since a computer usually keeps doing the same faults but not chanching it's failure randomly) - but unfortunately my computer does exactly like I said.


I have found out that there are keyboard layout setting for each user in **/home/username/.gconf/desktop/gnome/peripherals/keyboard/kbd/%gconf.xml**
I can edit them and I can see how they change if I configure the settings with the GUI.
But again: When I LogOut and LogIn again, the settings (and of course the gconf-file too) are changed. I tried to do a write protection on this file but even if it's read only for the owner (= the user) and no access for 'group' and 'others' it still keeps changing after the LogIn. Whatever keeps messing up the configuration... it just ignores the write protection (or probably I just don't know how to do a proper write protection?)

So my problem still exists :(

I guess it would be interesting to find out, where the settings are, that determine te keyboard layouts which are chooseable in the LogIn screen...

---

### Post by b00nish on 2010-01-07
Oh my god...
Now I think I found a way to do a REAL write protection on the config file (using **chattr +i**)
But guess what..?
Now it just creates a NEW config file called %gconf.xml.new in the folder and writes the wrong settings there...
I ask myself why there is a settings file at all if the system never reads and applies it's content but just uses it as a dump for some faulty and randomized settings of which I don't know where they come from...

Now I'm gonna 'chattr' the whole folder... wonder how it will react to this!

EDIT:

Hah..! As I suspected... the whole config files are a joke.. it doesn't matter at all what's written in there. Now that I managed it that the system is unable to change the config files it just IGNORES them!
I have now a config file in which the right settings are written (since I prevented the systems from changing them) but still the settings are faulty after LogIn.
So obviously, the settings that determine the keyboard layouts don't come from the above mentioned config files... 

So I guess I have two options now (aside from sending Gnome packing...)

1. Find out where the REAL settings are
2. Write a script which correct the layouts after every LogIn

For both options I ask for your help.

---

### Post by b00nish on 2010-01-07
I've got a workaround :D

Thanks to the help I've been provided with in the German Ubuntu Forums (Thread: [http://forum.ubuntuusers.de/topic/tastaturlayout-ausser-kontrolle/](http://forum.ubuntuusers.de/topic/tastaturlayout-ausser-kontrolle/) ) I've now a workaround for this Problem:

I had to create a shellscript

```

#!/bin/bash
setxkbmap -model pc105 -layout ch,th

```

(Replace ch,th with the layouts you need)

Then save this script somewhere, make it executable and add it to Autostart (System -> Preferences -> Sessions).

Since this little line 'setxkbmap -model pc105 -layout ch,th' fixes the problem till the next reboot, the whole problem is fixed by executing this line automatically after every LogIn :)

I should have been looking for a workaround from the beginning instead of trying to fix the problem ;)

---

