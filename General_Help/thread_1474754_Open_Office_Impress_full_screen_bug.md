---
title: "Open Office Impress full screen bug?"
date: 2010-05-06
forum: General Help
---

### Post by bubblehead74 on 2010-05-06
I was testing Open Office, whether I can use it for professional purposes, and I could not get the slide show to be completely full screen. Both horizontal Gnome bars remained on the screen. Can anybody reproduce this on 10.04?

---

### Post by Warthaug on 2010-05-06
I am experiencing the exact same thing.  To make matters especially irritating, the bars are actually overlying the presentation, rather than the presentation being scaled inside of the bars.

---

### Post by bubblehead74 on 2010-05-06
Then it is a bug indeed. Wow. Don't take me wrong, but I thought OO would be better. I mean the primary purpose of Impress is to give presentations... and it is broken?

---

### Post by bubblehead74 on 2010-05-06
OK. I found the corresponding bug report pages. It seems that disabling Compiz, which is useless in professional environment anyway, should fix this.

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/525807)

[http://qa.openoffice.org/issues/show_bug.cgi?id=110881](http://qa.openoffice.org/issues/show_bug.cgi?id=110881)

---

### Post by Warthaug on 2010-05-07
> **bubblehead74 said:**
> OK. I found the corresponding bug report pages. It seems that disabling Compiz, which is useless in professional environment anyway, should fix this.

Whoa, you callin me unprofessional...

...OK, maybe that's not too far from the truth.

Bryan

---

### Post by Warthaug on 2010-05-07
> **bubblehead74 said:**
> Then it is a bug indeed. Wow. Don't take me wrong, but I thought OO would be better.

Impress has always been the weakest part of OO.  We all hope for improvements, but they've been slow in coming.

I use virtualized WinXP and powerpoint for anytime I need to do a fancy presentation and for teaching.  OO of for quicky presentations only.

Bryan

---

### Post by bubblehead74 on 2010-05-07
> **Warthaug said:**
> Whoa, you callin me unprofessional...

You know bosses. They want to know what progress I made in the lab and not whether my windows can burst in flames. BTW, I did not mean to say that Compiz is useless. Only that I don't need it in work. Also, the full screen bug is not a Compiz bug; it is an OO bug. Disabling Compiz is just a workaround, while this mess will get fixed (if at all).

---

### Post by SeQueNceR on 2010-05-10
Hey friends. i din't find a total solution for this. but i've a small workaround. i've shown (hide buttons) on the panel. so that i can hide it with a click (right click panel --> properties --> show hide buttons) , i'm hiding the panel when i'm doing a presentation

i'm searching for a solution. i'll post it when i found it ;):guitar:

---

### Post by bubblehead74 on 2010-05-10
The workaround is to disable Compiz, or install Lotus Symphony 3:

