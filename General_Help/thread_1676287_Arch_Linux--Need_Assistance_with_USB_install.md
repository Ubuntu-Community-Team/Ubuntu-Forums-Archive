---
title: "Arch Linux--Need Assistance with USB install"
date: 2011-01-26
forum: General Help
---

### Post by jukingeo on 2011-01-26
Hello All,

I been an avid user of Ubuntu Linux since 2006 and I can't say enough how impressed I am with the community support here.  

I am currently working on a new project in which I would like to have a Linux based machine running arcade games (via SDLMame) in an arcade cabinet.    I am going to be using lower powered motherboards for this task and I wanted to use a lightweight, no gui Linux distribution.

Doing my research I found two choices came up often that would suit my task and that was Gentoo and Arch Linux.   Out of the two, it seemed like Arch would be the easier one to set up as one needs to be somewhat of an 'expert' to set up Gentoo.

Ok, so what I did is prepared an .iso install of the latest Arch Linux to a 4gb USB stick.   It would be from this USB stick that I would do a FULL INSTALL of Arch on to another 8gb USB stick.

I followed several instructions on how to do this and I get as far as installing everything to the 8gb memory stick and then it goes south from there.   Instead of bouncing me back to the installtion menu and the next option being "configure".   I get a message at the end of the install saying that "Package Installs Complete".   And there is a highlighted <CONTINUE> button on the bottom.   I hit enter when that comes up, and then the install hangs.   Pushing any keys just produces characters on the screen.   The only thing that works is a CTRL-ALT-DEL and that, of course, aborts the install and I have to do everything all over again.

Now, I don't know what I am doing wrong.   I have tried to look up the problem on the Arch Linux forums, but I didn't come across anything like the issue I am having.

Now I know that I should be posting this in their forum, but I was presented with something very odd when attempting to sign up there.

Here take a look...scroll down to the last question on the bottom:

