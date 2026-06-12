---
title: "Help setting up Ubuntu for my 62 year old mother"
date: 2009-10-20
forum: General Help
---

### Post by s1mp13m4n on 2009-10-20
Hello everyone.  I am a day in day out Ubuntu user.  I am not a hard core Linux user yet.  My mothers WinXP box got messed up pretty bad, so I decided to install Ubuntu 9.04, I did not have a legal WinXP license for it anyway.  My mother is an Internet surfer, facebook, pogo, gmail, types a paper or two or a resume for her husband.  What software should I install beyond the default Ubuntu install for her?  I was thinking VLC and Wine for starters.  
The house printer was connected to that now non-existant WinXP machine.  It is a HP Officejet J4550 all in one.  I want the printer to still be on that machine and available over the network for my Ubuntu 9.04 machine and my wife's WinXP netbook.  She is a nursing student and needs printer access from her netbook.  Thank you for the help.

---

### Post by howefield on 2009-10-20
> **s1mp13m4n said:**
> My mother is an Internet surfer, facebook, pogo, gmail, types a paper or two or a resume for her husband.  What software should I install beyond the default Ubuntu install for her?

The default install will take care of that for you along with a flash install for pogo.

You probably want multimedia codecs as well, ubuntu-restricted-extras

---

### Post by undecim on 2009-10-20
Definitely WINE, and the ubuntu-restricted-extras package. In a terminal, run
```
sudo aptitude install wine ubuntu-restricted-extras
```

For wine, you should add the winehq repositories as per the instructions from [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb). The command line instructions at the bottom of the page are probably the quickest and least painful ways. Below is a command that should set it all up when run from a terminal:
```
*wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -; **sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/$(lsb_release -cs).list -O /etc/apt/sources.list.d/winehq.list*
```

Also set up automatic updates (System -> Administration -> Software Sources; Updates Tab)

Maybe also change the fonts to be larger if she wears glasses or has vision problems (System -> Preferences -> Appearance; Fonts Tab)

---

### Post by s1mp13m4n on 2009-10-20
Thank you very much.  Pogo is no longer using flash but rather java plugin, so I am looking in to that as well.  When I installed Ubuntu I used F5 and selected high contrast which seems to have given a decent setup right out of the box for seeing things.  Thanks for the help and keep it coming.  :)

---

### Post by philinux on 2009-10-20
Open office is installed by default so no worries there.

gmail I think can be setup in thunderbird, needs installing or evolution, already installed by default.

Just share the printer. Dialog within system >admin>printing.

---

### Post by howefield on 2009-10-20
> **s1mp13m4n said:**
> Thank you very much.  Pogo is no longer using flash but rather java plugin, so I am looking in to that as well.

Sorry about that, I loaded pogo up to see what it was, and assumed it was flash. In any event, ubuntu-restricted-extras will take care of java as well.

If I were installing for someone else, some of the stuff I'd put on are msttcorefonts, xchat, compiz settings manager, emerald, cups-pdf, vlc, realplayer, samba, wine, miro, dropbox, skype and virtualbox.

Also, your printer should be fine and will network from your Ubuntu machine without issue.

---

### Post by s1mp13m4n on 2009-10-20
Thank you all for the great help.  Would you install dropbox or Ubuntu one?  I have her Ubuntu system updates set up to download and install without comfirmation to make it easier on her to use.  I am trying to make the machine "just work" so she can just use it and it will somewhat take care of the stuff she does not need to know about.  :)  I also did not know pogo did not use flash so I was in the same boat with you.

---

### Post by iTheBadGuy on 2009-10-20
> **s1mp13m4n said:**
> ... I am trying to make the machine "just work" ...
I think that won't be a problem :D

---

### Post by howefield on 2009-10-20
> **s1mp13m4n said:**
> Would you install dropbox or Ubuntu one?

