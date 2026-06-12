---
title: "MAME and OWNER problems."
date: 2011-06-28
forum: General Help
---

### Post by exinfernis on 2011-06-28
Hello people !
I just recently installed 10.04 on a hp nx7010, and after some older tries with linux, I can easily say that 10.10 (upgraded from 10.04 and then reinstalled fresh) is really ... really awesome. Great work.I'm  not new to computers but there's a saying: We live to learn... :)

There are 3 kinds of users on the laptop:wifey,kids and ...me. I have installed WINE to tryout MAME32 and I keep getting ownership problems... same with gmameui. Mame folder was copied from older windows hard drive (I've had my share of clonezilla hours...:))

I've managed to run it through WINE while logged in as root in the gui but cant seem to understand if I should copy the folder to the other profiles as well and then play with permissions and owners again. Keep getting .wine - owner problems...

As I am actually eager to make the turn to open source and specifically linux distros, I really have to catch up to unix again (old SCO openserver user).

P.S. I am really trying to switch my whole family's attitude towards linux.

Regards.

---

### Post by An Sanct on 2011-06-28
Welcome to the forums!

hm ... is there any special reason why you use windows software, that also has a port for linux?

I'm aiming towards [xmame]("http://linux.softpedia.com/get/System/Emulators/Xmame-4096.shtml") and [mamegui?]("http://gmameui.sourceforge.net/")

Take a peak at [this page]("http://www.danielandrade.net/2008/01/08/running-mame-games-on-ubuntu/") too ;)

---

### Post by exinfernis on 2011-06-28
Well, there is no specific reasoning behind it ... :|.Mame is my sons best use for the laptop, my daughter ... too young..., my wife wants facebook and such, and last but not least I want the full package :) . I like to experiment. I write simple scripts most of the time but at the moment I want to make them believe !!!. I have always believed in linux and one of the first tries I made for the switch was Lindows. Then Mandrake, Suse, Slack and now Ubuntu.

I really like this 10.10 distro. If I make it to be a clean replacement for our main PC with 7 on it, well it will be nice. Still though, most games are made for Windoz so I might just keep a dual boot on the PC when I re-install it.The laptop ... I want it on Ubuntu . 

Will look into those links right now. Thx for the prompt reply!

---

### Post by mcduck on 2011-06-28
> Mame folder was copied from older windows hard drive
There's probably your problem. Windows doesn't use file/direcory ownerships and permissions like Linux/Unix systems do, so the permissions pf files copied from windows are most likely wrong.

Make sure the mame directory is owned by your user, and that your user has read & write permissions there.

(also +1 for a native Linux version instead of running a Windows version through Wine. :))

---

### Post by exinfernis on 2011-06-28
Then I should have to copy the roms folder to each user profile home folder? Redundant isn'it? The one time that gmameui run and successfully loaded a rom, I had to chown the whole tree (mame files) using the root acount, within the kids account. If I had to run gmameui again but from my own account, should I copy it to my home as well? Or maybe put the files in some shared folder under /usr/share and point the links to it? Right now I 'm getting owner errors running it from my account while it sits on my desktop...

It seems as there is some king of conflict going on, as the gui starts to load the rom file but crashes either completely or just back to the main screen of gmamegui . I know I;m doing something wrong... :(

---

### Post by exinfernis on 2011-06-28
Info: Using gmameui now and not wine... still the same...:(

---

### Post by An Sanct on 2011-06-28
Well, I would move the roms to a *neutral* location, not the home folder of any person, that is totally redundant, besides, if you download another game, you would have to copy to all locations (or create symlinks ... again, redundant).

(1) I have a secondary disk for music, movies and other shared stuff, if you can put the roms in a location like that, that is the way to go

-alternatively-

(2) You can put them into '/usr/mame' or '/media/shared/mame' (create the folder) and make 'root' the owner, then make sure, everybody can read/write/modify/delete - in short give full access to the whole folder to everybody.

+make the new folder "[sticky]("http://en.wikipedia.org/wiki/Sticky_bit")", this means, that all files, that will be put inside will inherit the folders access settings. (I don't know how to do this from terminal, I use crusader for this)

-alternatively-

(3) You could create an user group, join everyone into that group and then do the above (nr.2) and make the group the owner of the folder, this way everyone will be able to modify its contents...

---

### Post by exinfernis on 2011-06-29
Well, I'm a bit absorbed with other aspects of Maverick and I am forced to postpone my MAME investigation.... Currently trying out Xpud and Slax for a really old machine and thinking of switching my windows torrent box into ubuntu..:) . Plus modifying my main PC for dual booting (pita I know).

I will look into Mame again sometime this week...

...drooling over Ubuntu... I have seen the light...:)

Sticking with Ubuntu for the time being exploring and trying it, and then I will see about games...

---