[https://bbs.archlinux.org/register.php?action=register](https://bbs.archlinux.org/register.php?action=register)

What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?>

W T F is that?

I NEVER seen anything so obtuse on a registration page before.

I have heard that the support for Arch is less than stellar because they want everyone to do their own research themselves.   Well, what do you do when one is stumped?   And then they make a game of trying to sign up to their forums?


Well, the bottom line is this.  I am hoping that someone here has managed to get Arch working on a full install off a memory stick and could possibly lend a hand.   Otherwise, I am probably going to give Gentoo a try.   Hopefully their community forums aren't so obtuse to sign up for.

Thank You,

Geo

---

### Post by ender4 on 2011-01-27
I'm not sure but it might be that the Arch installer is busy installing packages, building the ram disk, or something else. Some of the steps take a really long time to complete, without any kind of notification.  That is if I remember correctly.  It's been over a month since I did an Arch install.

---

### Post by ellgor on 2011-01-27
Hi,

Just to reiterate on what ender4 says, I have puppylinux on a usb and it takes ages to load data to it, I did read that the transfer rate of a HDD is about 100Mb sec whereas a usb is at around 20Mb if your lucky. I do recall that when the installer got to copying files to the usb I went and made a cuppa, had it and made another and was still waiting.

Regards, Ellgor.

---

### Post by jukingeo on 2011-01-27
> **ellgor said:**
> Hi,

Just to reiterate on what ender4 says, I have puppylinux on a usb and it takes ages to load data to it, I did read that the transfer rate of a HDD is about 100Mb sec whereas a usb is at around 20Mb if your lucky. I do recall that when the installer got to copying files to the usb I went and made a cuppa, had it and made another and was still waiting.

Regards, Ellgor.

> **ender4 said:**
> I'm not sure but it might be that the Arch installer is busy installing packages, building the ram disk, or something else. Some of the steps take a really long time to complete, without any kind of notification.  That is if I remember correctly.  It's been over a month since I did an Arch install.

Do you by any chance recall a hangup at that point I mentioned?  Basically it seems like all the packages are loaded up at that point and then at the bottom of the page is a <CONTINUE> button.  I click on that, and nothing.  I do get a cursor at the bottom of the page and you can play around with it, but it seems that is where it stops.

I know that Arch is updated frequently and it does have a rolling release, but I am wondering if perhaps I should look for an older version to start off with.  Could be that it might be less temperamental.

The bottom line is that I just want something lightweight that could run MAME/Daphne.  I prefer something that I could set up and once set, it doesn't need a gui and I can set it to boot right into Wah!Cade, which would be my front end loader.

There was a suggestion to use Puppy Arcade, but I found that not to work out for me.  I don't care for the front end on that, and when I did install it I had no sound and the games ran VERY slowly.   So I figured I would stick with the Wah!Cade / SDLMame way to go.

But there are other reasons why I wanted to use a lightweight, gui-less distribution of Linux and that is for I/O control...or embedded system control.

Thanx for the quick response guys...that is one thing I could always count on here in the Ubuntu forums.   I am very dismayed at why the folks over at the arch forums have that archaic way of signing on to their forums.  It is like they don't *want* newbies.  Granted, I know I could count my losses and perhaps move on to Gentoo, but from what I read, that is even harder to set up than Arch.

Edit on Gentoo:

Doing some more reading on Gentoo, I don't think it is what I am looking for.  From what I read you have to compile everything on your own and it can take days to properly set up Gentoo.  The advantage is that, like with Arch, you have control of what is installed on your system.  The one thing nicer about Gentoo is that you can fine tune it to your system.   However, this is the same reason why I don't think it would be suitable for my needs.   Not only am I looking for a lightweight distribution, but I am also looking for one in which I could easily duplicate on other systems.   That would kind of rule out Gentoo right there.

Getting back to Arch, I did find some older versions floating around on the web and I figured I would give that a shot first.  If it works I could always update it later on.


Geo

---

### Post by jukingeo on 2011-01-27
> **ender4 said:**
> I'm not sure but it might be that the Arch installer is busy installing packages, building the ram disk, or something else. Some of the steps take a really long time to complete, without any kind of notification.  That is if I remember correctly.  It's been over a month since I did an Arch install.

> **ellgor said:**
> Hi,

Just to reiterate on what ender4 says, I have puppylinux on a usb and it takes ages to load data to it, I did read that the transfer rate of a HDD is about 100Mb sec whereas a usb is at around 20Mb if your lucky. I do recall that when the installer got to copying files to the usb I went and made a cuppa, had it and made another and was still waiting.

Regards, Ellgor.

Hello guys, I am back again after taking both of your advices and giving it one more shot.

Guess what?  It was exactly as you said.  When I came upon that continue screen, I just clicked on it and then I got the long pause (which I thought was a hang).   So I went off to do something else and sure enough when I came back, the page was gone and it was waiting for me to select the next phase of the installation menu!

So I was happy and overjoyed that I managed to get through the rest of the installation, but all my cries of joy came crashing down when I tried to boot up my new USB install of Arch Linux.   I got this nice fat error message:

root (HD2,0)

Filetype Unknown

root = /dev/disk/by-uuid 7255-07F9  filetype 0x7

Error 17:  Cannot mount selected partition.  

There was something on the Arch site about this and it said something about running chroot "at the prompt".  So when the grub menu came up, I put it into the prompt mode and tried chroot.  I got another error message.   Apparently you have to do this chroot from somewhere else. Needless to say, at this point I am lost at what to do next and would appreciate some more help.

Edit:

I did some more digging in regards to this situation and apparently it has to do something with grub and it seeing multiple hard drives upon installation of grub onto the boot partition of the USB memory stick.

Now I am wondering if I should have done the install from the CD-Rom (instead of another memory stick) and disconnected the computer's hard drives this way grub would have no choice but to see the one and only USB drive.

Anyway, I don't want to have to reinstall everything for the umpteenth time.   Any suggestions on how to fix this?

Thank You,

Geo

---

### Post by djeikyb on 2011-01-27
> **jukingeo said:**
> [https://bbs.archlinux.org/register.php?action=register](https://bbs.archlinux.org/register.php?action=register)

What is the output of "date -u +%W$(uname)|sha256sum|sed 's/\W//g'"?>

W T F is that?It's a command they want you to run at the terminal. Basically, it's a nerdy captcha.

---

### Post by jukingeo on 2011-01-27
> **djeikyb said:**
> It's a command they want you to run at the terminal. Basically, it's a nerdy captcha.


Intersting, however, running that in my Ubuntu terminal yeilds a big fat 

">"

Hmmmm...wait a minute...

SUDO date -u +%W$(uname)|sha256sum|sed 's/\W//g' yeilds:

e06135132a9bf3778b771cae11f072d7e59cf9d03494e9fb7113c84a1cbd8876

Let's try that....

Ladies and Gentleman we have a Bingo!

Thanx for the tip!  Now I can complete the registration.


BTW, I am wondering since you were astute enough to figure that out, would you happen to shed some light on my plight?

Thanx,

Geo

---

### Post by djeikyb on 2011-01-27
Haha, for now I'm stumped by your main problem. I may have time later to look at it a little longer. I just recognised the date command format, pipes, checksum program, and that they were asking for output and thought to myself, "maybe this is a command.."

---

### Post by jukingeo on 2011-01-27
> **djeikyb said:**
> Haha, for now I'm stumped by your main problem. I may have time later to look at it a little longer. I just recognised the date command format, pipes, checksum program, and that they were asking for output and thought to myself, "maybe this is a command.."

That was pretty good insight on your part.  Something I didn't think of.   However, there was another trick to the puzzle and that was you need to be in super user mode in order to pull the command off.  Still it is a really obnoxious way to get attention from newbies wanting to sign up.

At any rate, getting back to my problem.  I was playing around with editing the values for the root (hd x,x) parameter in the grub menu.  Knowing that (hd 0,0) is my first hard drive first partition (My Windows Drive), I worked from there.

I have two Sata drives on my machine and during installation I added two usb memory sticks.

The Arch installation labeled the disks as follows:

sda -- The boot hard drive (for Windows and Ubuntu)
sdb -- The data hard drive
sdc -- The USB stick where I installed Arch To
sdd -- The USB stick where the Arch installation iso was located on.

Now changing this around to the nomenclature that Grub uses I figured the drives to be seen as follows:

(HD 0,0) -- The boot hard drive (for Windows and Ubuntu)
(HD 1,0) -- The data hard drive
(HD 2,0) -- The USB stick where I installed Arch To
(HD 3,0) -- The USB stick where the Arch installation iso was located on. (but I usually pull this one out after the install).

Ok, so I am homing in on HD 2,0.  

At first look it would seem that this is the problem because partition 0 is the boot partition NOT The root partition.  Grub seems to be looking for the root, correct?

So I ended up changing that "0" value and trying 1,2, & 3 which represent the 4 total partitions I have on that USB drive.   I figured I would 'hit' the correct one and the USB would boot Arch Linux, however, that didn't happen.

So as of now I am at a major loss at what to do next.  I will say that I have been working 3 days and about 12 hours total on this problem...I am ready to give up trying to get Arch to run from a USB.

Anything anyone else could think of I would appreciate.

Thank You,

Geo

---