For me, Ubuntu One has a few issues and is restricted to Ubuntu computers (8.10 onwards, I think) Dropbox has the edge with being cross platform and the fact it works for me.

I want to use Ubuntu One and most likely will once it does what I want it to do. Your mileage may vary of course.

---

### Post by s1mp13m4n on 2009-10-20
OK, I have taken all your great advice and I have this machine setup so far.  I have her data recovered from the WinXP crash and placed on this new Ubuntu install (pics, docs, etc) and have dropbox installed and that recovered data on dropbox.  I think she is set.  I just wanted to get the maching working so when I hook it up for her she can simply use it and it is ready to go.  Thank you for all the great help.  :)  I love Linux.

---

### Post by Mark Phelps on 2009-10-20
A really good way to frustrate ANYONE is to install apps they're used to running only to then have one or more features not work because the emulation is not 100%. All too often, folks see Wine as a magical cure to running MS Windows in Linux -- which it is NOT.

I spent six months experimenting with using "productivity" apps in Wine, and in all that time, NOT ONE exhibited useful levels of functionality.  In every case, one or more key features either didn't work, or worked in a different way from what was expected.

Personally, I would avoid Wine altogether. If, by some chance, you check with the WinHQ App Compatibility DB site and find out that ALL the MS Windows apps you want to run are rated Platinum or Gold, maybe then, Wine would be an OK idea.

If your mother needs MS Windows apps so much that you need Wine, you would do better showing her how to use a Linux alternative to do the same work.

---

### Post by P4man on 2009-10-20
Seems like no one mentioned the most important one: a way for you to **remotely access **the machine if she runs in to trouble. Depending on your preferences / experience configure remote desktop, ssh and/or FeeNX. Set up the router if needed, and if she is on a dynamic IP something like no-ip.org.

---

### Post by ram2500 on 2009-10-20
Wine isn't terribly bad, unless you are running it on a 486:P or using a resource-intensive application (even on a dual-core machine). simpleman (sorry, I couldn't remember the numbers in your screen name), what is your mother's computer specs? What specific Windows programs does she want to use?

---

### Post by s1mp13m4n on 2009-10-20
The system specs are:

Celeron 2.66
733.3MB RAM
40GB hard drive
cd rom
cdrw
shared video
intergrated audio and network

90% of what she does is Internet surfing/gaming
the rest might be games like Alice Greenfingers

The WIN XP machine that was messed up had Open Office on it and firefox and VLC

I know Wine will not be perfect but it is worth a shot.  :)

---

### Post by mike555 on 2009-10-20
That's an older machine and probably wont show special effects , but should run Ubuntu just fine ...... I also recommend Firefox add-ons;  ad-block plus, WOT , Xmarks (to save bookmarks online).

---

### Post by Roasted on 2009-10-20
> **P4man said:**
> Seems like no one mentioned the most important one: a way for you to **remotely access **the machine if she runs in to trouble. Depending on your preferences / experience configure remote desktop, ssh and/or FeeNX. Set up the router if needed, and if she is on a dynamic IP something like no-ip.org.

I'd like to expand on this question for the sake of learning this myself and the fact I think it's a VERY good thing to install on a grandma-approved Ubuntu machine. How exactly would you set this up? I use VNC all of the time but only on actual LANs and not across LANs.

If the grandson in question needs to remote in to grandma's computer, what does he need to do to their network to accomplish this?

Static IP the grandma computer?
Forward that IP through a certain port?

---

### Post by tlois on 2009-10-20
One piece of advice I'll give here.  Set up Open Office to always save as docs so that if she emails attachments to people they can open it.  Have set that up for my parents too.

---

### Post by CRAY-4 on 2009-10-20
gimp is the best

---

### Post by s1mp13m4n on 2009-10-20
Thank you all for the help.  It went well and the computer is up and running and to be honest the entire process was easier than Windows.  I did not have to go locate drivers for anything.  It simply worked.  Thanks again.

---