[http://symphony.lotus.com/software/lotus/symphony/SymphonyBetaHome.nsf/home](http://symphony.lotus.com/software/lotus/symphony/SymphonyBetaHome.nsf/home)

---

### Post by flipper9 on 2010-05-10
This bug was reported during the beta and is still not fixed.  I think the developers don't see it as a bug, or people are blaming the other developer for the problem.  This really needs to be fixed as it, frankly, makes Lucid look really bad when you fire-up a powerpoint and it looks like crap.  And turning off Compiz and hiding toolbars is really not a "fix", but a kludge...not a "work-around" as that doesn't fix anything.

---

### Post by lancest on 2010-05-14
It's pretty simple to enable/disable autohide in the panel properties during a presentation. (right click)

This is just one of the three minor problems I have related to Compiz. A bit disapointed.
(Titlebar missing, fullscreen flash, OO present fs)

---

### Post by mdbarton on 2010-05-16
Same issue here.  However I've now also installed KDE (Kubuntu) so I have a choice of desktops - and impress works full screen no problem - not sure if KDE uses compiz, the effects are flashy enough anyway

---

### Post by ashwinhgtx on 2010-05-16
Even I have the same problem on 10.04 with Compiz enabled. I guess it'll work in KDE as it uses Kwin instead of Compiz. Is there no fix available other than disabling Compiz?

---

### Post by flipper9 on 2010-05-16
The only answers I've seen...
1. Disable compiz, who needs that anyways?
2. Manually hide the toolbars. It's not that hard to have a few extra steps...right?
3. Use Microsoft Powerpoint viewer in Wine, because well we won't fix the problem.
4. Use another office package.
5. Live with it.
6. Install a build of open office from some other PPA, somewhere.  Might uninstall Ubuntu Software Center if you try to uninstall the OO that came with Lucid, according to another unrelated bug report and forum post.

On the bug reports...
1. It's Open Office's fault
2. It's compiz's fault
3. It's gnome's fault
4. It's somebody else's fault
(kinda reminds me of a recent congressional hearing, lol)

---

### Post by ashwinhgtx on 2010-05-16
> **flipper9 said:**
> The only answers I've seen...
1. Disable compiz, who needs that anyways?
2. Manually hide the toolbars. It's not that hard to have a few extra steps...right?
3. Use Microsoft Powerpoint viewer in Wine, because well we won't fix the problem.
4. Use another office package.
5. Live with it.
6. Install a build of open office from some other PPA, somewhere.  Might uninstall Ubuntu Software Center if you try to uninstall the OO that came with Lucid, according to another unrelated bug report and forum post.

On the bug reports...
1. It's Open Office's fault
2. It's compiz's fault
3. It's gnome's fault
4. It's somebody else's fault
(kinda reminds me of a recent congressional hearing, lol)


I guess we're officially all politicians now. :P

---

### Post by Gonzalo_VC on 2010-05-27
> **bubblehead74 said:**
> I was testing Open Office, whether I can use it for professional purposes, and I could not get the slide show to be completely full screen. Both horizontal Gnome bars remained on the screen. Can anybody reproduce this on 10.04?

[COLOR="Navy"]It's happening with OOo 3.2 and 3.1, in Ubuntu 8.04, 9.10 and 10.04.
And I don't think disabling compiz is a good solution! OK, just  for now, but somebody please solve this ;-)
[_I read that_]("http://qa.openoffice.org/issues/show_bug.cgi?id=110881") "*A Compiz developer mentioned that this was because OOo does not use the _NET_WM_STATE_FULLSCREEN property and the hack to make OOo draw fullscreen anyway that compiz used to implement they have dropped due to it causing problems with other applications*." [-X[/COLOR]

---

### Post by ashwinhgtx on 2010-05-28
Any progress in fixing this bug?

---

### Post by Hagar Delest on 2010-05-29
it seems to work fine with the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by vanadium on 2010-05-31
Problem for me with the Sun version (now Oracle) is that it does not work with Bibus on Ubuntu (unless that has been fixed in the mean time).

---

### Post by tolgainci on 2010-07-25
Hello,

I had already posted this problem in an old thread below with the same symptoms, but perhaps it's more suitable here:
[http://ubuntuforums.org/showthread.php?t=785404](http://ubuntuforums.org/showthread.php?t=785404)

> **tolgainci said:**
> Hello Everyone,

I have the same problem, and openoffice.org-gnome and openoffice.org-gtk  are installed. The only workaround for me is to disable compiz before  starting a slide show. This is actually not so great, because I really  would like to flip my desktop to a Windows installation on Virtualbox  using Desktop Cube. I typically make presentations about Windows  software at work, and I make a quick demo during the presentation by  changing to a different desktop. When desktop effects are disabled, this  doesn't look too cool, and you can imagine that my objective is to draw  audience attention and impress people with my presentation :)

To put it in a few words, Openoffice.org Impress without Compiz is NOT  IMPRESSIVE for me. I'm also not too impressed about the Ubuntu Software  Center, which apparently still distributes compiz+openoffice.org with  this major bug. 

If anybody has a solution that works when Compiz is still enabled, I will be very glad to hear it. 

Best Regards,

Tolga

Some comments on older posts in this thread:

**[bubblehead74]("http://ubuntuforums.org/member.php?u=810873"):** First of all, thank you for starting this thread. I'm a marketing professional and I actually need compiz for professional purposes. I need all the shiney, polishy look I can get, be that the firey mouse pointer, rotating desktops, wobbly windows etc. during a presentation.
[B]
[Warthaug]("http://ubuntuforums.org/member.php?u=177735")[/B] **:** It's really frustrating to hear that you have to use Powerpoint when you need to do something "serious". Nowadays, I only fire up windows in a vbox, since 90% of my customers still use it, and I need to provide support and services to them. Unfortunately running virtual Windows with Powerpoint on top of it, can be problematic. (font, multimedia and performance problems) And if I should run native Windows just to make a proper presentation, why would I switch to Ubuntu in the first place?

**[SeQueNceR]("http://ubuntuforums.org/member.php?u=891435"): **The first thing I tried was hiding the panels, but there still remains a line both above and below. Also the panels show up if you accidentally approach the top or bottom with your mouse pointer. During the presentation you look like an idiot who can't even run his PC, which is not a very good first IMPRESSion :)

**[Hagar de l'Est]("http://ubuntuforums.org/member.php?u=212513"):** Your suggesstion seems to be the best workaround, I will try installing OOO from Oracle's site. However this might be too difficult for the average user and goes against Ubuntu's simplicity and user-friendliness motto.

**[flipper9]("http://ubuntuforums.org/member.php?u=822657"): **You have the problem spot on! This is actually not a technical problem, it's a project management pitfall :) 

I beleive Ubuntu developers should step in and somehow fix this issue, as it's bad publicity for the OS itself. The bug may be within Compiz or Openoffice; however, it's Canonical who provides this distro, and it's advertised (quite rightly) as being everything and more than MS stuff for the average user. Perhaps special OOO builds can be compiled without this bug, or another Window Manager or Office package can be set as default, so that at least people will have a presentation tool that works as expected out-of-the-box.


Best Regards,

Tolga

p.s. I just reinstalled Ubuntu 10.04 LTS from the CD, installed all the updates and the problem remains the same.

---

### Post by Hagar Delest on 2010-07-26
> **tolgainci said:**
> I will try installing OOO from Oracle's site. However this might be too difficult for the average user and goes against Ubuntu's simplicity and user-friendliness motto.
Don't worry, there are just a couple of command lines, it will show you how easy it is. It's also quicker, especially with following installations when the command lines are still in the shell history.

---

### Post by lancest on 2010-07-26
Got 3.2.1 installed (Looks real nice).
However no full screen with Impress

---

### Post by Hagar Delest on 2010-07-26
Even with Compiz off?

It works fine for me but I use xubuntu.

---

### Post by lancest on 2010-07-26
With Compiz off it's full screen.
This bug won't shake my faith in Ubuntu. 
But I hope it gets fixed by 10.10

---

### Post by Gonzalo_VC on 2010-07-26
> **lancest said:**
> With Compiz off it's full screen.
This bug won't shake my faith in Ubuntu. 
But I hope it gets fixed by 10.10

[COLOR="Navy"]I think it is not Ubuntu's "fault"... it's a problem between Compiz, Gnome and OpenOffice.org ;)
[/COLOR]

---

### Post by tolgainci on 2010-07-27
[COLOR=Blue]Here's my workaround for Ubuntu 10.04 that will keep me happy until this issue is fixed:[/COLOR]
[B]
1.[/B] Open Ubuntu Software Center and install "Kubuntu Plasma Desktop System" (kubuntu-desktop)
**2.** Log out, and choose "KDE" from the options below before logging back in. 

That's basically it! Since KDE doesn't have the "Impress Full Screen Bug", you can do full screen presentations with full desktop effects enabled. I can switch to other desktops by Desktop Cube effects, use mouse trailing to highlights things in red etc. When I switch back, the presentation is still in full screen as expected :) I normally work in GNOME, I will just use KDE when I need to make presentations. Since it's just a GUI change, all of my documents, applications etc. are still available for use during the presentation.

I actually liked having KDE as well, since the default KDE applications are also visible and mostly usable in GNOME. Perhaps some might find this annoying, but you can always remove them from your menus if you like.

[COLOR=Blue]I had a few minor bugs after installing KDE alongside GNOME, here are the fixes:[/COLOR]

**1.** KDE default mouse pointer Oxygen is fixed in GNOME and can't be changed:
**FIX: **Uninstall oxygen-cursor-theme using Synaptic Package Manager.

**2.** Fonts look funny in Firefox in GNOME.
**FIX:** Type the following in a terminal, replace USERNAME with your UBUNTU username.
> sudo gedit /home/USERNAME/.fonts.conf
Delete the contents, paste the below text into the file. Save the file, log off, log back in.
> <?xml version='1.0' ?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target='font'>
<edit name='autohint' mode='assign'>
<bool>true</bool>
</edit>
</match>
</fontconfig>**3.** Boot screen displays Kubuntu logo.
**FIX: **Uninstall plymouth-theme-kubuntu-logo using Synaptic Package Manager.

I hope that helps people with the same problem.

Best Regards,

Tolga


p.s. It seems it's GNOME's fault after all :P

---

### Post by SabreWolfy on 2010-08-17
Installing KDE/Kubuntu as a workaround to a Compiz/GNOME/Ubuntu bug? No, I don't think so :)

I read that enabling Compiz|Workarounds|Legacy Full Screen should solve this, but it hasn't on my OOo 3.2 Lucid Ubuntu system.

---

### Post by Gonzalo_VC on 2010-08-17
> **SabreWolfy said:**
> Installing KDE/Kubuntu as a workaround to a Compiz/GNOME/Ubuntu bug? No, I don't think so :)

I read that enabling Compiz|Workarounds|Legacy Full Screen should solve this, but it hasn't on my OOo 3.2 Lucid Ubuntu system.

[COLOR="Navy"]I agree. KDE is great, but it MUST be another way, *i.e*: Gnome and Oracle must solve this issue :!:
[/COLOR]

---

### Post by xpace on 2010-08-20
searching for a solution to this bug and bump into this thread.

My workaround for this is to enter the presentation mode when a tooltip is being displayed, more elegantly done by clicking the presentation button in the toolbar.

I use KDE with compiz as window manager, hope it works with Gnome too.

---

### Post by mikitz on 2010-09-16
This is major issue for those of us who rely on OpenOffice Impress as part of our job. Parts of all slides are obscured by the bottom of the screen.The bottom portion of every single slide is obscured by the task bar. I am surprised this has been an issue since the release of Lucid and STILL hasn't been fixed ...

---

### Post by SabreWolfy on 2010-09-16
Bug report [here]("https://bugs.launchpad.net/bugs/525807"). Patched in upcoming 3.3 beta according to comment #82 there.

---

### Post by RedSingularity on 2010-09-28
Fix yet?

EDIT:  Nevermind, I see it.

---

### Post by mdbarton on 2011-01-29
Installed LibreOffice.  This now works fine.

---

### Post by lancest on 2011-01-29
LibreOffice is great for me at 3.3.    
Lets home the days of ongoing bugs like this are over. 
 (I had seen that full screen bug pop up in several past versions)

---

### Post by Gonzalo_VC on 2011-01-30
> **mdbarton said:**
> Installed LibreOffice.  This now works fine.

It was about time! ;)

---

