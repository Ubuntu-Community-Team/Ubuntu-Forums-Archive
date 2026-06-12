---
title: "Is Dapper really ready?"
date: 2006-05-27
forum: General Help
---

### Post by christian.convey on 2006-05-27
Hi guys,

On two out of two computers, my upgrade from Breezy to Dapper's RC (release candidate_resulted network interfaces that no longer worked and that I couldn't repair.

Is Dapper generally unready for release, or am I just especially unlucky for some reason?  From my experiences with it, it still seems way below the quality goals that the community and Mark have for it.

Am I the only one with this experience?

- Christian

---

### Post by Melvil on 2006-05-27
Have you tried doing a reinstall instead of an upgrade? That's the only way to really track down any issues.

---

### Post by christian.convey on 2006-05-27
For each computer, the first thing I tried is an upgrade, which introduced the network problems.

On my work computer, after experiencing this, I did a clean install of Breezy.  Then I immediately did an upgrade to Dapper RC, and still had the network problems.

At work I don't have a CD writer, so I couldn't easily to a clean install right from the Dapper install CD.  That's the next thing I'm going to try at home.

But still, a failed upgrade on 2 out of 2 computers?  It just seems to me like we should work this out a bit more before Mark spends a lot of $$$ burning the ShipIt CDs.

---

### Post by apollyonis on 2006-05-27
My experience has been that the upgrade through update manager resulted in catastrophic events - it got about 95% of the way through about 15,000 packages and then took a nosedive. I had install it through the Live CD - now its working fine.

---

### Post by Minyaliel on 2006-05-27
I had no problems... but then, I wanted to test the live CD, so I used that...

---

### Post by KingArthur10 on 2006-05-27
I only installed using a clean install.  Worked great.  Upgrades are notoriously ugly.

---

### Post by Phreaker on 2006-05-27
Just installed Dapper from the Livecd.
No problems .And it's faster than FC5.
No bugs found yet

---

### Post by Sef on 2006-05-27
Best way to install Dapper is with a clean install (reinstall via a CD.)

2nd best way is sudo apt-get update then sudo apt-get dist-upgrade

Other ways are best avoided.

---

### Post by milehigh on 2006-05-27
I installed beta and have been upgrading daily with very few problems. Networking was slow, but easily fixed by disabling "ivp6". My biggest issue was printing. I eventually found the driver, converted it from .rpm to .deb and installed it thanks to these excellent forums, user guides and a post at [http://www.finebushpeople.net/](http://www.finebushpeople.net/) 

I think installing the release candidate is worth a try if you can get a disc.

---

### Post by mannheim on 2006-05-27
For upgrading from Breezy to Dapper, there are instructions on the [RC page.]("http://www.ubuntu.com/testing/dapperrc")

In brief: (1) make sure you have the new version of the **breezy** update manager; then (2) gksudo "update-manager -d".

Does anybody know if this supposed to be less failure-prone than doing things by hand (editing sources.list then doing the usual apt-get update, apt-get dist-updgrade)?

---

### Post by sean on 2006-05-27
My experience is that cupsys printing is still seriously broken.  I have a team of 15 software engineering developers who use Breezy as their desktop and in my evaluation of Dapper suitability has seen serious problems on both a clean install and an upgrade.

Sean

---

### Post by dada1958 on 2006-05-27
Today I installed Dapper Drake RC on that old Celeron @ 333 MHz on my work. Unfortunately the installer is still crashing, it cost me 3 attempts before the actual installation started. Partitioning the HD is still tricky.
But for the rest Dapper Drake is way faster than Breezy on this machine.
But an installer shouldn't crash...

---

### Post by isotonic on 2006-05-27
i've done an upgrade and everything seems fine - no problems downloading and updating, on one machine everything is working and on the other i'm having nvidia issues i'm dealing with now.

just thought i'd put in a good word for the update manager...:p

---

### Post by dglock on 2006-05-27
I installed kbuntu rc on this comp using the live cd, this is the first version that did not crash at the partition page.
 
  I am not a fan of upgrading, i much prefer to backup any critical data and do a full install. 

  don

---

### Post by ejos on 2006-05-27
"Is Dapper really ready?"
I was just thinking this and noticed this thread when I went to post about it. Has anyone looked at the launchpad bugs yet? There are way too many bugs to be releasing this, many of them are classified confirmed major bugs. I also think KDE needs more loving, things can get messed up on it pretty quick. I honestly think if this is going to be an LTS release that it should be delayed again. If someone has a major problem with ubuntu which is not unlikely, they will remember it. The goal of this LTS is to gain support for ubuntu with an up-to-date *and* stable release. It would be much more effective if these major bugs were fixed. Now I don't know whether or not it's realistic for the team to fix these bugs within the June 1st timeframe, but if it isn't there should be another delay. Push it back.

---

### Post by Horizon on 2006-05-27
I think for the major release dapper is supposed to be they shouldn't even give people the option to do an upgrade and force everyone to fresh install (or at least urge people to fresh install). I'm not really a fan of upgrading either and i think it just creates problems. I guess forcing people to fresh install a desktop OS isn't really practical until they get some decent custom-ubuntu backup software :-k

---

### Post by adamkane on 2006-05-27
No, it isn't ready.

My Gnome desktop panels blink non-stop. I've been using KDE for the past two months.

---

### Post by az on 2006-05-27
[QUOTE=christian.convey]For each computer, the first thing I tried is an upgrade, which introduced the network problems.
[/QUOTE]

Maybe due to the fact that ndiswrapper is no longer needed for a bunch of wireless cards?   If you keep trying to use ndiswrapper with them, they conflict with the native linux driver.


What kind of network problems?

---

### Post by Sef on 2006-05-27
> I was just thinking this and noticed this thread when I went to post about it. Has anyone looked at the launchpad bugs yet? There are way too many bugs to be releasing this, many of them are classified confirmed major bugs.

Dapper is ready.  Bugs are part of software.  Getting rid of them takes time.  If there were to be no bugs before a release then it would always be a beta.

---

### Post by silvagroup on 2006-05-27
Bugs are part of software, it's the nature of the beast. Anyone remember bugs in Windows. That's not as much a concern as upgrading. I think that if Ubuntus object is to be a user friendly desktop for the average user  we need to remember that they will not be performing system backups regularly, yet have data that is important. If you get into the mind set that you can just do a fresh install and reinstall your programs and reinstall your data you will also loose a large majority of the current user base, and possibly many new users which have switched over from Windows and Mac, and many more possible ones. The average user doesn't want to learn system administration and program, they just want to use the computer, it does what it's suppose which is to (in theory) make their life a little easier. Update/Upgrade tools need to work and need to work right the first time.](*,)

---

### Post by pecanov on 2006-05-27
[QUOTE=Sef]Dapper is ready.  Bugs are part of software.  Getting rid of them takes time.  If there were to be no bugs before a release then it would always be a beta.[/QUOTE]

I think everyone would agree that there is a limit of bugs that could prospone a release of any piece of software.

Dapper dramatically fails to meet it's expectations since it is long being promoted as a very stable release, the most stable one in years before and years to come. Yet I bet the "edgy" will have less bugs and annoyances than dapper itself. 
This is sad for every ubuntu user, but we just have to admit it, and in future help more to achieve a better ubuntu.

Denial won't help at all.

---

### Post by Lovechild on 2006-05-27
I tried Dapper the other day and about 50% of the programs I tried I was able to find a severe bug in, I try to make software fail because users will hit those scenerios in real life. It's a hobby, some people collect stamps, I break software. I was even able to make the installer misbehave.

I have no earthly idea how they plan to support this for 5 years, I'm really scared that they are getting in over their heads with the longterm support promise. Dapper is nowhere near ready for that kind of deployment. The problem for my money isn't that Canonical might be loosing money on this, but that they make GNU/Linux look bad by claiming that 6.06 LTS is suitable for massive deployment. 

My objective evaluation is that Dapper isn't ready for release and especially not for the LTS plan, the dapper development cycle has been rapid development not aimed at stability nor security. If you plan to release something with this level of support you can't go introducing tons and tons of new unvetted and unreviewed code.

If Dapper is to be supported for 5 years following release, I'd bet we'd need another 12 months of pure stresstesting and bugfixing with absolutely no introduction of new code. This kind of dedication to quality assurance is why products like RHEL are so succesful.

What is acceptable on your desktop is not the same as what is acceptable on a corporate desktop which has to be stable and secure for long periods of time with minimal administration.

Dapper falls short of the target, I'm sorry - please don't release it I beg you to not make GNU/Linux look bad.

---

### Post by David Valentine on 2006-05-28
For what it's worth, I went through the recommended upgrade procedure and hit only one hiccup--I had to chmod the permissions to 644 on /etc/apt/sources.list to get rid of an error in the upgrade manager.  Everything seems to work fine so far.

---

### Post by sharkboy on 2006-05-28
[QUOTE=Lovechild]I tried Dapper the other day and about 50% of the programs I tried I was able to find a severe bug in, I try to make software fail because users will hit those scenerios in real life. It's a hobby, some people collect stamps, I break software. I was even able to make the installer misbehave.

I have no earthly idea how they plan to support this for 5 years, I'm really scared that they are getting in over their heads with the longterm support promise. Dapper is nowhere near ready for that kind of deployment. The problem for my money isn't that Canonical might be loosing money on this, but that they make GNU/Linux look bad by claiming that 6.06 LTS is suitable for massive deployment. 

My objective evaluation is that Dapper isn't ready for release and especially not for the LTS plan, the dapper development cycle has been rapid development not aimed at stability nor security. If you plan to release something with this level of support you can't go introducing tons and tons of new unvetted and unreviewed code.

If Dapper is to be supported for 5 years following release, I'd bet we'd need another 12 months of pure stresstesting and bugfixing with absolutely no introduction of new code. This kind of dedication to quality assurance is why products like RHEL are so succesful.

What is acceptable on your desktop is not the same as what is acceptable on a corporate desktop which has to be stable and secure for long periods of time with minimal administration.

Dapper falls short of the target, I'm sorry - please don't release it I beg you to not make GNU/Linux look bad.[/QUOTE]

I agree with almost everything in this post. I don't think it would need 12 months, but an extra month of pure bugfixing would do wonders. It's great that dapper is getting so much attention, but that also increases the obligations.

---

### Post by r4ik on 2006-05-28
I clean installed RC and hit the wall..hard.
I wonder what it will do to first time linux users so from that piont of vieuw i agree with Sharkboy.
Dapper is not ready perhaps the Final release is but i find that believe close to beeing stupid.

---

### Post by dada1958 on 2006-05-28
[QUOTE=r4ik]I clean installed RC and hit the wall..hard.
I wonder what it will do to first time linux users so from that piont of vieuw i agree with Sharkboy.
Dapper is not ready perhaps the Final release is but i find that believe close to beeing stupid.[/QUOTE]

Once again: especially an installer should **not** crash:confused:

---

### Post by gsuveg on 2006-05-28
i have a realy BIG problem with dapper and apm/acpi. I have an ASUS notebook. and  after the last kernel update, it dont power off with halt -p (or from gnome). It run over the init process, and last dont power off. Before kernel uptade it worked fine.

---

### Post by DeeZiD on 2006-05-28
Everything is fine on my notebook (best working linux distri ever!).
But my printer (Canon Pixma ip4200) still won't work :evil:

---

### Post by r4ik on 2006-05-28
[QUOTE=dada1958]Once again: especially an installer should **not** crash:confused:[/QUOTE]

I got past the installer eventualy and chanched the screen resolution and ended up with the stupid "double" screen again.
Nothing to click locked rock solid.
It is just another example why Dapper is not ready or at least not for me.
Is it my hardware ?
Most likely not it does not occur with other distro's i've tried.
Please notice this is a post out of frustration and therefore not very constructive but i had to get out my system.

---

### Post by apollyonis on 2006-05-28
I'd have to say that Dapper should/could be stalled on the release at least until the end of June to at least get the booting/acpi, installer and burning bugs fixed. These are just a couple of the major issues that I believe would cause the most headaches.  There are going to be a lot of frustrated veteran Ubuntu users and the new people will be turned away if these issues are NOT resolved.

---

### Post by flankker on 2006-05-28
i have some minor issues, but by far my biggest problem is sound. only beep works (well, most of the time) rythmbox, amarok, banshee, listen.... just crash and bring down sound for the whole system with them.

i dont think the release date should be moved though, they just need to patch it and make edgy a good release.

---

### Post by awaldram on 2006-05-28
Dont forget the wirless lan and network manager also badly broke
WEP wont function at all from network manager and WPA only if you pre connect it with wpa_supplicant.

Its related to the re-mapping of wlan to eth as if you check the source for wpa_supplicant you can find the hard coded wlan antries for the network cards.

if (strncmp(ifname, "wlan", 4) == 0) {
		/*
		 * Host AP driver may use both wlan# and wifi# interface in
		 * wireless events.
		 */
		char ifname2[IFNAMSIZ + 1];
		strncpy(ifname2, ifname, sizeof(ifname2));
		memcpy(ifname2, "wifi", 4);

this strike me as very sloppy as if they are rushing when they should be walking.

Introducing the massive backports into the kernell 2 weeks prior to release is fool hardy bearing on reckless.

Lets delay the release and not luck really foolish.

---

### Post by luca.b on 2006-05-28
I dist-upgraded my notebook yesterday. The only problems I had were from non-standard software I had.

---

### Post by Lovechild on 2006-05-28
[QUOTE=sharkboy]I agree with almost everything in this post. I don't think it would need 12 months, but an extra month of pure bugfixing would do wonders. It's great that dapper is getting so much attention, but that also increases the obligations.[/QUOTE]

As much as I would love to agree with you, I doubt we could get sufficient testing done in a month. I've gathered quite some experience finding bugs, stomping out the hard to spot bugs can take ages - not only that even if they are 100% reproducable and there's confirmation - the fix might be non obvious.

To give you an example, I own a relatively highend Plextor DVD burner - however due to a security fix in the kernel I have been unable to burn anything as a user since I believe the Breezy era. Even though this is a known bug all distros have shipped with it because the fix requires a lot of work. It's okay to ship a release like FCx or any Ubuntu release because odds are the next release will fix it or an update will. However when you plan to support a distribution for 5 years, this absolutely needs to be fixed from the word go.

Another example can be see in a recent Dave Jones (Fedora kernel hero) blog post, he flooded a nic with data to uncover a bug - the bug itself didn't appear before he left it on for days. There are probably plenty of these around every distribution - or bugs where everything is fine untill you hit ctrl and right click something on a Saturday while standing naked in a barrel of eel eyes, you know the kind of bug that never shows up during testing but users have a habit of stumbling on all the time.

There are tons of bugs like this in Ubuntu currently, little bugs that just make the experience miserable if you manage to hit the correct combination. 

Futhermore it's probably known to all that I've campaigned for proactive security in Ubuntu to no avail since early in the Hoary cycle, this is not so much because I'm paranoid but because it's a great way of spotting bugs.[1] [2]
By playing fully legal tricks with the address space you can uncover some great blunders in coding, this enhances security and helps to make software more stable at a very low cost of entry mind you. The second bonus is that the hard data shows us that proactive security fixes about half of all security bugs without the need for an update - do you have any idea how much this saves over 5 years of support. It means we can issue collected updates for these bugs, rather than urgent bugfixes.

I'm sorry but history shows me that to get a truly production ready release we need more than a month, baring a small miracle that is.. if you have 1000 dedicated dogfooders up your sleeve don't hestitate to let them loose.

but thank you for the kind words.

[1] [http://lovesunix.net/blog/?p=44](http://lovesunix.net/blog/?p=44)
[2] [http://lovesunix.net/blog/?p=8](http://lovesunix.net/blog/?p=8)

---

### Post by Lovechild on 2006-05-28
[QUOTE=flankker]i dont think the release date should be moved though, they just need to patch it and make edgy a good release.[/QUOTE]

Not an option, it needs to work for Dapper, Dapper will be supported for 5 years remember. This means no silly bugs in the release.

---

### Post by racoq on 2006-05-28
Hello

I think it is easy to critacize development's work on Ubuntu, however did all of you reported the bugs founded?

I Have!

It's hard for a release to be improved or to "Rock Harder" as ubuntu staff like to call it, with a comunity where almost all the people want a stable release, and few only contribute.

I think that we have to trust in ubuntu developers, they want as much as us to Dapper to result in a stable release. 

Only people, like i do, who program know that it doesn't exist software without bugs, so don't expect a release without bugs. Suse have bugs, fedora has bugs, mandriva has bugs, and bugs will be forever part of software development even if we choose to accept it or not.

As for my opinion about dapper release on June 1. i think its stable enough to be released, delaying it will give a bad impressions to the gnu/linux comunity, and it will kill expectations of some people, who were depending on that for the use in important projects.

So don't you all agree with me if this release is delayed it will keep away some people who was expecting it.

If you guys want people to use other linux distros, so go ahead... delay it by one month ot two (don't forget that ubuntu has already been delayed). After that don't keep me saying that i didn't warn you. 

Even Dapper with fewer bugs is more secure or stable that Windows XP.

If your hardware isn't recognized (as i've saw on some issues here) don't blame it on ubuntu (since its the release who best detects the majority of the hardware parts), blame it on the kernel. And that my friends, it isn't ubuntu developers fault it's kernel developers responsability.

One last thing, if you want a installation without any problems do backups and a fresh install, or update using update notifier, other procedures are still in early development.

---

### Post by mejy on 2006-05-28
[QUOTE=Lovechild]Not an option, it needs to work for Dapper, Dapper will be supported for 5 years remember. This means no silly bugs in the release.[/QUOTE]

Can't relatively small bugs be fixed after release in the form of updates?  I remember with the release of opensuse 10 there was an annoying bug with firefox in KDE that caused it to use the gnome cursor (or something along those lines).  If there are lots of bigger bugs something really needs to be done (maybe Dapper Release 2 after a year, with no new features but lots of security features), but for smaller bugs an online update should be fine, surely?

Unfortunately I'm not sure how big the problem is - I'm running dapper with XGL and haven't had a single crash in the last two months (and its mostly quite recent hardware).  The only problems I've had were with totem, but my quarms with that piece of software don't belong in this thread...

Edit: what racoq said about fresh installs made me think - anyone looking for a stable release will surely do a fresh install once dapper has been released.  Isn't it possible that some of the bugs here are due to upgrade issues and could be fixed by doing the same?

---

### Post by DeeZiD on 2006-05-28
@awaldram:

networkmanager 0.62 works great here.
I've tested it on many notebooks with wpa and wep. 
And I don't have to use wpa_supplicant before ;)

It just works well...



But it is sad that printing and burning are not working :(

---

### Post by awaldram on 2006-05-28
Whats your card is it one that used to give a wlan0 interface ???

i.e prism/orinoco

---

### Post by DeeZiD on 2006-05-28
I'm using a Broadcom Wireless on my Acer Aspire WLMi 5024 (ndiswrapper (eth0!) or opensource driver, both are working fine with wpa here)

A friend of mine has a Toshiba A150-153 with a intel ipw3945 wireless card which works with the newest ubuntu kernel and wep or wpa in network manager.

A few weeks before I've tested networkmanager 0.61 on an older toshiba notebook with a dlink pcmia-wifi card and it worked perfectly with wpa.


regards Dennis

---

### Post by Lovechild on 2006-05-28
[QUOTE=mejy]Can't relatively small bugs be fixed after release in the form of updates?  I remember with the release of opensuse 10 there was an annoying bug with firefox in KDE that caused it to use the gnome cursor (or something along those lines).  If there are lots of bigger bugs something really needs to be done (maybe Dapper Release 2 after a year, with no new features but lots of security features), but for smaller bugs an online update should be fine, surely?

Unfortunately I'm not sure how big the problem is - I'm running dapper with XGL and haven't had a single crash in the last two months (and its mostly quite recent hardware).  The only problems I've had were with totem, but my quarms with that piece of software don't belong in this thread...

Edit: what racoq said about fresh installs made me think - anyone looking for a stable release will surely do a fresh install once dapper has been released.  Isn't it possible that some of the bugs here are due to upgrade issues and could be fixed by doing the same?[/QUOTE]

You are forgetting how corporate deployments work and how much time it takes before an update is actually applied to a client machine, if ever. This means we have to fix all the silly bugs, test upgrade paths, fresh installs.. and not just once, I mean test them till we get sick.

If customers hit silly bugs out of the box we are screwed.

Dapper has no automated testing, no QA and just look around the Dapper forum at present.. everyone scrambling to get the last complaints in - however with 4 days till release it's already to late. If the release is to be made on the 1st. ISOs will have to be spun Monday, final install tests done Tuesday and it goes out to mirrors on Wedenday..

This means there is no more time. Dapper is as good as it is going to get unless the release is pushed.

Comparing Dapper to OpenSuSE 10 is not fair, OpenSuSE never made the promise to offer support for that release for 5 years. Dapper during it's entire cycle was not run in any manner that suggested that they wanted the support it longterm. If you make that kind of a plan, you will need to be extremely conservative, going ahead with business as usual isn't a terribly good idea.

Dapper is a good release by current Ubuntu release standards but it does not have the quality it takes to play ball with a product like RHEL - they simply didn't take any precautions to ensure stability early on.

---

### Post by sharkboy on 2006-05-28
[QUOTE=Lovechild]As much as I would love to agree with you, I doubt we could get sufficient testing done in a month.

--snip--

but thank you for the kind words.

[1] [http://lovesunix.net/blog/?p=44](http://lovesunix.net/blog/?p=44)
[2] [http://lovesunix.net/blog/?p=8](http://lovesunix.net/blog/?p=8)[/QUOTE]

I'd love to use the OS you're advocating, but I don't see it happening  even in the LTS version of ubuntu. For that kind of stability I turn to debian stable or openbsd. Currently none of those work well with my too new hardware though, so I'm sticking it with debian unstable until etch is released. I think the expectations have risen way too high on dapper atm for it to be plausible with a 12 month delay. A month, two at the most. What hasn't been done by then will have to be fixed in updates. I don't want GNU/Linux to look bad anymore than you do, but right now I think a 12 month dapper delay will do just as much damage to its reputation as a premature release.

---

### Post by Lovechild on 2006-05-28
[QUOTE=sharkboy]I'd love to use the OS you're advocating, but I don't see it happening  even in the LTS version of ubuntu. For that kind of stability I turn to debian stable or openbsd. Currently none of those work well with my too new hardware though, so I'm sticking it with debian unstable until etch is released. I think the expectations have risen way too high on dapper atm for it to be plausible with a 12 month delay. A month, two at the most. What hasn't been done by then will have to be fixed in updates. I don't want GNU/Linux to look bad anymore than you do, but right now I think a 12 month dapper delay will do just as much damage to its reputation as a premature release.[/QUOTE]

A 12 month delay hurts Ubuntu and only temporarily - however it would give Ubuntu full vindication once the world sees the rocking release.

A release now with the promise of being enterprise ready.. hurts all of GNU/Linux because it makes everyone look incompetent not just Ubuntu.

Remember Ubuntu has risen to be one of the most popular distros out there, people will expect it to represent the very best GNU/Linux can offer.

---

### Post by the_tiger on 2006-05-28
I agree. Lets not pretend that Dapper is an enterprise quality release. Too many updates too late in the cycle and not enough testing. It is a good desktop release and a good first introduction to linux for the uninitiated.

Lets make edgy eft even more suitable for the home user. IMHO better out of the box multimedia support is essential. People expect to be able to listen to music, watch dvds and browse internet pages with all the multimedia available to them. I can understand not including restricted formats in the ubuntu distribution but there should be an option for a user to install them all in a simple, well explained, gui simple click process. No terminal, no confusing names, nothing to scare those who are not used to linux or text based operating. With regard to the home user better support for gadgets such as mp3 players and pdas will be needed or people will just migrate straight back to windows.

These functions are not the priority of industry. So why not introduce yet another flavour which simply uses an entire cycle to hone an enterprise edition. Test till the fingers bleed, streamline, work on improvements in all areas of networking/sharing. The demands of business are very different to those of the desktop user and I believe we are close to meeting them. I feel that direction of dapper has been torn between the two providing a release that is not quite suitable for either.

For all these comments though I think that this distribution is still one of the best out there and who knows, maybe in six months time we will have some real competition for Vista both in terms of performance and price.

---

### Post by ramiro on 2006-05-28
a few things I'd like to add

firstly, dapper is the enterprise release, whereas edgy is going to be testing new stuff. in my opinion, the ubuntu devs put too much new stuff into dapper, instead of solidifying it. Basically dapper should have been breezy but with a few _essential_ version upgrades and a hell of a lot of testing, if they needed it to be enterprise ready. Basically, it should have been six months spent getting it as stable as possible.

Unfortunately now, there are too many new packages that are unstable, and nothing can be done. Basically, dapper has to be shipped, can't be delayed now. For those of us running dapper already, this won't be a problem, since bugfixes and security fixes will continue to be released for the next 5 years. Even though it's not perfect now, I would say in a year dapper will be a rock solid enterprise ready solution. It's a shame it's not there on release, but it will get there.

> Lets make edgy eft even more suitable for the home user. IMHO better out of the box multimedia support is essential. People expect to be able to listen to music, watch dvds and browse internet pages with all the multimedia available to them.

don't count on any linux distributions offering dvd support easily accessable and free because this will never happen. If you have an issue with this then you have to take it up on the legal side because quite simply the DeCSS algorithm is illegal and an legal open source dvd player is impossible to build.

This sort of thing needs to be fought in the courts not in the technical forums because I'm sure we'd all love to have dvd support accessable and although it is perfectly technically possible the problem is it's illegal. If you would like to see this chage I recommend you store all your multimedia in free formats (such as OGG) and recommend to all your friends they do the same

---

### Post by stewski on 2006-05-28
[QUOTE=ramiro]Of you would like to see this chage I recommend you store all your multimedia in free formats (such as OGG) and recommend to all your friends they do the same[/QUOTE]

Yup - rather than bemoaning the (lets face it) relatvely minor steps required to add DVD support (in countries where its legal) pushing for adoption of free standards is the way forward.

Take that messy mp3/wmv etc collection and rip it to a decent open standard format like ogg, Then support (with your dollars/pounds etc.) any manufacturer willing to support these, I think samsung have some good devices with support for ogg!

I'd love to see a definitive list of non DRM/legally restrictive gnu/linux/ubuntu friendly devices emerge, with fair reviews of the hardware and software!

As for dappers stability, I'm only working in a home (dual boot) environment on shuttle XPC FN41-G2, but Ive had very little trouble with stability (other than a few problems with XGL which Im not too fussed about) ever since flight 5

Is it a stable corporate desktop equivalent - I don't know, but its definately good enough for most home users in my experience!
-
My 2cents - for an OS thats been going for a couple of years (although built on the great work of debian) Dapper is extraordinary both technicaly and philosophically. FLOSS for the masses is on track, sign me up!

---

### Post by pecanov on 2006-05-28
[QUOTE=ramiro]
don't count on any linux distributions offering dvd support easily accessable and free because this will never happen. If you have an issue with this then you have to take it up on the legal side because quite simply the DeCSS algorithm is illegal and an legal open source dvd player is impossible to build.

This sort of thing needs to be fought in the courts not in the technical forums because I'm sure we'd all love to have dvd support accessable and although it is perfectly technically possible the problem is it's illegal. If you would like to see this chage I recommend you store all your multimedia in free formats (such as OGG) and recommend to all your friends they do the same[/QUOTE]

It's very annnoying to read this over and over. 
DeCSS is illegal only in (the US of ) America. 
It's legal in the rest 95% of the world.

At least you can do is offer an easy way to install them. Users should be notified  about the situation. 
Nowdays, if you aren't aware of the problem, you can't find solution, and you will simply dismiss Ubuntu as an alternative. Let's be more realistic, I wouldn't install an OS that can't play DVD's and MP3's even in the office.

---

### Post by awaldram on 2006-05-28
'As for dappers stability, I'm only working in a home (dual boot) environment on shuttle XPC FN41-G2, but Ive had very little trouble with stability (other than a few problems with XGL which Im not too fussed about) ever since flight 5'

And you dual boot because???????

Personaly I've single booted Ubuntu for 2 years and have found during the last 2 weeks the Dapper has become increasingly buggy.

---

### Post by Daniel McLaws on 2006-05-28
Just yesterday, I upgraded to Dapper 6.06 LTS from Breezy 5.10 using the following upgrade script:

gksudo "update-manager -d"

And everything worked great for me. Downloading the upgrade did take a few hours. I'm wondering if the problem people are having has to do with incomplete or corrupted downloads. I'm not sure if the upgrade script does a checksum on the download or not.

Anyway, it worked in my case. So I'm wondering if the problems people are having are are a downloading, rather than a program issue.

---

### Post by stewski on 2006-05-28
[QUOTE=awaldram]And you dual boot because???????[/QUOTE]

I'm studying a course that requires the use of non FLOSS software that I currently  dont have running under dapper!

Once I finish this semesters exams I'm hopeful that I can go fully Ubuntu and use VMware player to run any nonFloss that I need for my course!

Stability wise since flight 5 (I had install issues with flight 3) I can't say I've had issues but then I've not updated in the last 2 weeks as I'm flat out on a Microsoft heavy course...

---

### Post by andrecasteliano on 2006-05-28
[QUOTE=awaldram]Personaly I've single booted Ubuntu for 2 years and have found during the last 2 weeks the Dapper has become increasingly buggy.[/QUOTE]

Well, to me last 2 weeks make dapper rock solid :D 
Human icons are so ugly now, but this can be solved after official release, I think.

--
André Casteliano
Ready to put dapper on 50+ workstations ... waiting for 'final' 8)

---

### Post by Nomearod on 2006-05-28
I think that Dapper is an amazing OS. Everything worked with my computer ( excluding my wireless card, but the solution is in the wiki ), and it took 10 min to install all the codecs and programs that I wanted ( automatix rules :D ).

---

### Post by rcarring on 2006-05-28
A simple way to upgrade is to:

first apt-get update for update-manager
a) backup sources.list
b) add the install cd as a source in repo
c) remove all breezy repos in synaptic
d) mark all upgrades
e) upgrades processed from install cd no download from network required

---

### Post by the_tiger on 2006-05-28
I understand the problem of the legality of incorporating restricted formats in the USA. However if Ubuntu can host a wiki website which explains how these things may be installed for the rest of the world anyway, why not give the option, along with legal explanation to users anyway.

With regard to formats like ogg, I personally like them, in particular FLAC for its audio quality. However for people who don't understand (and do not care) about these formats, who already have a music collection in a format such as MP3, they are just the type of person who needs the restricted codecs to be installed easily. Until that time the ordinary PC user will not migrate to ubuntu.

Finally with regard to the artwork, it will be tragic if the oppressively bright fonts and the riduclous desktop view icon are not changed soon. They are very unpopular and detract from the otherwise excellent improvements to the icons.

---

### Post by leech on 2006-05-28
Fluendo packages for mp3 support are now in Universe for Dapper.  Fluendo has also been working on a free legal DVD player for Linux.  The only Distribution that I know of that actually comes with full legal DVD play back is Turbo Linux, which comes with PowerDVD for Linux.  

Leech

---

### Post by rcarring on 2006-05-28
I read through this thread, seems opinion is divided as follows:

a) Dapper is fine, it installs ok, everything works
b) Dapper is pants, it doesn't install, nothing works
c) Dapper is acceptable but not enterprise quality

Now... compare this to Redmond's offering and consider the sheer number of security updates, bug fixes and service packs that come out on an almost weekly basis.

Consider also the system requirements of Vista compared to Dapper (Edgy, whatever version F is to be called).

Not everyone is installing Ubuntu on older machinery, some are installing on the latest Dell laptop whatever.

XP is still a five year old system, and still buggy.

Dapper is released in a few days.

---

Why do people expect an operating system with 6 months development compared to an operating system with two or three years development to be perfect?

----

The corporate desktop -- most companies upgrade their computers on a three or four year basis -- so many companies now are running systems bought and setup three or four years ago (upgraded when XP SP1 came out) -- if Dapper can support these old clunkers then it has achieved its aim.

I would look to Ubuntu going head to head with Vista next year, and that's plenty of time to come up with a nigh on perfect distribution.

---

### Post by pecanov on 2006-05-28
You are not being fair.

Windows XP has bugs but there were never in scale with the dapper bugs. This bugs are obvious and are experienced in everyday work for both desktop and office users.

... and Vista's requirements are pretty low compared to what is offered. (please check the official requirements, speculations were made about some silly requirements).

---

### Post by rcarring on 2006-05-28
Regarding Vista -- 

Last month (April) system ram requirement was 256mb, this month this has doubled to 512mb. I ran the Vista Upgrade advisor and checked this.

Only recently has it been admitted that Vista requires 15GB free disk space to upgrade/install, because of setup using images rather than individual compressed files.

I also hear that Vista will only install to first, primary partition on a pc.

---

Dapper needs 128mb ram and 2Gb disk space.

----

Point taken about XP and bugs.

---

### Post by Terracotta on 2006-05-28
[QUOTE=pecanov]You are not being fair.

Windows XP has bugs but there were never in scale with the dapper bugs. This bugs are obvious and are experienced in everyday work for both desktop and office users.

... and Vista's requirements are pretty low compared to what is offered. (please check the official requirements, speculations were made about some silly requirements).[/QUOTE]

You are not being fair: how many devices does windows XP support out of the box, most problems are still hardware problems. 
I personnaly can't find many bugs in dapper (except the Kaffeine 0.7 problems which are solved in kaffeine 0.8, I still hope Jonathand Riddel makes some packages like he does for amarok, Koffice and the rest of KDE).

For the rest: there are problems, but they can/will be fixed soon with the upgrade system. It's not Ubuntu's fault that companies don't do update/upgrades of their system, these updates are ment to make the OS secure and stable, not cutting edge. Every new distro will have bugs, if you want rock solid go for a two year old OS.

---

### Post by denzilla on 2006-05-28
I think the release cycle should go to 1 yr. 8 months to develope and the last 4 months to bugfix/polish. 

My biggest issue with OSS is that big componets of the OS are made by third parties and when a problem is reported, you get a response like " Ubuntu team does no work on Gnome. File a report with Gnome team." IMHO, if you're going to put together an OS, you should take some responsibility for improving the various components used in it. If there is a serious issue with Gnome printing or Evolution crashes, then for the sake of releasing a quality product, fix it. While Gnome or evolution aren't made by Ubuntu, they don't make Ubuntu look good when they screw up because the user assumes that its an Ubuntu problem as a whole. OSS has alot against it because of greedy corps and this whole "intellectual property" nonsense we hear so much about these days but what the community can do, should be done with alot more care than the other guy. 

This post isn't a gripe or troll. Dapper is an awesome release which shows how much Ubuntu has matured since Warty. Lots of good things to be had with Dapper!

---

### Post by Asraniel on 2006-05-28
well, in dapper bugs like:
you cant save files in ethereal!! and wxmaxima does not work!! are not solved, and i see only a small chance that they are ever fixed. i dont even know a workaround for them!

so well, i hope very much that many bugs get fixed in the next weeks.

PS: oh yes, for many people laptops do not shutdown.. well, havent seen any work on that too. so no, dapper is far from ready

---

### Post by wylie348 on 2006-05-28
Been using Dapper for some time now and pretty minor problems.  Laptop issue (not shutting down on Inspiron 8600) was definitely related to xorg.conf changes I made and are now fixed, and also sometimes related to not ensuring acpi=on is set on boot.
On that note - anyone know if there is a way to stop grub from automatically adding acpi=off whenever I upgrade the kernel?
Thanks!
:D

---

### Post by remusus on 2006-05-28
The only serious issue I've had with Dapper (other than terrible support for my card with ATI's driver) is that my laptop will only successfully suspend once per boot, the second time it will hardlock when coming out of suspend.  But my laptop is obscure enough that I doubt that can ever be fixed.  Besides, since RC hibernate has worked perfectly, so I won't whine about it.

---

### Post by Video Toaster on 2006-05-28
[QUOTE=wylie348]Been using Dapper for some time now and pretty minor problems.  Laptop issue (not shutting down on Inspiron 8600) was definitely related to xorg.conf changes I made and are now fixed, and also sometimes related to not ensuring acpi=on is set on boot.
On that note - anyone know if there is a way to stop grub from automatically adding acpi=off whenever I upgrade the kernel?
Thanks!
:D[/QUOTE]
Of course!  There's a commented-out section of the GRUB configuration file (/boot/grub/menu.lst, I think it is... can't remember exactly) that Ubuntu uses for the default boot options.  Search for acpi=off in the GRUB menu file and delete it wherever you find it.

As for Dapper being released, it's been running great for me!  I've got Kubuntu on three machines and Ubuntu on two other machines (one of which was upgraded from Breezy) and they've all been humming along with no problems to speak of - network printers work, Samba shares (both client and server) working flawlessly, crossfading between my tunes with amaroK 1.4, awesome iPod support in amaroK 1.4 and GTKPod, no crashes... I'm a very happy (K)Ubuntu user.  :D

If only the latest new network monitor icon were replaced with the old new one... ;)

---

### Post by gsuveg on 2006-05-28
[QUOTE=DeeZiD]@awaldram:
networkmanager 0.62 works great here.
I've tested it on many notebooks with wpa and wep. 
And I don't have to use wpa_supplicant before ;)
([/QUOTE]
me dont works my wifi with Networkmanager :( only wired. with old way wifi and wired works good.

---

### Post by DeeZiD on 2006-05-28
Which card do you have?
Are you using WEP or WPA?

---

### Post by gsuveg on 2006-05-28
[QUOTE=DeeZiD]Which card do you have?
Are you using WEP or WPA?[/QUOTE]

ipw2200
i have many network. with and without wep. i dont see the wifi in NM.

---

### Post by garba on 2006-05-28
telling from the number of bugs on launchpad still waiting for a fix, dapper should still be considered a software product in its beta stages, but it looks like it will be released next week nevertheless...

---

### Post by marianoi on 2006-05-28
[QUOTE=garba]telling from the number of bugs on launchpad still waiting for a fix, dapper should still be considered a software product in its beta stages, but it looks like it will be released next week nevertheless...[/QUOTE]

I agree but if you check this thread out: [http://ubuntuforums.org/showthread.php?t=183393](http://ubuntuforums.org/showthread.php?t=183393)

which I started yesterday, mostly everyone thinks otherwise...:-k 

For instance I cannot print with my PagePro 1350W when I did with Breeze...

Cheers

Mariano

---

### Post by BoyOfDestiny on 2006-05-28
I guess what spurred me is that Breezy 64 was totally broken for ati's open source driver for 3d (at least for me.) So I just moved to Dapper in late december then january for my other box...

I feel since I'm in the minority (64-bit), if I didn't want to wonder, gee will 'this' work in the next release, I wanted to make sure the bugs I ran into are addressed or at least acknowledged.

To those finding flaws the week before release, next time (if possible) either test it with dual boot, qemu, or the livecd (yes you can download and install apps from there...) and file bugs. 

The more people filing them, the better Ubuntu can be. 

You can't be sure that someone else will run into the problem, unless it's for very common tasks...

So for some Dapper is already awesome, for others, well... time to hope backports solves your issues...

Sorry if this post is preachy. I just want to counter the BS of don't use Dapper until it's done, and stay away from the 64-bit release because it has no benefit... You reap what you sow...

---

### Post by marianoi on 2006-05-28
well the printing problem is not new at all...and still not working at 3 days of the release date...](*,) 

if I (and probably many others) cannot print I cannot work efficiently so I cannot use Dapper as my main OS...and I hate to depend on M$ or other Linux distro. I personally like Ubuntu, but I have to say that for me Breeze did a better job at hardware recognition than Dapper. IMHO Dapper, in some regards, is a step backwards...:(

---

### Post by BoyOfDestiny on 2006-05-28
[QUOTE=marianoi]well the printing problem is not new at all...and still not working at 3 days of the release date...](*,) 

if I (and probably many others) cannot print I cannot work efficiently so I cannot use Dapper as my main OS...and I hate to depend on M$ or other Linux distro. I personally like Ubuntu, but I have to say that for me Breeze did a better job at hardware recognition than Dapper. IMHO Dapper, in some regards, is a step backwards...:([/QUOTE]

[https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/30282](https://launchpad.net/distros/ubuntu/+source/cupsys/+bug/30282)

Well seems someone got it to print (someone in the thread has the same model you do) but not through cups... The bug is assigned to someone... Hopefully it will be fixed within the next few days... 

Did you do a fresh install or dist-upgrade? The thread there is from dist-upgrading (not sure if that causes the bug)

---

### Post by Lovechild on 2006-05-28
I think it's time to open a bug on Ubuntu simply called "Not ready for LTS release" and cc basically everyone in this thread.

---

### Post by marianoi on 2006-05-28
I agree

---

### Post by wylie348 on 2006-05-28
Actually I have been editing this file (/boot/grub/menu.lst), but have found that every time I upgrade the kernel, the setting gets overwritten with acpi=off for some reason...!
Thanks anyways,
:)

---

### Post by Video Toaster on 2006-05-28
[QUOTE=wylie348]Actually I have been editing this file (/boot/grub/menu.lst), but have found that every time I upgrade the kernel, the setting gets overwritten with acpi=off for some reason...!
Thanks anyways,
:)[/QUOTE]
Yes, but there's another commented-out spot in menu.lst that specifies the default kernel arguments to be added when the list is updated by DPKG.  Did you also remove it from there?

---

### Post by Lovechild on 2006-05-28
Since someone had to do this, I opened the following bug:
[https://launchpad.net/distros/ubuntu/+bug/47195](https://launchpad.net/distros/ubuntu/+bug/47195)

---

### Post by angkor on 2006-05-28
> **Lovechild]Since someone had to do this, I opened the following bug:
[https://launchpad.net/distros/ubuntu/+bug/47195](https://launchpad.net/distros/ubuntu/+bug/47195)[/QUOTE]

:)

"several key Ubuntu users"? Isn't every user a 'key' user?

Let's wait and see what the reply will be.


Dapper does a great job on my box btw. Only one problem with gdm after the dist-upgrade but the rest just works. So my subjective opinion is that it's the best distro / release ever.  said:**
> Fedora truly is the truth and the path to goodness.

;)

---

### Post by alper_tr on 2006-05-28
I have installed Ubuntu Drapper yesterday and its been a total disaapointment for me. It seems as a step backwords to me. 
Why would a user needs to boot for mins on a live cd just to install system? Why arent we given choice to install it the old way? Why???

Today is 29.05.2006, why don't we get a wpa-psk support out of box??? ms windows, osx has it for more than years! Why? Whom uses WEP today!!! I mean why can't we do it from GUI, from Network Manager!
Doesn't Ubuntu developers read on forums, can't they see most people fails to install or set their wireless cards! I don't care what gnome people those.. If I use Ubuntu, Ubuntu developers are the ones I would assume responsible for that. And If I were them, I wouldnt release Drapper untill it supports wpa out of box, and i mean GUI, not editting or compiling files.
What businessmen will do? Will they spend time to adjust and tune their wireless configuration files on their way to plane at airport, or at time when they have to send emails from different locations?

Second thing, thunderbird seems as it has been installed. But where is it? Even the 'search' tool cant finds it? 

I don't want to undergrade anyonelses work, or strieve for better, but is it where linux is on era of communication? and nerworking is suppose to be strongest part of unix'es :(

---

### Post by gabbman on 2006-05-28
2 issues still on RC release.  At least on my harware.

1. Update Manager not working.

2. Cdrecord on ide-scsi units still not working.

---

### Post by Sef on 2006-05-28
> Today is 29.05.2006, why don't we get a wpa-psk support out of box??? ms windows, osx has it for more than years! Why? Whom uses WEP today!!! I mean why can't we do it from GUI, from Network Manager!

If the manufacturer's released the source codes, then wpa-psk support out of the box would be a reality.

---

### Post by Lovechild on 2006-05-28
> **angkor]:)
"several key Ubuntu users"? Isn't every user a 'key' user?
[/quote]

I took the high road called you gentlemen key users for lack of a better term. 

> 
Let's wait and see what the reply will be.


My bet.. no, but at least those here who wanted to voice their opinion had a chance to do so.

[quote]
Dapper does a great job on my box btw. Only one problem with gdm after the dist-upgrade but the rest just works. So my subjective opinion is that it's the best distro / release ever.  said:**
> 

I think my personal experiences are irrelevant, I look around at users and see quite a lot of major breakage still going on.

[quote]
Edit: Btw Are you in some sort of Fedora Core cult?


Not really, I just value having a stable and secure OS - the worship bit is merely a joke. I think Fedora has it right in many respects especially proactive security and freedom. 10% off on the robe if you sign up now.

---

### Post by christian.convey on 2006-05-28
I think I've figured it out.  By some odd conincidence, both computers in question had the same ethernet controller chip: 

Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)

My home computer is an nForce 4 board, so it also has a built-in nVidia-branded ethernet chip.  When I use that controller, everything comes up roses.  This doesn't solve the problem for my work computer, but at least I've narrowed the issue somewhat.

---

### Post by christian.convey on 2006-05-28
Thanks for the tip.  In fact, on one or both of the computers that I had the problem for, I thought I saw some error message regarding IP6.  Could you please tell me how you disabled it?

Thanks,
Christian

---

### Post by christian.convey on 2006-05-28
I agree that Dapper doesn't seem as good as it should be.  But your tone is pretty harsh.  Please remember two things.  First, this is a free distribution, and one reason it's free is that lots of unpaid people are trying to make the world a better place.  

Second, just about every one of us can do something to improve Dapper.  Whether it's filing a carefully investigated bug report, or suggesting a code patch that will fix a bug, or helping with documentation.  If you have a problem with Dapper, I encourage you to find a way to lend a hand.  Both you, and the rest of the community, can benefit.

Regards,
Christian

---

### Post by ramiro on 2006-05-28
dapper is free, but the developers are far from unpaid. Although there are many people who are giving unpaid time and effort to improve dapper, remember that there are also many developers who are being paid for it

---

### Post by Anthem on 2006-05-28
[QUOTE=Lovechild]This kind of dedication to quality assurance is why products like RHEL are so succesful.[/QUOTE]
The funny thing is that as soon as I saw your very first post, I thought "$10 he busts out a RedHat reference."  :laugh:

For what it's worth, Dapper's been rock-solid for me.  Everything works, and I haven't crashed in months.  But, as always, YMMV.

---

### Post by marianoi on 2006-05-28
Thanks for posting the bug report.

Dapper is solid, it is free, fast, secure, and overall better that Breeze. However, it has big issues that the previous release (Breeze) handled like a charm (printing for instance)

They introduced a new installer for the Live CD that is not quite working for many users (just look at the posts and some reviews)

IMHO this is not a race to catch Fedora or Suse this is about releasing the best Linux OS.

We all contribute to the community just by reading and posting things in here.

I believe that releasing an OS with the potential of not being productive or being unreliable or not being friendly installed for people with Win partitions is much worse than releasing and bug fixing short after

Cheers

Mariano

---

### Post by brian g on 2006-05-29
Dapper Drake is a Deaf Duck.
seems to me theres a lot of issues getting sound to work on upgrades.
lots of instances, few sugguestions, and no solutions.
I do realize it's still a beta, but I hope that gets cleared up before Thursday or whenever

---

### Post by angkor on 2006-05-29
[QUOTE=Lovechild]I think my personal experiences are irrelevant, I look around at users and see quite a lot of major breakage still going on.[/quote]

Totally irrelevant. However if I can't speak from personal experience what else? Dapper's just been great on this box.


> 10% off on the robe if you sign up now.

oeh, tempting....:)

---

### Post by nocturn on 2006-05-29
Did the upgrade on two systems, a desktop and a laptop.  No problems there.

The laptop was initially Hoary, dist upgraded to Breezy and now used update-manager to go to Dapper.
I did use the wired interface though as wireless is ndiswrapper which needs to be reinstalled after upgrading.

---

### Post by hap0 on 2006-05-29
"Is Dapper really ready?"

Not for me.

Two words:

1. Firefox
2. Codecs

---

### Post by morgs on 2006-05-29
[QUOTE=hap0]"Is Dapper really ready?"

Not for me.

Two words:

1. Firefox
2. Codecs[/QUOTE]

Are you experiencing regressions from Breezy? If not, note that these things are always difficult for any distro release. Edgy *will* be better.

Have you logged bugs or commented on existing bugs?

---

### Post by David Corrales on 2006-05-29
So... what's with flaming Lovechild? It seems like people here don't like to recognize things as they are.
I usually try to stay away from drama posts but the number one thing that's keeping linux from becoming mainstream is part of it's user base.

For example, why on earth after 20+ years of having an X server for Unix systems isn't there a **good, reliable and complete** GUI configuration utility for it? 
Probably because some developers and users say: "Sure, it's really easy. Just edit the xorg.conf and put this [tons of lines of code]. You should be smart enough to do that if you're using a computer". That's like buying a TV and having to google out how to solder something to make the screen a tad brighter.

Like I said, I don't get it why some people just don't accept the fact that other operative systems do some things better and **learn** from that, rather than going on blindly criticizing.
To all the anti-windows zealots... "this is not windows", "winblows", "m$ crappola". Your attitude is hurting linux more than helping.
Once you realize the fact that Windows **does** get things right in some aspects and in some it's even way beyond current linux state (complex filesystem permissions hierarchy anyone?), take all those good ideas and ask for them (or implement them!) in linux systems THEN we'll all be winning in features.

It's sad that some people really do think that Dapper's ready for wide enterprise deployment or even worse, deny the fact that it's not. Heck, not even the icon set is consistent right now (the cancel button is an undo button for example).
Personally, I had 2 huge regressions on my laptop. Sleep won't work and the 686 kernel puts my cpu to 90% use on idle and I lose around 1 hour or 1 hour and a half of battery time. Not really moving forward.

---

### Post by morgs on 2006-05-29
[QUOTE=christian.convey]Second, just about every one of us can do something to improve Dapper.  Whether it's filing a carefully investigated bug report, or suggesting a code patch that will fix a bug, or helping with documentation.  If you have a problem with Dapper, I encourage you to find a way to lend a hand.  Both you, and the rest of the community, can benefit.[/QUOTE]

+1

---

### Post by brt on 2006-05-29
some days ago i updated from breezy to dapper on my notebook without any problems :)

i was using the recommended procedure:

sudo apt-get update
sudo apt-get dist-upgrade   # just to be shure i start from an uptodate breezy
sudo update-manager -d

everything is working also wlan using ndiswrapper with the shipped driver.

i also installed dapper on a brand new PC (AMD64, nforce4, Nvidia GF6500PCie, DVB-s,2x onboard GBitLAN,Firewire) without any problems, all hardware has been detected perfectly all drivers loaded just out-of-the-box :)

my impression: "~DAPPER ROCKS~"

---

### Post by ctgray on 2006-05-29
Ubunut will never be ready for the public. Even if it was rock-solid stable with no bugs whatsoever, everyone would complain about mp3, wmv, other restricted/windows stuff. Oh and they'd bitch about the default theme too.

---

### Post by sas on 2006-05-29
[QUOTE=David Corrales]
For example, why on earth after 20+ years of having an X server for Unix systems isn't there a **good, reliable and complete** GUI configuration utility for it? 
Probably because some developers and users say: "Sure, it's really easy. Just edit the xorg.conf and put this [tons of lines of code]. You should be smart enough to do that if you're using a computer". That's like buying a TV and having to google out how to solder something to make the screen a tad brighter.[/QUOTE]

A couple of theories: rather than developing a gui configuration tool for it, it's more time efficient to make it Just Work for as many people as possible.

There's so many options to change that the end user generally won't have a clue as to what buttons they should press in order to make it work. 

It's much more versatile than the windows GUI possibilities.

---

### Post by tseliot on 2006-05-29
[QUOTE=David Corrales]So... what's with flaming Lovechild? It seems like people here don't like to recognize things as they are.
I usually try to stay away from drama posts but the number one thing that's keeping linux from becoming mainstream is part of it's user base.

For example, why on earth after 20+ years of having an X server for Unix systems isn't there a **good, reliable and complete** GUI configuration utility for it? 
Probably because some developers and users say: "Sure, it's really easy. Just edit the xorg.conf and put this [tons of lines of code]. You should be smart enough to do that if you're using a computer". That's like buying a TV and having to google out how to solder something to make the screen a tad brighter..[/QUOTE]
Windows' xserver is more advanced than GNU/Linux's. But if Linux's shipped with Nvidia and Ati's proprietary drivers by default (and if they had less problems) then things would work much better.

And if Ati, Nvidia, etc. made the licence of their drivers a bit more suitable to the one of the xserver...

And setting the driver to vesa unless the graphic driver was 100% compatible with the graphic card wouldn't be bad. (Knoppix 4 already did it).

---

### Post by southerncross on 2006-05-29
for my experience i think it' ready... ;)

---

### Post by Paloseco on 2006-05-29
Usually when you make a clean install it works very well, but when you update from previous version is a shame. The problem is when improper configuration files are kept. That has to be improved in some way, but will take some years.

---

### Post by joepotter on 2006-05-29
[QUOTE=ctgray]Ubunut will never be ready for the public. Even if it was rock-solid stable with no bugs whatsoever, everyone would complain about mp3, wmv, other restricted/windows stuff. Oh and they'd bitch about the default theme too.[/QUOTE]

Ubuntu is a Debian based distro. As such, it is a broadband based distro just as any Debian based distro.

I think fixing any network problems before calling it an "Enterprise Release" would make sense. Do you think the "Enterprise" is ready for a distro that does not work with WPA wifi reliably? I think not.

After all, it is somewhat difficult to download a "fix" for a broken network. :-)

By the way, at [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto) we see that Ubuntu sends anyone tring to use Dapper over to Debian proper for infomation! 

Dapper will be released. It will be fixed up in a couple of months --- just like Breezy.

---

### Post by mejy on 2006-05-29
[QUOTE=Paloseco]Usually when you make a clean install it works very well, but when you update from previous version is a shame. The problem is when improper configuration files are kept. That has to be improved in some way, but will take some years.[/QUOTE]

Speaking from personal experience, I made a clean install and it worked fine.  If this is the same for most people, can we not expect enterprise customers (who need the support) to make one?  A pole has to who's had problems with a clean install after flight 7 might be usefull.

---

### Post by Paloseco on 2006-05-29
[QUOTE=mejy]Speaking from personal experience, I made a clean install and it worked fine.  If this is the same for most people, can we not expect enterprise customers (who need the support) to make one?  A pole has to who's had problems with a clean install after flight 7 might be usefull.[/QUOTE]
I tried all flight versions from 1 to 7, and to get it working most times I had to install ubuntu each time. Do you think that is "normal"?. I do not think so. Tha major problem is that you have to make another partition in order not to lose your data, or you can format the current partition and backup all .conf files for everything. Because if there are wrong configurations with one version are kept when updating. Really sucks. I do not know if enterprise users prefer to update or fresh install but any of both options should work flawlessly on each situation.

---

### Post by wanger123 on 2006-05-29
[QUOTE=wylie348]Been using Dapper for some time now and pretty minor problems.  Laptop issue (not shutting down on Inspiron 8600) was definitely related to xorg.conf changes I made and are now fixed, and also sometimes related to not ensuring acpi=on is set on boot.
On that note - anyone know if there is a way to stop grub from automatically adding acpi=off whenever I upgrade the kernel?
Thanks!
:D[/QUOTE]

Care to let us know how you solved this problem in your Xorg.conf file

many thanks

wanger

---

### Post by tseliot on 2006-05-29
[QUOTE=wylie348]Actually I have been editing this file (/boot/grub/menu.lst), but have found that every time I upgrade the kernel, the setting gets overwritten with acpi=off for some reason...!
Thanks anyways,
:)[/QUOTE]
You have to edit the "kopt" line in your /boot/grub/menu.lst:
e.g.
# kopt=root=/dev/hdc1 ro

and add or remove option there.

Then save and exit.

Type:
```
sudo update-grub
```

---

### Post by wanger123 on 2006-05-29
As stated in the original bug post, DAPPER IS NOT READY FOR RELEASE!!!!

Many many laptop users cannot shutdown, reboot or logout. This includes me on a Dell Inspiron 9300 using the official ATI driver.

Why does sudo /sbin/halt or sudo /sbin/reboot work from the konsole but not from kde/kdm?????? (kde uses /sbin/halt and /sbin/reboot in the login manager section of system settings). Is there some other script called for by the gui?

Also, I upgraded the kernel on the 24/05/2006 and then was presented with a non-bootable system due to dapper being unable to find root hd0,0 or something like that. Luckily I still had another kernel installed so I could boot up and remove the updates

wanger123

---

### Post by tseliot on 2006-05-29
Anyhow Dapper works great here.

---

### Post by Athropos on 2006-05-29
I did a dist-upgrade on two computers last week without any problem. Perhaps that problems are mostly encountered by people who 'hack' a lot their system...

---

### Post by ctgray on 2006-05-29
Most people who think Dapper is 'not ready' is mostly (I say mostly) laptop users. They all want to have hibernate/sleep/wifi working perfectly out of the box and IMO that will not happen for a long time.

Sorry if I seem hostile, it's just that whenever I come onto the Dapper forum there's always some thread stating that Dapper isn't ready of whatever.

In the end, Dapper is ready, just not for everyone.

---

### Post by awaldram on 2006-05-29
NO I think the issue as in my case

hibernate and sleep were working correctly 
wifi funtioned satisfactorily then we had the 'final kernel ' which broke it all.

as previously (in this thread)  you can see why. The kernel remapps wlan0 to eth0 yet the apps do allow for this.

Obviously this only affect peoples who wifi used to be wlan0.  (prism etc)

Sorry if I seem hostile but having had to rebuild my laptop due to file corruption (new Kernel and prelinked file) to only find things are worse with a clean build. I am a litle techy.

---

### Post by joepotter on 2006-05-29
[QUOTE=awaldram]NO I think the issue as in my case

hibernate and sleep were working correctly 
wifi funtioned satisfactorily then we had the 'final kernel ' which broke it all.

as previously (in this thread)  you can see why. The kernel remapps wlan0 to eth0 yet the apps do allow for this.

Obviously this only affect peoples who wifi used to be wlan0.  (prism etc)

Sorry if I seem hostile but having had to rebuild my laptop due to file corruption (new Kernel and prelinked file) to only find things are worse with a clean build. I am a litle techy.[/QUOTE]

You need to learn from this. The Ubuntu team will always break the system just before release. With Breezy they had at floppies and cdroms with a broken pmount just a week before release and then it was not fixed for a long time even after it was fixed in the development release (was Dapper back then).

Now they break 3 out of 20 boxes at my work with this new kernel, and at the same time they have borked wireless.

So, wait a few weeks till the "Enterprise" people start complaining and we will get action. The key lesson is that a new Ubuntu release is polished *after* release because the developers can not resist throwing stuff at the system with a sort time to go until release.

Perhaps they will mature and learn from all this, but I am betting against it. :-)

---

### Post by r4ik on 2006-05-29
Message understood.
Thanks.

---

### Post by brt on 2006-05-29
[QUOTE=ctgray]Ubunut will never be ready for the public. Even if it was rock-solid stable with no bugs whatsoever, everyone would complain about mp3, wmv, other restricted/windows stuff. Oh and they'd bitch about the default theme too.[/QUOTE]

LOL, if this would be true, m$ windoose would never be ready for anything, i know not one single novice who would be able to install winXP on a modern PC with sata drive, or how to install the right drivers to get common onboard networkcards to work.
80% of the mainstream PC's out there just work because they have been pre-installed by the manufacturers, the rest is setup by some windo$ geeks.

---

### Post by wanger123 on 2006-05-29
[QUOTE=ctgray]Most people who think Dapper is 'not ready' is mostly (I say mostly) laptop users. They all want to have hibernate/sleep/wifi working perfectly out of the box and IMO that will not happen for a long time.

Sorry if I seem hostile, it's just that whenever I come onto the Dapper forum there's always some thread stating that Dapper isn't ready of whatever.

In the end, Dapper is ready, just not for everyone.[/QUOTE]

I don't really give a f##k about hibernate/sleep, but I really would like to shutdown or reboot my laptop on demand (seems kind of fundamental to me but maybe I AM expecting too much!!)

wanger

---

### Post by cliveau on 2006-05-29
[QUOTE=christian.convey]Hi guys,

On two out of two computers, my upgrade from Breezy to Dapper's RC (release candidate_resulted network interfaces that no longer worked and that I couldn't repair.

Is Dapper generally unready for release, or am I just especially unlucky for some reason?  From my experiences with it, it still seems way below the quality goals that the community and Mark have for it.

Am I the only one with this experience?

- Christian[/QUOTE]

 
dear christian, you can try the on screen menus"system-administration-networking"
click in "Ethernet connection" - 
"activate"-"properties"-enable connection- click "DHCP" "Okay"

then you may get online again

---

### Post by christian.convey on 2006-05-29
Thanks, but I'm passed the problem.  Apparently something with the particular chipset on the ethernet card I tried.  Turns out both computers' NICs used the same problematic chipset.  That was a regression from Breezy.  Fortunately my home computer also has another ethernet controller built into the motherboard which is finally supported in Dapper.  So I'm ok for now.

---

### Post by bluenova on 2006-05-29
[QUOTE=pecanov]It's very annnoying to read this over and over. 
DeCSS is illegal only in (the US of ) America. 
It's legal in the rest 95% of the world.

At least you can do is offer an easy way to install them. Users should be notified  about the situation. 
Nowdays, if you aren't aware of the problem, you can't find solution, and you will simply dismiss Ubuntu as an alternative. Let's be more realistic, I wouldn't install an OS that can't play DVD's and MP3's even in the office.[/QUOTE]
Well you have to select your country during install, so an easy option would be if US is selected the installer won't install the things that are illegal in the US and if any other country is selected then those codecs etc will be installed.

---

### Post by nocturn on 2006-05-29
[QUOTE=bluenova]Well you have to select your country during install, so an easy option would be if US is selected the installer won't install the things that are illegal in the US and if any other country is selected then those codecs etc will be installed.[/QUOTE]

Yeah, but if a user still goes ahead and selects UK even though he is in the US?
The DMCA would still apply and when you consider the Sklyarov case a couple of years back, I would even refuse to do this as a developer unless I was 100% sure that I would never set foot in the US.

---

### Post by sean on 2006-05-29
I am running OpenSuse 10.1 on my Lenovo ThnkPad t60.  In my opinion, Ubuntu Dapper has far too many problems even with laptop installs.

Sean

---

### Post by rcarring on 2006-05-29
I thought that they had already started mastering the ship it cds for despatch this week. I think it's too late now.

---

### Post by bluenova on 2006-05-29
[QUOTE=nocturn]Yeah, but if a user still goes ahead and selects UK even though he is in the US?
The DMCA would still apply and when you consider the Sklyarov case a couple of years back, I would even refuse to do this as a developer unless I was 100% sure that I would never set foot in the US.[/QUOTE]
That's true, but at least it would put the responsibility in the hands of the person installing rather than the developers of ubuntu. Especially if a message was given that installing for another country than the one you reside could breach local laws. Just food for thought, it would be nice if there was a legal way to easily install for countries where it is legal. It would help a lot of newbies moving to Linux.

---

### Post by hap0 on 2006-05-29
> [QUOTE]Originally Posted by hap0
"Is Dapper really ready?"

Not for me.

Two words:

1. Firefox
2. Codecs

Are you experiencing regressions from Breezy? If not, note that these things are always difficult for any distro release. Edgy *will* be better.[/quote]

Fresh install Kubuntu, latest revision as of two days ago.

> Have you logged bugs or commented on existing bugs?

Nope. I barely had time to test the install. Thus posting here is as far as I've gotten. I took this forum for a venue for surveying current user experience, which is what I *took the time* to report - albeit in few words (sorry).

The issue persists none-the-less. I'm going to give Mepis another look.

Cheers.

---

### Post by cjm5229 on 2006-05-29
I have been using Dapper since flight 4, I did a fresh install with beta 1, have just kept upgradeing twice a day since then. Right now I have virtually no issues. I can play videos, Printer works great, am presently printing the entire KJV New Testament for my Father-In-Law, My Epson CX6400 works perfectly. I have absolutely 0 issues with sound, I don't use Wifi, have 4 computers networked through my DSL Router, 2 are using Dapper, 1 uses PCLinux MiniMe, and one is still on WindowsXP, (Teen agers computer) When the viruses finally completely overwhelm that one it will get Dapper also. No Networking issues, except Permissions issues, for some reason the PCLinux box will not even show shareing. I have had problems with the liveCD though. In two of my computers It takes 14 min. to boot up, in the one with PCLinux installed it runs fine, but won't install, but for some reason I can't even get Breezy to install in that one, In the XP box, it will boot up but is VERY slow, takes 2 min to bring up the Apps menu.  I'm not too sure the LiveCD is ready yet but Dapper it's self is doing great. Just stick to the Text install CD and most problems disappear. 
I think it is ready to go final, but I would nix the live CD installer for now.

PS. I tried Fedora Core 5, My bottom was so sore I couldn't sit for a week.

---

### Post by Lovechild on 2006-05-29
Regardless the battle is over Mark Shuttleworth himself closed the bug, there is nothing left we can do to stop a release on the 1st. 

If your hardware has the slightest flaw or there's a software flaw causing you grief the only option is filing tons and tons of bugs. Hopefully this will lead to your setup being supported in the near future.

However this isn't likely to fix installer bugs unless they respin the ISOs at somepoint - this however isn't likely either for support reasons (you'd suddenly double the amount of installer media you'd have to support which isn't desirable for a LTS cycle).

If you can find the last changeset where something worked it would be greatly helpful in fixing your bug.

I'll remain of the opinion that going ahead is a mistake, but bitterness will not bring us further towards getting the many broken setups supported. If your hardware isn't supported out of the box all you can really do is be vocal - bugreports are good, bugreports with patches are better.

---

### Post by effoff on 2006-05-29
No Dapper is not ready. As long as you have several thousand users shutting down their laptops with the power button because of screwed up scripts, it won't be ready.

---

### Post by Paloseco on 2006-05-29
[QUOTE=effoff]No Dapper is not ready. As long as you have several thousand users shutting down their laptops with the power button because of screwed up scripts, it won't be ready.[/QUOTE]
i have a Clevo and I am using kubuntu, the power button always works perfectly for me.

---

### Post by David Corrales on 2006-05-29
[QUOTE=brt]LOL, if this would be true, m$ windoose would never be ready for anything, i know not one single novice who would be able to install winXP on a modern PC with sata drive, or how to install the right drivers to get common onboard networkcards to work.
80% of the mainstream PC's out there just work because they have been pre-installed by the manufacturers, the rest is setup by some windo$ geeks.[/QUOTE]
To see it your way, 80%+ of the computers using linux today not only have been installed by linux geeks but they also need one to properly function. That's the real problem.
And I also don't know any novice or experienced user who can install Ubuntu from the live cd if it crashes and leaves you with an unbootable system :)

---

### Post by David Corrales on 2006-05-29
[QUOTE=ctgray]In the end, Dapper is ready, just not for everyone.[/QUOTE]

That's an oxymoron. You can't be "ready" if you're not ready for everyone, unless Ubuntu is called "non-laptop edition" or something.

---

### Post by effoff on 2006-05-29
[QUOTE=Paloseco]i have a Clevo and I am using kubuntu, the power button always works perfectly for me.[/QUOTE]
The PHYSICAL machine power button works perfectly for everyone, but that is not how to shut down a laptop unless the shutdown scripts are screwed up. 
Many many users cannot shut down normally by hitting the GUI shutdown button.
It is not model specific. Therefore it must be a reintroduced script error.

Ok then! Dapper is ready! Shutdown your laptop with a hammer.... until further notice.

---

### Post by David Corrales on 2006-05-29
[QUOTE=sas]A couple of theories: rather than developing a gui configuration tool for it, it's more time efficient to make it Just Work for as many people as possible.

There's so many options to change that the end user generally won't have a clue as to what buttons they should press in order to make it work. 

It's much more versatile than the windows GUI possibilities.[/QUOTE]

[QUOTE=tseliot]Windows' xserver is more advanced than GNU/Linux's. But if Linux's shipped with Nvidia and Ati's proprietary drivers by default (and if they had less problems) then things would work much better.

And if Ati, Nvidia, etc. made the licence of their drivers a bit more suitable to the one of the xserver...

And setting the driver to vesa unless the graphic driver was 100% compatible with the graphic card wouldn't be bad. (Knoppix 4 already did it).[/QUOTE]

I have to agree that the issue with nvidia and ati is problematic (though nvidia does a good job releasing good drivers).

Even like that, I think it's really odd that a windows server doesn't have a GUI configuration utility. It's like having a car manufacturing plant and using oxcarts to haul the parts around, it just shouldn't be.
A good solution would be to do what Windows does in that regard. They use a failsafe 100% vesa mode that's compatible with 99.99% configurations (640x480 @8bits). If the config tool tries to do something funky, you revert to that one until the user gets the screen the way he wants.
Finally, about the complexity, it's our job as IT professional to try and hide it from users while making expert based default choices. You won't get to edit **every** parameter there is in Xorg.conf, just the ones you need to get things working. Stuff like dual screen setups should also go into this utility.

---

### Post by awakatanka on 2006-05-29
[QUOTE=nocturn]Yeah, but if a user still goes ahead and selects UK even though he is in the US?
The DMCA would still apply and when you consider the Sklyarov case a couple of years back, I would even refuse to do this as a developer unless I was 100% sure that I would never set foot in the US.[/QUOTE]
Will this also happen if something offended a law in a small country and the rest of the world had no legal issues?

Don't think so, The whole world needs to follow a US law but the otherway around it won't be happening.

---

### Post by garba on 2006-05-29
[QUOTE=David Corrales]
Even like that, I think it's really odd that a windows server doesn't have a GUI configuration utility. [/QUOTE]

yep, very true, I think we need a gtk frontend to xorg.conf, and most of all, the xserver should fall back to vesa mode when unable to start because of some problem with the ati/nv drivers.

---

### Post by AllenGG on 2006-05-29
Whoa! hold it. we're way off topic here. First, on a "spare" working system it was difficult to install Dapper. Very. So, I changed disk parameters (don't ask) and tried a new  way, no luck. SO, re-installed  5.10 , Breezy, and did an **"upgrade",** viola ! success.  That's on an X86 machine. Now I need to do same on an AMD64, now, again, **is Dapper ready for a "production" machine ?** (yes, I've seen the disclaimer.)

---

### Post by stewski on 2006-05-29
[QUOTE=AllenGG]Whoa! hold it. we're way off topic here. First, on a "spare" working system it was difficult to install Dapper. Very. So, I changed disk parameters (don't ask) and tried a new  way, no luck. SO, re-installed  5.10 , Breezy, and did an **"upgrade",** viola ! success.  That's on an X86 machine. Now I need to do same on an AMD64, now, again, **is Dapper ready for a "production" machine ?** (yes, I've seen the disclaimer.)[/QUOTE]

All I can tell you is on my setup dapper looks good to go.

For people with serious issues from upgrading, Ive installed plenty of computers with plenty of OS's and Ive never liked upgrades, fresh/clean installs are usually beneficial and that goes double if you've been "playing" with unusual software/configurations.
if suspend doesnt work and you're running a whole heap of XGL AIGLX maybe you need to prioritise!

---

### Post by dvarsam on 2006-05-29
> Originally Posted by nocturn
Yeah, but if a user still goes ahead and selects UK even though he is in the US?
The DMCA would still apply and when you consider the Sklyarov case a couple of years back, I would even refuse to do this as a developer unless I was 100% sure that I would never set foot in the US.

Conclusion: the installation of the "codecs" should be independent to the country which somebody selects...

[QUOTE=bluenova]That's true, but at least it would put the responsibility in the hands of the person installing rather than the developers of ubuntu. Especially if a message was given that installing for another country than the one you reside could breach local laws. Just food for thought, it would be nice if there was a legal way to easily install for countries where it is legal. It would help a lot of newbies moving to Linux.[/QUOTE]

Correct!
A popup screen will warn the user, describe how the case is in the US (or other countries too!) & pass/forward the "full" responsibility in the hands of the person installing the codecs...

Case solved! & the Ubuntu OS stays on the safe side!

What do you think?

P.S.1> The Release of the Dapper MUST NOT be delayed!
P.S.2> All problems found in each & every one of you, should be posted in the forum & reported as bugs.
P.S.3> Each & every problem/case will be looked-in on an individual basis, see what hardware is involved with it & see how many people are facing such problem... (if you post on the forum, we will see how many people might be facing the same problem - how common/popular the problem is - & all the community will try to help you solve your problem). Besides, this is what we have been doing until today, haven't we? And in 95% of the times (if not more) things get fixed!
P.S.4> My personal experience: When M$ released the latest beta version of IE for WinXP (a few months ago), when I installed it, all the Favorites (or Bookmarks) would not launch when clicked... & there was NO  "uninstall" button to get rid of the beta IE... I had to FORMAT my PC!!! So, what is the conclusion? That M$ must never launch the IE newer edition?
P.S.5> Other personal experience: When I bought WindowsMe as an upgrade to Windows98, whenever I tried to Upgrade (instead of Format & Clean Install), hell would break loose & the PC would "halt" (whenever it felt like it). So the conclusion again is that M$ must NOT launch WinME?
P.S.6> Life proves the opposite... New releases must keep up & running! The more people that use the OS, the faster the problems will surface out & the faster they will be solved... And for God Sake, stop "crying out" like babies, that the Dapper should not be released! Just be logical! Dapper will have bugs & XP will have bugs! If you do NOT like any of these OS's, just quit using your PCs & return back to your little "caves" & do not forget to hide behind your "bushes"!!!

---

### Post by joshrobinson on 2006-05-29
one of these threads pop up all the time.. i think dapper is perfectly ready, anything that needs to be fixed after launch can easily be fixed with an update

---

### Post by 23meg on 2006-05-29
I won't comment on the readiness or not readiness of Dapper; I'll just be a jackass for a moment and leave. This isn't about just this thread, or the reactions on these forums, but my general impression of the reactions to Dapper Flight 6 and later all over the net.

"It's not ready because it didn't detect my wireless card out of the box" or "Of course it's ready; I've had no problems whatsoever" or "It's not ready, it's the crappiest OS ever, Ubuntu is moving backwards, not forwards with each release because I still don't have sound even though I've been working on it for three days" of "OMG DRAPPER IS DA BOMB!! It detected all my hardware and installed in two minutes and AIXGL r0x0Rz!!!" are not valid statements. Because:

- They draw on insufficient data (limited set of hardware and usage permutations)
- They often draw on insufficient knowledge (made obvious by comments on various shortcomings or strengths)
- They often originate from a position that's already been taken regarding the viability of the OS.

In other words: "Dapper is a crappy OS because it didn't detect my soundcard" is a statement that makes sense; at least we are used to and can understand the reasoning behind it, but "Dapper isn't *ready* because because it didn't detect my soundcard" is not. Ubuntu's roadmap is clear, and its fixed release cycle is the greatest determining factor in it, and the six week delay was a one time exception  made in order to reach the long term support goal.

An Ubuntu release cannot be delayed forever; there are other OSes that can always be delayed forever, and will still work perfectly for many uses, such as Debian Stable. But there's no other Debian derivative that can ship a "stabilized" Sid plus lots of polish plus great community and professional support minus a lot of hassle EVERY SIX MONTHS other than Ubuntu. 

And to remain like that, and go on with pushing development ahead, Ubuntu has to keep making releases. A bit more delay and we have no more time to resync with the Gnome cycle and test the next release properly, thus Edgy would have to be skipped altogether, or turn out worse than the "unready" Dapper. Whether it's enough for the LTS goal or not (that we shall see altogether in the next five years), six weeks was all that could have been compromised. I'm inclined to believe, in a broad strategic planning sense, that it was a good compromise.

---

### Post by Lovechild on 2006-05-29
Where does all this "delay forever" talk stem from. I specifically said 12 months under the assumption that we change as little code as possible and do as much stress testing as possble. Given the Vista release being early 2007 cutting testing down to 6 months might just be a good idea simply to be competitive with Microsoft at the time they ship their product but this requires very strict development and testing guidelines.

I specifically noted how the Dapper cycle followed none of the time honored methods for ensuring well tested and easily supportable software.

If Dapper was just another Ubuntu release I wouldn't have complained, but if you just look around this place the amount of issues in Dapper now days before release. The question does have to be posed, are we really prepared to support it for 5 years.

There's a big difference between the kinds of people who will jump on Edgy shortly after Dapper' release and those who plan to deploy a desktop in an Enterprise environment. And I'm sorry but people who don't fall into the second catagory should think very hard before posting fanboy "Ubuntu is the teh r0xor!!" posts, you are simply not the target for Dapper.

I had hoped that Dapper would be a second choice for this kind of deployment (the other one being RHEL/CentOS), however this is simply not the case.

---

### Post by agurk on 2006-05-29
Perhaps there's a middle way here, how about releasing Dapper now but putting the Edgy development start on hold 'til October? That would get the product out the door, while buying a whole four months to be invested in focused support of the Dapper release. It would at the same time give Edgy a [probably much needed] full six-month dev cycle.

---

### Post by christian.convey on 2006-05-29
I think our situation is different than how you characterize it.  Here's why:

- Dapper is being advertised as having 5/3 years support.  While not stated explicitly, an implicit message is that with this long-term support commitment, Canonical is claiming that Dapper is a pretty stable Linux distro.

- In my own case, I can across two major regressions on two computers that I upgraded from Breezy.  One was that my ethernet chipset (which happened to appear in both computers) stopped working.  Or didn't work with IP6. Or something.  The other problem is that fsck.vfat started pegging the CPU on a particular file I have on a vfat partition.  Regressions are more problematic than the average bug, because it means you can't trust a system upgrade to not break things.  

- Maybe I just didn't read the message boards closely enough when Breezy was about to come out, but it seems to me that many more people are voicing concerns about major bugs in Dapper than they did in Breezy.  This makes me think that a larger fraction of people installing Dapper will encounter problems than did people installing Breezy.

So those two apparent problems: regressions and a large number of serious bugs, make me afraid that Canonical/Ubuntu will look bad when Dapper is released.  That is, Dapper will have a big seal of quality from Canonical, but will actually get a reputation for being pretty buggy compared to Breezy.  I don't want Canonical or Ubuntu to look bad because I want both to succeed.

Or to put it differently:  Could you imagine a bug list sufficiently  bad that Dapper shouldn't be released?  Because all I'm doing is asking, is Dapper in that state?  I'm not presuming that my experience alone gives the answer.

---

### Post by AllenGG on 2006-05-29
[SIZE=3][COLOR=Sienna]**OK, here's the "reality check"  Dapper (6.06) is ready.**[/COLOR][/SIZE]
Think back, say 10 years ago when Microsoft released versions and said they were "ready", we know that was untrue.
Perhaps, we here on this forum should be more supportive and accept that Dapper is a very complex and terrific system. Jump in and help, that's what this forum is all about.
Our complaints are minor. Our demands are major.
No one here is a neophyte. 
[SIZE=3][B]Sure, 6.06 may not be ready for "enterprise" desktops that do not have proper IT support.
Who here falls in to that category ?

[/B][COLOR=DarkRed]Allen8)[/COLOR][/SIZE]

---

### Post by 23meg on 2006-05-29
[QUOTE=Lovechild]Where does all this "delay forever" talk stem from. I specifically said 12 months under the assumption that we change as little code as possible and do as much stress testing as possble. [/QUOTE]I wasn't referring to your particular statement (which to be honest I hadn't read before) but to the example I myself gave, namely Debian Stable and its fame at being delayed.

---

### Post by morequarky on 2006-05-29
I guess I am going to stick with Breezy for a while.  Dapper, according to posts here, isn't ready.  In some ways, I would like to test Dapper and report bug after bug, but I have a message board running and I can't have days of interuptions trying to get my network and server working in Dapper.  Sad really.

Two points.

I read the RC message and the only thing it said was JUNE RELEASE.  It didn't say the FIRST.

Secondly,  Blizzard E regularly delays games for quality.  No one complains about the setbacks really, because the games are SO good when it finally does go GOLD.

Should there be more testing?  Sure.  Should we take part?  Sure.

---

### Post by joepotter on 2006-05-29
[QUOTE=23meg]I wasn't referring to your particular statement (which to be honest I hadn't read before) but to the example I myself gave, namely Debian Stable and its fame at being delayed.[/QUOTE]


Debian stable gets delayed because they support many more platforms than Ubuntu. Plus, they put out a *very* stable product.

The fact is, I find Debian **testing** to be very stable and usable all the time. It has a few bugs, but then so does other folks "Enterprise" release.

---

### Post by minisori on 2006-05-29
In my case I have it on serveral computers, I'm not having any problem at all. All the updates working smooth, not messing anything. Since I upgraded to dapper in flight 4 is been working better than breezy.

So I would say it's ready.

---

### Post by drizek on 2006-05-29
[QUOTE=morequarky]
Secondly,  Blizzard E regularly delays games for quality.  No one complains about the setbacks really, because the games are SO good when it finally does go GOLD.

Should there be more testing?  Sure.  Should we take part?  Sure.[/QUOTE]


Blizzard doesnt delay games 2 days before the release date, and Dapper WILL ship this thursday.

---

### Post by morequarky on 2006-05-29
"Blizzard doesnt delay games 2 days before the release date, and Dapper WILL ship this thursday." by drizek


That is true.  Dapper should have been delayed longer months ago.

---

### Post by Lovechild on 2006-05-29
[QUOTE=AllenGG]
Sure, 6.06 may not be ready for "enterprise" desktops that do not have proper IT support.
Who here falls in to that category ?
[/QUOTE]

That was the entire point of the Long term support target for Dapper.. what is so hard to understand about that, it falls short of that one promise and it is being marketed on that promise.

---

### Post by David Corrales on 2006-05-29
[QUOTE=Lovechild]That was the entire point of the Long term support target for Dapper.. what is so hard to understand about that, it falls short of that one promise and it is being marketed on that promise.[/QUOTE]

I agree with you Lovechild but I think he was trying to convey the idea that with good IT support staff, it's ok to have a really buggy desktop installation.
Try to manage 300 dapper desktops full of bugs. Just give it some **deep** thought and you'll see why some of us here would've liked another kind of decision taking in regards to quality.
In big enterprises there's patching policies, testing and QA. You can't expect that a company will be rolling 100mbs of patches every 2 days for every single desktop.

---

### Post by Lovechild on 2006-05-29
[QUOTE=David Corrales]I agree with you Lovechild but I think he was trying to convey the idea that with good IT support staff, it's ok to have a really buggy desktop installation.
Try to manage 300 dapper desktops full of bugs. Just give it some **deep** thought and you'll see why some of us here would've liked another kind of decision taking in regards to quality.
In big enterprises there's patching policies, testing and QA. You can't expect that a company will be rolling 100mbs of patches every 2 days for every single desktop.[/QUOTE]

Exactly.. 

He failed to understand that when it comes to system administration on that level it's just not acceptable to roll out massive updates every week uncritically. It entails lenghty testing. 

His desktop is not comparable to maintaining a large network of clients machines, a cron job to do updates and hoping for the best just doesn't cut it.

---

### Post by rcarring on 2006-05-29
I used to work in an NT shop. Our rule was nothing was upgraded until the technical testing dept had completed regression testing with every single app the company used, including custom built ones in house. I think XP took four years for them to roll out.

So far as an Enterprise distribution is concerned, many companies simply build an image, make sure it works and then roll it out. So, Dapper may be released 6-1 but a corporate might not roll it out till November, or whenever they are happy with it.

---

### Post by blakamin on 2006-05-29
[QUOTE=rcarring]Dapper may be released 6-1 but a corporate might not roll it out till November, or whenever they are happy with it.[/QUOTE]


Exactly!

Does everyone think think that every corporation that *might-at-some-stage* use Dapper is just waiting for Thursday to roll around so they can go "stuff it, we'll install this on every computer in the company NOW and to hell with the consequences"?


](*,) 
btw, my company only started using XP in Jan 04!

---

### Post by Lovechild on 2006-05-29
[QUOTE=blakamin]Exactly!

Does everyone think think that every corporation that *might-at-some-stage* use Dapper is just waiting for Thursday to roll around so they can go "stuff it, we'll install this on every computer in the company NOW and to hell with the consequences"?


](*,) 
btw, my company only started using XP in Jan 04![/QUOTE]

No but they do look at softwares track record and if the record says that there's a significant chance of large untested chunk of coding being dropped on them.. would they be likely to use it?

---

### Post by aysiu on 2006-05-29
[QUOTE=blakamin]
btw, my company only started using XP in Jan 04![/QUOTE] My company started using XP only this past year (late 2005).

---

### Post by drizek on 2006-05-29
rcarring, that is a really good point. Ubuntu at this stage is not known for its stability or security compared to other linux distros, and no company is just going to jump in and upgrade without doing some real comparisons. 

Ubuntu at heart is still designed for desktop/educational use and dapper works really well for that. TBH, im not sure what made shuttleworth decide to do this TLS thing. Ubuntu just started 2 years ago, and it only started being decent one year ago. I dont think its right to expect a distro to mature from "usable" to "mission critical" in just one year.

---

### Post by ubman on 2006-05-29
Ive just recently d-loaded dapper and been an avid suse user but i find myself using dapper more and more. 
I think the devs have done an excelent job quick and easy install and configuring all the pkgs i would ever need..
NICE NICE NICE:) 
can't see me copying over this distro unless its for the next release!

---

### Post by lonetree on 2006-05-29
[QUOTE=David Corrales]I agree with you Lovechild but I think he was trying to convey the idea that with good IT support staff, it's ok to have a really buggy desktop installation.
Try to manage 300 dapper desktops full of bugs. Just give it some **deep** thought and you'll see why some of us here would've liked another kind of decision taking in regards to quality.
In big enterprises there's patching policies, testing and QA. You can't expect that a company will be rolling 100mbs of patches every 2 days for every single desktop.[/QUOTE]

I have been following the progress of dapper for a while, at first I thought it would be a good idea that dapper being delayed from April to June is a good move. I totally agree with what David Corrales say. (if you break a single stick, it is easy, but if you try to break 10 sticks at a time, you find that it is not easy) No one will want to maintain a bunch of desktop being buggy and everyday users will call up and complain on their computer having problem.

When I was using Hoary, I was completely happy about it and felt that I have found the right choice at last, but when it came to Breezy, my confidence drops, especially when it comes to many undesire problem with application which works in Hoary and not in Breezy. I was hoping that Dapper will be better and stable, until yesterday I tried it out and find that it might not be as ready, at least not for the enterprise enviroment. 

However, I will still support ubuntu and hopefully it will always remain as the best  linux distro ever. I myself have attended many linux seminars and talks and many times, they say it is ready for desktop, but let's just sit back and think about it, is it realy ready for desktop? what is the meaning of desktop to many many end users all around the world? 

I felt that linux should have at least a common standard and make installation and software upgrading as easy as the "W*****s" and "M*c" does. No end user would want to sit in front of the computer and type in command line to trace the problem and find a way to fix it. 

Hopefully one day, this will come and this is the day when linux dominates. 

Last but not least, if dapper is really not ready, I think it is better to further delay the final release, nothing to be shy about, no one will say anything about it, see how long has the other "one" been delaying their new OS, W****** V***a ? 

Wow thats a long one, sorry if it strain your eyes.

regards,

---

### Post by blakamin on 2006-05-29
[QUOTE=Lovechild]No but they do look at softwares track record and if the record says that there's a significant chance of large untested chunk of coding being dropped on them.. would they be likely to use it?[/QUOTE]


Thats why this



[QUOTE=drizek]Ubuntu just started 2 years ago, and it only started being decent one year ago. I dont think its right to expect a distro to mature from "usable" to "mission critical" in just one year.[/QUOTE]


Makes so much sense!

---

### Post by Anthem on 2006-05-29
What I find hilarious is that Lovechild, whose distro of choice is Fedora, is the one crucifying Mark for "rushing it out the door."  I mean, if you were a hard-core slackware or Debian guy, I'd take it seriously.  But Fedora?

Lovechild, you're a smart dude.  Way smarter than me when it comes to Linux.  But I can never figure out what's going on in your head... I can never follow your reasoning.  The only thing I've figured out is that you always back Red Had (no matter what), and always go against anybody who doesn't love Red Hat.  And the moment Ubuntu looked like they might steal some Sun/Oracle love from RedHat, you started having a lot more problems with Ubuntu.

---

### Post by David Corrales on 2006-05-29
[QUOTE=Anthem]What I find hilarious is that Lovechild, whose distro of choice is Fedora, is the one crucifying Mark for "rushing it out the door."  I mean, if you were a hard-core slackware or Debian guy, I'd take it seriously.  But Fedora?

Lovechild, you're a smart dude.  Way smarter than me when it comes to Linux.  But I can never figure out what's going on in your head.[/QUOTE]

Fedora is the base for Redhat Enterprise Linux, they don't promote Fedora as enterprise like they do with Ubuntu Dapper.
If you want to compare the facilities Redhat gives over Ubuntu in corporate environments I think you'll quickly see who's best suited.

And then again, he could very well be a fan of Windows 95. That doesn't change the fact that the quality assurance that **should've** gone into Dapper never was done properly.

---

### Post by Anthem on 2006-05-29
[QUOTE=dvarsam]Conclusion: the installation of the "codecs" should be independent to the country which somebody selects...[/QUOTE]
Hey, the Ubuntu team has committed to releasing an all-Free distro.  Which means no MP3 support.  That's not an Ubuntu thing, it's a Free thing.  Fedora, Mandrake, Debian, and Suse do the same.

---

### Post by Anthem on 2006-05-29
--Double Post--

---

### Post by Anthem on 2006-05-29
[QUOTE=David Corrales]Fedora is the base for Redhat Enterprise Linux[/QUOTE]
Nope, it's too different codebases.  They use Fedora as a testbed, but it's a different codebase.

[QUOTE=David Corrales]And then again, he could very well be a fan of Windows 95. That doesn't change the fact that the quality assurance that **should've** gone into Dapper never was done properly.[/QUOTE]
You seem really emotionally invested in this.  Why is that?

---

### Post by David Corrales on 2006-05-29
[QUOTE=Anthem]Nope, it's too different codebases.  They use Fedora as a testbed, but it's a different codebase.

You seem really emotionally invested in this.  Why is that?[/QUOTE]

They do use Fedora as a testbed because quality needs proper testing. Packages that go into Redhat have been tested by the community and QA. The testing distro shouldn't be the enterprise one then.

Emotionally invested? nah, I just happen to like Ubuntu but dislike people who blindly negate the truth in front of their eyes. Denial is a really bad way of facing things if you want them to improve.

---

### Post by Lovechild on 2006-05-30
[QUOTE=David Corrales]Fedora is the base for Redhat Enterprise Linux, they don't promote Fedora as enterprise like they do with Ubuntu Dapper.
If you want to compare the facilities Redhat gives over Ubuntu in corporate environments I think you'll quickly see who's best suited.

And then again, he could very well be a fan of Windows 95. That doesn't change the fact that the quality assurance that **should've** gone into Dapper never was done properly.[/QUOTE]

I actually really liked Windows 98SE, I found that one to be the best Windows release I had to use (I never ran Windows XP or 2000).

I run Fedora Development on my desktop, daily upgrades each more baby eating than the next, it doesn't mean I don't know how to make something stable. I happen to enjoy a bit of instability in my every day life - I'm that kind of a bugfiling sadist when it comes to my personal machine.

Fedora is definately not aimed at production deployment, you get 2 years of support (plus whatever Fedora Legacy provides) and the general state of the distro is decent however if I had to deploy a massive network with longterm support requirements I would use RHEL (or CentOS if I could live without Red Hat' excellent support channels).

RHEL is a product which is geared towards this kind of deployment, it is evident in the way it's developed. To turn a Fedora Core release into RHEL takes maybe a year of polishing, a year of not upgrading large portions of code, backporting important fixes. This is hard work.

---

### Post by Anthem on 2006-05-30
[QUOTE=David Corrales]The testing distro shouldn't be the enterprise one then.[/quote]
See, that's where we disagree.  That's why I stopped using Fedora, actually.  I'm not interested in being somebody else's beta tester.  If I'm going to be a beta tester, it will be for myself.  If you're going to force me to beta-test stuff I don't want but you need in your enterprise product, I'm going to go somewhere else.

> I just happen to like Ubuntu but dislike people who blindly negate the truth in front of their eyes. Denial is a really bad way of facing things if you want them to improve.
Well, if you want something to improve, I recommend staying away from message boards on the internet.  They're notorious for not getting stuff to improve.  :)

I don't see anybody "blindly negating the truth in front of them."  I see a lot of people who acknowlege that every bug hasn't been stamped out, but think the distro is ready to ship nonetheless.

---

### Post by Anthem on 2006-05-30
[QUOTE=Lovechild]I actually really liked Windows 98SE, I found that one to be the best Windows release I had to use (I never ran Windows XP or 2000).[/quote]
Agreed.  If Microsoft hadn't EOL'd it, nobody would have ever moved away from it.  I'm continually shocked by how many people stil use it.

Just for fun, I might install CentOS on this laptop to see how it goes.  If it doesn't recognize my wireless card, do I get to declare that it's not "enterprise ready?"

---

### Post by David Corrales on 2006-05-30
[QUOTE=Anthem]See, that's where we disagree.  That's why I stopped using Fedora, actually.  I'm not interested in being somebody else's beta tester.  If I'm going to be a beta tester, it will be for myself.  If you're going to force me to beta-test stuff I don't want but you need in your enterprise product, I'm going to go somewhere else.

Well, if you want something to improve, I recommend staying away from message boards on the internet.  They're notorious for not getting stuff to improve.  :)

I don't see anybody "blindly negating the truth in front of them."  I see a lot of people who acknowlege that every bug hasn't been stamped out, but think the distro is ready to ship nonetheless.[/QUOTE]

The only way you'll test stuff for yourself is if you build it yourself. You're still testing stuff for the Ubuntu guys and a lot of that stuff you don't need.

I agree that getting things moving in forums is not the most productive channel, but I find that it's important for people to understand that you don't have to be always positive to support something.
If there's things you think are being counterproductive, go ahead and make your point. I do think that this distro is not even close to being called "enterprise ready" and I'm giving out my reasons as why I think that. Hopefully, others will see this "alternate stream of thinking" and reevaluate their standing for the greater good.

And I have seen tons of people saying "It's ready, stop whining", "It's ready, just not for everyone", "If you don't like it, use something else". Is that going to make the troubles go away? doubt it. You can keep saying it's ready all you want, but realistically, it's not even desktop stable for a lot of people.

---

### Post by Anthem on 2006-05-30
[QUOTE=Lovechild]Back on ignore you go troll[/QUOTE]
Back on ignore?  Meaning I was there once before?  Interesting.

Well, I must say that wasn't the reaction I was expecting.  I'm not sure what about my post was "troll-like" but you are, of course, more than entitled to both your opinion and your right not to read my posts.  Seems unfair, though, since I read all of yours.

I won't bother responding to the rest of your post since you won't read it.  But accusing Ubuntu of proprietary lock-in... that's rich.

---

### Post by joepotter on 2006-05-30
[QUOTE=David Corrales]Fedora is the base for Redhat Enterprise Linux, they don't promote Fedora as enterprise like they do with Ubuntu Dapper.
If you want to compare the facilities Redhat gives over Ubuntu in corporate environments I think you'll quickly see who's best suited.

And then again, he could very well be a fan of Windows 95. That doesn't change the fact that the quality assurance that **should've** gone into Dapper never was done properly.[/QUOTE]
Great point you have.

In Red Hat we see a mature corporate release. They use Fedora to test ideas and software to improve the money maker release which has its own testing to boot.

In Debian we see 4 branches. We have experimental, Sid, testing (Etch at the moment), and finally the stable release. 

In Ubuntu we have two branches. We have only experimental and release. The development branch (Dapper just now) is always experimental and the developers are too young and reckless to refrain from making major changes with only a short time to go before release. They will mature over time we hope.

This means we get official warnings to the community *not* to use the development branch as your main desktop as it is too unstable. This cuts down on the number of people testing, and the number of different types of equipment tested. Imagine, it is not as reliable as Sid!

All in all, Dapper turned out the way I predicted because that is the only way Ubuntu can work with this current development model. We did get a short extension this cycle to fix bugs, but did anyone really think a few weeks was all that was necessary? All in all, Dapper will be polished up *after* release because that is the way our development model works. At release the developers stop adding new bugs and allow the community to start fixing the remaining bugs.

All the above is opinion; and yes your opinions are worth at least as much as mine. :-)

---

### Post by pope on 2006-05-30
[QUOTE=David Corrales]I agree with you Lovechild but I think he was trying to convey the idea that with good IT support staff, it's ok to have a really buggy desktop installation.
Try to manage 300 dapper desktops full of bugs. Just give it some **deep** thought and you'll see why some of us here would've liked another kind of decision taking in regards to quality.
In big enterprises there's patching policies, testing and QA. You can't expect that a company will be rolling 100mbs of patches every 2 days for every single desktop.[/QUOTE]

Ok, I understand your point!

IF this is the case, then Ubuntu should focus on Releasing "Dapper", but stick to Desktop use for now...
Then they can go on & release the "Corporate/Enterprise" Edition maybe on the coming October, when they will have the "Edge" project finished...

But you must understand that they are releasing the LTS (long time support) to earn some money... And money has to come from Big Corporate Companies...
That is why they care so much to promote the "Enterprise" Edition.

I do NOT blame them, because they must make some money in order to further fund/improve their projects...

At the same time, I think that 5 years of LTS is too much, they should stick to 3 years (same as the Desktop). With the fast progress of Linux & Ubuntu, 5 years seem too long... nobody will want to use "Dapper Enterprise" in 4 years from now...
People will want to use newer versions on the coming days...


A message from the Pope:
---------------------------------
Dear Beloved believers of Ubuntu,

I understand your concerns about the Dapper release...

In the Vatican, when we heard about the Book of Dan Brown - "The Da Vinci Code" - everybody was very angry with the author Dan Brown...:twisted: 
Catholic Fanatics wanted his head on a "silver" plate...

As time went by, things went smoother, the Vatican finally decided NOT to burn all the Movie Theaters around the Globe & many people went to see the movie in the Movie Theaters...:)

The Vatican, to soft things out, has _only_ decided to bann the Movie from the "Academy Award Nominnees" - The "known" Oscars...

To conclude, all this "chaos" created a very nice advertisement campaign for the book...
As a result, Dan Brown decided to offer 10% of the Movie Profits to our "Don Corleone" (sorry, I meant the Vatican) Family...

All the Vatican Family now is safe & happy,8)

At the same time, since Dan Brown made this generous 10% profit offer to the Vatican, the Vatican Family is willing to select/decide on 1 of the following choices:

1. Create a Statue of Dan Brown (from Marble) & place in the square of St. Peter

2. Proclaim Dan Brown as "Saint" (of course after death)

3. Print on the Vatican's biggest Paper Bill/Currency, Dan Brown's figure. 

To decide which of the 3 above options to follow, a vote is going to take place on this Thursday, right after the Realease of the Dapper!!! :D 
Right now, we are all praying so "God enlightens us to make the right decision"... 


Same case is happening now to the Ubuntu Family...!!!

The Globe wants to "crucify" the Dapper...

Let the Dapper come out & we will see how it goes from there...

In the mean time, to get a "taste" of the coming release, visit your nearest BK (Burger King) & ask for the "Big Wh(D)opper" (pronounced with a sillent "D")!!!:-D

Love,

The Pope
(Live from the Vatican)

---

### Post by MaX on 2006-05-30
[QUOTE=Anthem]Back on ignore?  Meaning I was there once before?  Interesting.

Well, I must say that wasn't the reaction I was expecting.  I'm not sure what about my post was "troll-like" but you are, of course, more than entitled to both your opinion and your right not to read my posts.  Seems unfair, though, since I read all of yours.

I won't bother responding to the rest of your post since you won't read it.  But accusing Ubuntu of proprietary lock-in... that's rich.[/QUOTE]

I've searched 3 pages back now, and nowhere can I find Lovechild saying you're on ignore.

I've seen Lovechild on forums since he used Gentoo and I usualy think he has good points. Redhat has a model that is proven to work and there are some issues with doing a release this way (dapper), maybe dapper should have been in feature freeze for the last three months instead of adding features until the very end.

I think Ubuntu has shown that they cannot do a reliable release, just look at the no-ubuntu-spatial option they had to put in.

---

### Post by Gustav on 2006-05-30
[QUOTE=MaX]I've searched 3 pages back now, and nowhere can I find Lovechild saying you're on ignore.

I've seen Lovechild on forums since he used Gentoo and I usualy think he has good points. Redhat has a model that is proven to work and there are some issues with doing a release this way (dapper), maybe dapper should have been in feature freeze for the last three months instead of adding features until the very end.

I think Ubuntu has shown that they cannot do a reliable release, just look at the no-ubuntu-spatial option they had to put in.[/QUOTE]
It's in jail [http://ubuntuforums.org/showthread.php?t=184485](http://ubuntuforums.org/showthread.php?t=184485)

---

### Post by MaX on 2006-05-30
[QUOTE=Gustav]It's in jail [http://ubuntuforums.org/showthread.php?t=184485](http://ubuntuforums.org/showthread.php?t=184485)[/QUOTE]

Ah, that would be the reason then. The post was kind of hard.  I wouldn't trade in a debian based distro for an rpm-one ever but I have a feeling I'll have to take the train 420Km home again for this release since everything has changed since breezy.

The change to breezy really messed up nautilus and now they've changed it again. When they do these kind of changes it would be nice for an explanatory gui to come up and give the user a choice.

I'll probably tell my parents and friends who use Ubuntu to wait with the upgrade until October when all the release kinks are fixed.

---

### Post by Anthem on 2006-05-30
[QUOTE=MaX]I think Ubuntu has shown that they cannot do a reliable release[/QUOTE]
Sorry, I'm not willing to concede that.  I've been using Linux for 5 years now, and Dapper is, by far, the most reliable cutting-edge release I've used.  And I've used all of the Fedoras (except 5), all of the Suse releases since 9.0 (never tried 10.0 or 10.1, since I fell in love with apt-get), several mandrakes, and misc releases like VectorLinux and whatnot.

I've been running Ubuntu on the same laptop without a reinstall since January.  It's only crashed on me once, and the only time updates broke my system was when I was screwing with XGL/compiz.

I've used all of the Ubuntu releases, and Dapper's the best one yet.  It's not perfect, but it's certainly not fatally flawed like some on here claim.

---

### Post by David Corrales on 2006-05-30
Anthem, you seem to keep missing the point. It's not fatally flawed for the regular desktop. In fact, it's the only distro I use on my laptop despite it's problems. I **love** the debian base opposed to an RPM base like Fedora/Suse/Mandrake.

For the enterprise-wide deployment, it's another story. The system still feels in beta stages in several aspects which are critical.
Say printing for example, it's been a headache for lots of people in the last few weeks. Imagine deploying Ubuntu for a small number of machines, say 30. Finding out no one can print and losing a couple days of productivity.

About the Oracle backing of Ubuntu. I think it's great! It's cool to see another distro get a shot in the enterprise market, but again, if you can't deliver what you promise you'll end up worse than you began. Remember people easily forget when you make delays in developing time -if you provide a solid product- (for example, Blizzard Entertainment games) but they **always** remember those ugly and crude first impressions (Windows ME).

---

### Post by garyng on 2006-05-30
[QUOTE=Anthem]I've been using Linux for 5 years now, and Dapper is, by far, the most reliable cutting-edge release I've used[/QUOTE]

For large scale deployment, no surprise is much more important than cutting edge. IT support stuff is more comfortable with knowing what doesn't work than what may pop up tomorrow. Ubuntu, with its aggressive schedule is designed to surprise people.

---

### Post by David Corrales on 2006-05-30
To Pope and Joepotter. Yeah, the problem is pretty much the kind of release cycle used for Dapper.
It'd be a lot better if they still release Dapper right now in June -but- don't go LTS yet. Instead, freeze the Edgy release, debug Dapper thinking about doing a LTS release in december and polish it up. That way you supply the desktop people with a newer desktop (and comply with the release cycle) but you also end up having a better enterprise release based on Dapper. Freezing Edgy sounds like a good trade-off to have 6 months more of pure developer time on Dapper.

---

### Post by Anthem on 2006-05-30
[QUOTE=David Corrales]It'd be a lot better if they still release Dapper right now in June -but- don't go LTS yet. Instead, freeze the Edgy release, debug Dapper thinking about doing a LTS release in december and polish it up. That way you supply the desktop people with a newer desktop (and comply with the release cycle) but you also end up having a better enterprise release based on Dapper. Freezing Edgy sounds like a good trade-off to have 6 months more of pure developer time on Dapper.[/QUOTE]
What makes you think they won't do that?  Mark has said there are two teams getting ready to launch Ubuntu services&support.  Why does everyone believe they're going to start rolling out mission-critical desktops on Thursday?

---

### Post by joepotter on 2006-05-30
[QUOTE=David Corrales]To Pope and Joepotter. Yeah, the problem is pretty much the kind of release cycle used for Dapper.
It'd be a lot better if they still release Dapper right now in June -but- don't go LTS yet. Instead, freeze the Edgy release, debug Dapper thinking about doing a LTS release in december and polish it up. That way you supply the desktop people with a newer desktop (and comply with the release cycle) but you also end up having a better enterprise release based on Dapper. Freezing Edgy sounds like a good trade-off to have 6 months more of pure developer time on Dapper.[/QUOTE]


Yes, I think you are correct in your assesment.  At this point it would be a good idea for Mark S. to think about doing that.

However, I still think the basic development model will always yield these sorts of results. We go from sorta-like--sid to semi-stable release. I thought the whole original idea was to be a "better" Debian. One that released on a regular schedule -- no one mentioned that we would never see a polished release.  

I think we need three lines. The sid-like experimental, the testing for polishing, and the very stable release. How can we do that if we release a new stable every 6 months? You may **not** put anything new into testing; the 6 months are for bug killing. You put the new stuff in the sid-like branch.

Ubuntu does not have to shy away from that model simply because Debian does it. They will not sue us! :-)

---

### Post by David Corrales on 2006-05-30
[QUOTE=Anthem]What makes you think they won't do that?  Mark has said there are two teams getting ready to launch Ubuntu services&support.  Why does everyone believe they're going to start rolling out mission-critical desktops on Thursday?[/QUOTE]

Justifying half broken promises, bad quality processes and poor decision making is **not** going to help Ubuntu.
Sure they can get it right... after who knows how many months. Image is a big asset for companies.

---

### Post by dvarsam on 2006-05-31
[QUOTE=David Corrales]Justifying half broken promises, bad quality processes and poor decision making is **not** going to help Ubuntu.
Sure they can get it right... after who knows how many months. Image is a big asset for companies.[/QUOTE]

Facts:
-----
1. Image is nice.
2. To build an Image, you first need a GOOD Product.
3. When you have finally built the GOOD Product, you can easily now build the Image.
4. Building the Image is consequently easier than to build the Product (if People are happy with the Product, Image - in most cases - will also be good).

Problems:
--------
1. The People's expectations for your _NEXT_ Product, will become higher.
2. This means that it is HARDER to meet those Expectations (especially if you are _NOT_ making any money - like the Ubuntu's "Dapper").
3. In ALL cases, it is impossible to meet ALL People's Expectations.

Conclusion:
----------
1. If you take into consideration ALL people's Expectations/Opinions, STOP producing ANY Product, cause NONE of your Products will EVER Meet ALL Peoples Expectations...
2. EVEN if you were making a Product for the Money (as M$ does), NO matter how hard you have been working to create the BEST Product, People would STILL be NOT happy with your Product (NO matter how GOOD your product in fact is) - _Note_: People are unhappy with Windows, no matter what... & Ubuntu, even though it is better than Windows in many Fields/Aspects, in many other Fields it is "lacking" in BIG quantities...
3. The hardest part, is to FINALLY decide which People's Expectations/Opinions you should start taking into consideration. Your EARS must Screen Out some of the "Wrong signals" & ONLY let the "True signals" go through (Keep in Mind that MOST of the "Signals" you will Hear want you to FAIL than to SUCCEED, so you better HAVE a GOOD "Screening" Proccess).
4. IF your "Screening" Proccess worked correctly, you should then work on IMPROVING what the "True signals" are looking for...
5. Finally, if you are REALLY "Lucky" & you have finally MET those Expectations, this is because you have GOOD f*cking EARS & a GREATER Programming Team that helped you MEET those Expectations. NEVER _EVER_ forget the Programming TEAM involved that created YOUR Product, cause that was ALL you had in the first place, wasn't it? AND it is THOSE People that CREATED the Product & gave it THIS _ENORMOUS_ RECOGNITION... (...cause IF my EYES are correct 100,000 people/members are disgussing about the pros & cons of this _NEW_ Product...). Do NOT forget to HONOR those People & Give/Pay Tribute!!!...

Farewell:
-------
So, my DEAR Ubuntu,
you have only got 1 DAY to go...
I wish you GOOD Luck & A GOOD & Successfull Launch!!!
(It sounds like a NASA Space launch, but it "almost" IS!...)

Thanks for ALL you have offered & the latter to come...

dvarsam

P.S.> Why don't you ALL go ahead & wish our NEW OS some good Luck!
        We will NEED it anyway!

---

### Post by joepotter on 2006-05-31
[QUOTE=dvarsam]
...
1. The People's expectations for your _NEXT_ Product, will become higher.
...[/QUOTE]

The people's higher expectations might just have been caused by Mark S. & crowd telling us this one was an "Enterprise ready" release. The first "real release" as some said on these very forums.

Miss that did you?

---

### Post by flyingbrass on 2006-05-31
Commitments have been made.  Dapper will release on schedule as it should.

From what I've experienced and read, Dapper is fine for the desktop, but I wouldn't trust it in a mission critical environment.  For that, if using a Debian system, I'd go with Sarge.  How could Ubuntu expect to accomplish in 6, no 7, months what took the whole Debian team much longer to get done?

I've used Ubuntu since before Warty was released.  I didn't pay attention to what was going on before Warty or Hoary became final.  I did pay some attention to the posts here when Breezy was nearing final.  I didn't and still don't understand why such major hacking would be going on so close to the final release.

Now I see the same situation with Dapper.  Ubuntu's schedule strikes me as either a joke or an advertising gimmick.  Why not say up front that version x will be continually hacked, as in new stuff put in, broken, fixed, etc. until the timer runs out for final release, and even more frantically so in the last moments until the buzzer rings?  That's what happens.  Why pretend to have a "release candidate"?  Even if they had one, what good does cranking it out a mere 7 days before the proposed release actually accomplish as far as discovering and mashing bugs?

I'm not a developer, so maybe I'm missing something.

I like Ubuntu.  It suits my needs, but any hype about Dapper being enterprise ready is a joke.

---

### Post by hesser on 2006-05-31
I believe that since Sunday the updates were rather minor. Does some have a list of major outstanding bugs? I relly do not have any issues.

Thanks

---

### Post by rcarring on 2006-05-31
Let's look at some key issues here:

Any live distro worth its salt is going to have to provide the following:

Boot the system without crashing or hanging
Once the system is booted, identify hardware present without crashing or hanging -- hardware that is not understood should be ignored and a notice provided to the user when the system finally boots to the desktop
Boot to gui automatically and thereby identify the video adapter, using vesa 3 or vga compat if the card is unknown
Correctly load network drivers
Correctly load sound drivers
Correctly load usb drivers

Once the desktop is loaded, user should be able to run applications without waiting half an hour for them to load.

Open a default webpage with a readme / how to in it.

----

For the enterprise side of things, Ubuntu might consider building a special version for a corporate if a corporate wants to install it on 20000 desktops after evaluation. This was certainly the case for my old company I worked for and Windows NT.

---

### Post by Zodiac on 2006-05-31
I don't get it... 

Are the people who are saying that Ubuntu isn't ready, i.e. Lovechild (who really has been bashing Ubuntu from the moment he got on these forums) and David Corrales, implying that other distros do not have the exact same problems Ubuntu has?

---

### Post by Rackerz on 2006-05-31
All Distro's have there own problems, nothing is perfect. I for one think Dapper is ready, I can't say it's enterprise ready because I wouldn't be using it for that purpose. But from a desktop user view, it's ready.

---

### Post by rcarring on 2006-05-31
I think some users are partisan about the favorite operating system. There will be people who are primarily Windows or Mac OSX users who will look at Linux from that perspective. 

I use Windows XP as my host system, because the software I run and things I do on my laptop require me to use Windows XP.

One day, the penny will drop -- software drives the OS not the other way around =D

---

### Post by joepotter on 2006-05-31
[QUOTE=flyingbrass]Commitments have been made.  Dapper will release on schedule as it should.

From what I've experienced and read, Dapper is fine for the desktop, but I wouldn't trust it in a mission critical environment.  For that, if using a Debian system, I'd go with Sarge.  How could Ubuntu expect to accomplish in 6, no 7, months what took the whole Debian team much longer to get done?

I've used Ubuntu since before Warty was released.  I didn't pay attention to what was going on before Warty or Hoary became final.  I did pay some attention to the posts here when Breezy was nearing final.  I didn't and still don't understand why such major hacking would be going on so close to the final release.

Now I see the same situation with Dapper.  Ubuntu's schedule strikes me as either a joke or an advertising gimmick.  Why not say up front that version x will be continually hacked, as in new stuff put in, broken, fixed, etc. until the timer runs out for final release, and even more frantically so in the last moments until the buzzer rings?  That's what happens.  Why pretend to have a "release candidate"?  Even if they had one, what good does cranking it out a mere 7 days before the proposed release actually accomplish as far as discovering and mashing bugs?

I'm not a developer, so maybe I'm missing something.

I like Ubuntu.  It suits my needs, but any hype about Dapper being enterprise ready is a joke.[/QUOTE]

Well put; much better than I could have.

The thing is; I think it will always be exactly like this because of the development cycle and the maturity level of the development team. So, just figure that a given release is really the first RC candidate. Ubuntu will then release fixes over time and 3 months or so later the release works well.

I think this means Breezy plus backports works better than Dapper just now and will do so for some time.

Just an opinion.

---

### Post by henriquemaia on 2006-05-31
For me is ready. It has surpassed most of my expectations for this new release.

---

### Post by Anthem on 2006-05-31
[QUOTE=rcarring]Let's look at some key issues here:

Any live distro worth its salt is going to have to provide the following:

Boot the system without crashing or hanging
Once the system is booted, identify hardware present without crashing or hanging -- hardware that is not understood should be ignored and a notice provided to the user when the system finally boots to the desktop
Boot to gui automatically and thereby identify the video adapter, using vesa 3 or vga compat if the card is unknown
Correctly load network drivers
Correctly load sound drivers
Correctly load usb drivers

Once the desktop is loaded, user should be able to run applications without waiting half an hour for them to load.

Open a default webpage with a readme / how to in it.[/QUOTE]
Yup, agreed.  Ubuntu does all of these things extremely well, but in addition is rock solid, easy to use, pretty, cutting-edge, and easy to administer.

Works for me!

---

### Post by garyng on 2006-05-31
[QUOTE=Anthem]Yup, agreed.  Ubuntu does all of these things extremely well, but in addition is rock solid, easy to use, pretty, cutting-edge, and easy to administer.

Works for me![/QUOTE]

I am afraid the catch phrase is "works for you". To be enterprise ready, it needs to work for most people and with predictive result. Even XP can't claim that after 5 years, ubuntu with its 6 month scehdule will never be able to do that.

---

### Post by Terracotta on 2006-05-31
I'm affraid that it does work for most people, on these forums you only see the worst case scenarios, most people just use it. I've installed it on several pc's and didn't find problems. Besides what's the problem with it being completely stable after three months? Most people don't install a new OS every six months, most certainly enterprises don't. They just do security updates, so if you can say after three monts release and you have a rock solid OS it is still great.

PS: dapper is already solid for quite some time now.

---

### Post by garyng on 2006-05-31
[QUOTE=Terracotta]I'm affraid that it does work for most people, on these forums you only see the worst case scenarios, most people just use it. [/QUOTE]

You mean for most people on this forum who are early adaptors ? Try to put it in the hand of those who go through some short term computer course and work as  sys admin. 

I believe the guys behind ubuntu underestimate the task of making an enterprise ready OS. I would say that even just using Breezy as the base without adding any new thing, 6 months may still not enough to polish it.

---

### Post by topgi on 2006-05-31
Guys, just look to what M$ does. They release buggy operative system and then fix overtime. Windows XP wasn't really stable until the service pack 2. 
I bought a IPAQ 1950rx with windows mobile 5, I have to reset 3-4 times a day and after 3 month after release M$ relased the first update.  But now no more update and I keep doing reset.
This never happen to me with Dapper since 1 month and I keep installing and playing with many software.

Let's the show begin.......

Good Luck DAPPER

---

### Post by garyng on 2006-05-31
[QUOTE=topgi]Guys, just look to what M$ does. They release buggy operative system and then fix overtime. Windows XP wasn't really stable until the service pack 2. 
I bought a IPAQ 1950rx with windows mobile 5, I have to reset 3-4 times a day and after 3 month after release M$ relased the first update.  But now no more update and I keep doing reset.
This never happen to me with Dapper since 1 month and I keep installing and playing with many software.

Let's the show begin.......

Good Luck DAPPER[/QUOTE]

MS can do that because initially, there was no competition(or the competition was even worse, not necessary for technical reasons as I consider OS/2, DR GEM better). Then they claimed the monopoly position and can continue to do it this way, as bad as it was/is(where it is still much better than all the linux I have tried), people are stuck with the only choice. New comers like ubuntu don't have that luxury. How many linux distro have tried and gave up ?

---

### Post by Gtaylor on 2006-05-31
I think they're saying that upgrades from Dapper forward should be a bit smoother. The first few releases were amidst major reorganizations and serious low level changes that made sweeping changes beneath the hood from version to version. Not all of these transitions happened cleanly on some setups, particularly when the users had to modify some of the configuration files.

---

### Post by Anthem on 2006-05-31
[QUOTE=garyng]To be enterprise ready, it needs to work for most people and with predictive result.[/QUOTE]
Well then by your very definition, it's enterprise ready.  Right now, it works for most people and "with predictive result."

---

### Post by garyng on 2006-05-31
[QUOTE=Anthem]Well then by your very definition, it's enterprise ready.  Right now, it works for most people and "with predictive result."[/QUOTE]

depends on your definition of "most people" which is pointless to argue. All I can say is, I run it as my secondary OS(well primary linux desktop) under XP but if I want to do mass deployment(i.e. beyond my own use), I won't consider using it but rather would go for the outdated debian sarge.

---

### Post by henriquemaia on 2006-05-31
I think it is rather diffiicult to say bluntely: «It is ready» or «It is not ready».

Only when It hits public attention one will get the real scenario. These forums are not a very reliable «case study». Just a thought.

---

### Post by tribaal on 2006-05-31
It definately feels like new years eve...

Happy Dapper Drake everyone! ;)

- trib'

---

### Post by henriquemaia on 2006-05-31
[quote=tribaal]It definately feels like new years eve...

Happy Dapper Drake everyone! ;)

- trib'[/quote]

Yes, right. We get all excited for something we already know how it is going to be. :)

---

### Post by Anthem on 2006-05-31
[QUOTE=garyng]All I can say is . . . if I want to do mass deployment(i.e. beyond my own use), I won't consider using it but rather would go for the outdated debian sarge.[/QUOTE]
Well that's fair.  I wouldn't want to do a mass deployment either... Ubuntu lacks tools for things like centralized patch management and mass customization, and those things are necessary in a large-scale rollout.  I wouldn't consider Sarge either, I'd probably go with Novell Linux Desktop.

It doesn't matter if they promise 10-year support; nobody's going to do a mass rollout of a FOSS product in a place with mission-critical desktops unless there's a support contract associated with it.  In enterprise space, Linux lives on programmer's workstations and on call centers or computers that don't require much besides a web browser.

They're not calling it "Ubuntu Enterprise," they're calling it "Ubuntu LTS."  Long-term support.  I still haven't figured out why this bothers so many people.  It's just like all the other releases, but better.

---

### Post by henriquemaia on 2006-05-31
I'm a **Ubuntu 6.06 User** as you can see on the side bar!

:D

---

### Post by awaldram on 2006-05-31
I can predict that anyone with an orinoco/prism wireless card cant get wpa working (orinoco driver doesn't support wpa) 

I can predict that pism54 v2 users 3com and netgear cant get wpa working (islsm beta sofware no wpa)

Both chipsets capable of doing wpa with the correct drivers hostap /prism54 

as these are the 2 most common chipsets the've just broke 50% of their wireles market.

But it gets worse the backports have remapped wlan to eth this has broke wpa_supplicant wep support for all such type cards.

These are problems that corperations will not put up with they will not even look at it.

Then of course theres the shutdown problems , printing problem, dvd problem and suspend hibernate all issues caused by kid in a candy store syndrome (what can we fit in before release).

I am not complaining I love it having run linux since .99 kernels this is going to be the best desktop linux ever, but lets keep our feet on the ground it aint enterprise and is bearly server ready.

you don't run kernels in such a hybrid state on servers unless you want trouble.

hence my server runs debian stable never switches off and has only ever been rebooted to upgrade hardware .

Tarl (my server) started life march 1998 now thats stable.

---

### Post by David Corrales on 2006-05-31
[QUOTE=Zodiac]I don't get it... 

Are the people who are saying that Ubuntu isn't ready, i.e. Lovechild (who really has been bashing Ubuntu from the moment he got on these forums) and David Corrales, implying that other distros do not have the exact same problems Ubuntu has?[/QUOTE]

I'm not saying other distros don't have their issues. But the other companies are smart enough to know that a 6 month cycle is not near enough if you want a solid product to be deployed company-wide.
Mandrake and Suse have desktop editions, so does Redhat for example. When you check what they have you'll probably go "yuck, this is all outdated stuff". That's because it had it's proper testing and debugging.
Ubuntu is *ok* for desktops... for any sane company, it's not going to be stable for a long while.

---

### Post by David Corrales on 2006-05-31
[QUOTE=awaldram]I can predict that anyone with an orinoco/prism wireless card cant get wpa working (orinoco driver doesn't support wpa) 

I can predict that pism54 v2 users 3com and netgear cant get wpa working (islsm beta sofware no wpa)

Both chipsets capable of doing wpa with the correct drivers hostap /prism54 

as these are the 2 most common chipsets the've just broke 50% of their wireles market.

But it gets worse the backports have remapped wlan to eth this has broke wpa_supplicant wep support for all such type cards.

These are problems that corperations will not put up with they will not even look at it.

Then of course theres the shutdown problems , printing problem, dvd problem and suspend hibernate all issues caused by kid in a candy store syndrome (what can we fit in before release).

I am not complaining I love it having run linux since .99 kernels this is going to be the best desktop linux ever, but lets keep our feet on the ground it aint enterprise and is bearly server ready.

you don't run kernels in such a hybrid state on servers unless you want trouble.

hence my server runs debian stable never switches off and has only ever been rebooted to upgrade hardware .

Tarl (my server) started life march 1998 now thats stable.[/QUOTE]

That's exactly the kind of issues I'm talking about when I say Ubuntu shouldn't have been called "enterprise ready".

For example, the whole network manager thing. Advertised on the release notes. Not working for some, others have to comment lines in **/etc/interfaces**. I mean, what the hell are they thinking? isn't this supposed to be for regular users? Sending people to a command line, has a 95% possibility of just causing the user to go: "bah, I've no time for this. Too complicated" and ditch Ubuntu.
This example will probably get replies like: "Oh, he shouldn't be using Linux then!" "If you're smart enough to use a computer, why can't you do that little bit". If you think like this, pat yourself on the back, because you're causing linux to stay underground forever.

Anthem, before you troll... read [http://www.desktoplinux.com/news/NS4283763735.html](http://www.desktoplinux.com/news/NS4283763735.html) if you're not concerned that people actually do think Ubuntu is enterprise stable, I've not much else to say :-k

---

### Post by newbie2 on 2006-05-31
how come that firefox 1.5.0.3 is in 6.06-rc(2006/05/25) and not in (later 2006/05/31)snapshot ?
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)
:-?

---

### Post by aysiu on 2006-05-31
[quote=David Corrales]That's exactly the kind of issues I'm talking about when I say Ubuntu shouldn't have been called "enterprise ready".

For example, the whole network manager thing. Advertised on the release notes. Not working for some, others have to comment lines in /etc/interfaces. I mean, what the hell are they thinking? isn't this supposed to be for regular users?[/quote] There are two separate issues here--"Enterprise Ready" and "regular users"--you're talking about.

In the "Enterprise" (businesses, etc.) there is something called a technology department. Any business that is willing to adopt a Linux distribution for desktop use will hire an IT staff (or Canonical itself) to support the migration.

What does editing lines in the /etc/interfaces have to do with "Enterprise"? If you can't hire IT staff to edit lines in a config file, then that's sad. I'm no IT person, but I can edit a file. What's so hard about that?

Any business that asks its regular employees (not IT) to configure networks has other things to worry about than migration!

---

### Post by Rackerz on 2006-05-31
[QUOTE=newbie2]how come that firefox 1.5.0.3 is in 6.06-rc(2006/05/25) and not in (later 2006/05/31)snapshot ?
[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)
:-?[/QUOTE]

I'm also wondering, I hope it comes with 1.5.0.3.

---

### Post by David Corrales on 2006-05-31
[QUOTE=aysiu]There are two separate issues here--"Enterprise Ready" and "regular users"--you're talking about.

In the "Enterprise" (businesses, etc.) there is something called a technology department. Any business that is willing to adopt a Linux distribution for desktop use will hire an IT staff (or Canonical itself) to support the migration.

What does editing lines in the /etc/interfaces have to do with "Enterprise"? If you can't hire IT staff to edit lines in a config file, then that's sad. I'm no IT person, but I can edit a file. What's so hard about that?

Any business that asks its regular employees (not IT) to configure networks has other things to worry about than migration![/QUOTE]

There's enough troubles to worry a migration staff. For example, the company has 200 laptops and surprise! half of them won't shutdown as it is, or suspend. My laptop used to suspend with Breezy (9/10 times), with Dapper it's worthless. Or half of them won't be able to use wireless! Yipee for lost productivity.

There's the SMP 686 kernel bug that causes extreme CPU utilization at idle in some laptops. So, if you recompile the kernel but want to upgrade it using the traditional methods you run into the possibility of hosing all machines again. Time = money.

Also, if Ubuntu has TONS of bug fixes and they're rolling all days (like those lovely Open Office patches that weight 100-120mb). The IT department you talk about won't be happy with testing ALL of them and deploying patches following decent policies to assure stability. It's not like you set updates on auto in every machine... that's asking for trouble. Especially when the distro is in the process of becoming stable.

About the interfaces file, I was referring to regular users. Stuff like networking has to work out of the box in 99% of the cases. And yes, that means all the wireless problems with WPA and network manager have to go. Sure, you can edit a file and probably recompile a kernel. Lots of us here can, we're *usually* a little more saavy than regular users when it comes to computer knowledge.
But if you plan to ask someone that only wants to be productive with it's computer without worrying about stuff like that, you're losing a **big** market share by denying that it's year 2006 and we shouldn't be editing text files to get -basic networking- up and running.

Finally, go ahead and edit 50 **/etc/interface** files counting that each modification won't be the same for each machine. Say, you take 5 minutes per machine, that's 4.2 hours you'll be wasting AND paying for something that should simply work.

Bottom line, you can't expect to be 100% perfect in a distro, but if you don't struggle to be the best you can and assume false premises (6 more weeks will go from very unstable to rock solid) you won't get a good product.
I just **heavily** disagree with Ubuntu being called "enterprise ready". It hurts more than it helps if people believe it.

---

### Post by aysiu on 2006-05-31
While I think your criticisms have some validity, "regular users" still have nothing to do with "enterprise ready."

And if Ubuntu doesn't recognize the wireless card in the 200 laptops you already have--guess what--no one's going to get Ubuntu. You don't think they'd at least try out the live CD on a few of those laptops before undertaking a migration?

Most likely, they would wait until their laptop lease cycle is over and then lease out new laptops that they're sure will work with Ubuntu. You don't buy an operating system and hope it'll work with your hardware. You make sure your hardware works with your software.

I'm an idiot if I buy a PowerPC and then expect Mepis to work on it. Or if I expect PlaysforSure software to work on a Mac.

Again, we should assume IT departments are not stupid.

As for regular users, they will **never** be installing an operating system anyway. I've configured a network in Windows, too--that's no easy task. Setting up a wireless router for our apartment (totally GUI in Windows) was also no easy task. I struggled to get that thing up--I think it took me at least an hour and a half to get everything satisfactorily working.

When a friend of ours came with his Windows 2000 laptop, he thought if he had the WEP key and the network name that's all he'd need. Guess what. He couldn't find a way to get the proper hexidecimal prompt for the password.

Normal people can't configure networks. I consider myself a little above average, and I still don't think I can confidentally say I can walk up to some computer and configure its networking--Windows, Mac, or Linux.

My wife's Powerbook's wireless networking is also a nightmare sometimes when it switches networks (when she goes between home and school). We couldn't get it to switch to the home network again. Turns out there was some weird bug where you had to give the network setup the wrong password, save out, and then try to give it the right password again.

If you really believe "regular users" set up networks, give my mom a home-made PC, a wireless adapter, a router, and a Windows CD... unless you're going to argue Windows too isn't "enterprise ready."

---

### Post by awaldram on 2006-05-31
Ok lets set the record straight.

I do run a it department for a large multi national (helping) run the largest single AD forest in the world so I know what enterprise means.

We lock our desktops (not Linux) so that users cannot make non approved changes.

We use a database driven package to deploy Apps to clients. 

and use Strings held in sysvol to trigger OS patching (after trickle feeding packages to clients.

even so a 100Mb patch is a real headache to deploy to approx 500,000 desktops (I told you it was large).

We expect less than 2% failure rate with these deploys.

SP2 took  nearly 9 months to test and deploy due to the large changes in the security systems having to be tested and approved.

Though I'm no MS lover I'm afraid Ubuntu (being best of breed on the desktop)  just could not handle this at all, it'd never get out of testing. (bear in mind we replace desktop/laptop approx every 3 years so every 6-9 months we have a raft of new models to contend with.

We do use Linux on the server side but wouldn't dream of using Ubuntu for the reason stated earlier

---

### Post by aysiu on 2006-05-31
[QUOTE=awaldram]
even so a 100Mb patch is a real headache to deploy to approx 500,000 desktops (I told you it was large).

We expect less than 2% failure rate with these deploys.

SP2 took  nearly 9 months to test and deploy due to the large changes in the security systems having to be tested and approved.

Though I'm no MS lover I'm afraid Ubuntu (being best of breed on the desktop)  just could not handle this at all[/QUOTE] Now, *that's* a legitimate gripe.

Thanks for setting the record straight with a really applicable example.

---

### Post by awaldram on 2006-05-31
aysiu;

Models are chosen by operating companies generaly on colour or street cred value.
I think you'll find this common in most multi faceted companies though generaly it'll be from 1 maybe 2 prefered suppliers.

As to whether uses set up networks I agree they just expect it to work .. Oh where have I heard that .... Network Manager "just works"!!!!!!!!!!

---

### Post by awaldram on 2006-05-31
Enough Griping

:KS Whoo hooo Dapper comming:KS 

< 3hours 

Long live edgy:twisted:

---

### Post by mips on 2006-05-31
[QUOTE=awaldram]Ok lets set the record straight.

I do run a it department for a large multi national (helping) run the largest single AD forest in the world so I know what enterprise means.

We lock our desktops (not Linux) so that users cannot make non approved changes.

We use a database driven package to deploy Apps to clients. 

and use Strings held in sysvol to trigger OS patching (after trickle feeding packages to clients.

even so a 100Mb patch is a real headache to deploy to approx 500,000 desktops (I told you it was large).

We expect less than 2% failure rate with these deploys.

SP2 took  nearly 9 months to test and deploy due to the large changes in the security systems having to be tested and approved.

Though I'm no MS lover I'm afraid Ubuntu (being best of breed on the desktop)  just could not handle this at all, it'd never get out of testing. (bear in mind we replace desktop/laptop approx every 3 years so every 6-9 months we have a raft of new models to contend with.

We do use Linux on the server side but wouldn't dream of using Ubuntu for the reason stated earlier[/QUOTE]

The company I worked for had a similair setup although i was not involved in it. I always wondered how one would accomplish the same thing with linux.

---

### Post by aysiu on 2006-05-31
[QUOTE=awaldram]
Models are chosen by operating companies generaly on colour or street cred value.
I think you'll find this common in most multi faceted companies though generaly it'll be from 1 maybe 2 prefered suppliers.[/quote] That's true, but (and you can correct me if I'm wrong on this) if a company is actively seeking to migrate to a new operating system, wouldn't they check with Dell, for example, to find a Dell model and accompanying parts that would work with that new operating system?

> 
As to whether uses set up networks I agree they just expect it to work .. Oh where have I heard that .... Network Manager "just works"!!!!!!!!!! My point was simply that I've found networking still beyond the grasp of even above-average users, regardless of operating system, even with a GUI for everything.

---

### Post by David Corrales on 2006-05-31
I have to agree with the fact that an IT department will of course try the distro before moving forward, but as Mark Shuttleworth stated:
> I, and others, would very much like Dapper to stand proud amongst the traditional enterprise Linux releases from Red Hat, Debian, and SUSE as an equal match on quality, support, and presentation
If you had a company that earns and spends hundreds of thousands of dollars, would you -today- invest in Ubuntu or Redhat enterprise?

Why are you justying things that **should** be better? I'm not here to drive Ubuntu people away lol. I'm here to state points that should be taken into account not only for opinions but also for decisions.
The goal is to have a better Ubuntu as days pass, but if people keep saying "well, that's ok" "I can live with that" "oh, they'll fix it... someday" you're not really motivating the people or developers to fix stuff that's in already and stop adding things until they have a solid base.

I do agree that a regular user wouldn't be able to make an iptables script and build his firewall. But why can't we make life easier for the new people? If you want to move people from Windows to Ubuntu, you gotta offer them more or else there's no point.
Networking isn't perfect in any os right now, why not push Ubuntu over the top instead of thinking about what other OS's can or can't do.

Say someone buys a laptop -right now- and it comes with XP preinstalled. You install Ubuntu and wireless doesn't work, suspend or shutdown either, you can't play videos or mp3's and that nice integrated webcam becomes useless. Would you as that user switch to Ubuntu? You want to get what you pay for, you'll switch if there's a benefit.
Having to read hours in the forums searching for answers for your specific device, maybe to find out that it doesn't work yet doesn't seem like a benefit... at all.
It's true that a -big- part of the problem is the hardware makers themselves. But in practice, wether that's fair or not doesn't concern most users. They go out, spend their money and they expect things to work. Right now I have to use Windows XP for example to do video conference with my sister because if I use linux it won't work. That's a desktop requirement there, not enterprise that still needs polish for example.

The mentality of trying to inyect knowledge into users when they don't want or have a need is not going to work. It's the ideal method, but real life doesn't work like that. Consoles are a BAD way to solve problems for casual users.

---

### Post by awaldram on 2006-05-31
Very simmlar

update provided using in house repositories (something along the line of debian security updates)

some kinda scripted wget *.deb /dpkg -i for app install

should sorta work

it's how I keep my debian server updated

---

### Post by thecityofgold2006 on 2006-05-31
The RC version of ubuntu is not ready for the general public. It does not 'do the right thing' even nearly every time.

I love ubuntu and has been using it for about 4 months as my primary desktop, however, even after 4 months of me playing with it (and I've used DOS, Windows extensively for 15years+) I cannot get some stuff to work. E.g. Epson Picturemate. The printing support overall, is awful.

As a test I tried to install the RC version on a PC I'd pulled out of my office.. It was all very shiny and installed quickly but the internet just did not work.. Not the right thing at all.

Ubuntu is fine for people with lots of time and some technical knowledge but it is definitely not ready for the general public with limited IT knowedge.

There was some talk of another delay. This would be a good thing. Ubuntu doesn't want to have it's image tarnished by shipping less than ready product.

---

### Post by David Corrales on 2006-05-31
[QUOTE=thecityofgold2006]The RC version of ubuntu is not ready for the general public. It does not 'do the right thing' even nearly every time.

I love ubuntu and has been using it for about 4 months as my primary desktop, however, even after 4 months of me playing with it (and I've used DOS, Windows extensively for 15years+) I cannot get some stuff to work. E.g. Epson Picturemate. The printing support overall, is awful.

As a test I tried to install the RC version on a PC I'd pulled out of my office.. It was all very shiny and installed quickly but the internet just did not work.. Not the right thing at all.

Ubuntu is fine for people with lots of time and some technical knowledge but it is definitely not ready for the general public with limited IT knowedge.

There was some talk of another delay. This would be a good thing. Ubuntu doesn't want to have it's image tarnished by shipping less than ready product.[/QUOTE]

Good thing to see I'm not alone amongst zealots.

---

### Post by awaldram on 2006-05-31
aysiu

A lot of companies even go so far as to insist the manafacturer does not change the model for a specific period (you have to be big to do this).

What generaly happens is that the company will agree 20,000 units to be supplied over a 3 year period with no hardware changes.

I've only seen it in the banking enviroment so don't know how wide spread this practice is but it'd suit Linux.

With windows Xp you can get away with any old rubish Hardware as the manafacturer will make sure it at least cosmeticaly funtions under this OS.

Things get a bit tougher under windows server OS's but microsoft has worked hard to standardise hardware api's so that if it works in XP (which it will (at least sort of)) it'll work on the server.

Linux is also goinf this way thats why stuff works cross kde/gnome etc initialy   it was hell to try and cross pollinate apps now its pretty easy.

It's tougher for Linux though as most hardware manafacturers don't give a stuff if it works in Linux (notable exeptions take a bow).

On the plus side if you get one chipset working in linux generaly all of the same will work. It always impressed people pulling my 3com pcmcia card out and pluging my netgear in and the connection stayed up. doing the same in Windows produced a beautiful blue screen irq<= .

---

### Post by aysiu on 2006-05-31
[QUOTE=David Corrales]
Say someone buys a laptop -right now- and it comes with XP preinstalled. You install Ubuntu and wireless doesn't work, suspend or shutdown either, you can't play videos or mp3's and that nice integrated webcam becomes useless. Would you as that user switch to Ubuntu? You want to get what you pay for, you'll switch if there's a benefit.[/QUOTE] While your scenario's quite typical, it's not really fair if you're judging the software, not the sociological circumstances.

Let's say someone buys a laptop from System 76, and it comes with Ubuntu preinstalled. You install Windows and wireless doesn't work, suspend or shutdown either. You can't play videos or DVDs. Would you as a Ubuntu user switch to Windows?

Recognize that even though your scenario is more common, your faulting Ubuntu for something even Windows can't do--work on every single piece of hardware available.

Call me a *zealot* if it makes you feel superior, but you are giving unfair comparisons.

As stated before, too, these "someones" who buy laptops have nothing to do with an operating system being "enterprise ready."

To awaldram, thanks for the further explanation. It is tough for businesses trying to switch to Linux for workstations, and you're spelling out some real obstacles.

---

### Post by garyng on 2006-05-31
[QUOTE=aysiu]
Let's say someone buys a laptop from System 76, and it comes with Ubuntu preinstalled. You install Windows and wireless doesn't work, suspend or shutdown either. You can't play videos or DVDs. Would you as a Ubuntu user switch to Windows?
[/QUOTE]

Except that the chance of such thing happen is very very very remote. BTW, fair or not is not the issue here, reality is. People don't love/hate OS(well most people don't), they just want something that can help them. So for typical business, it is cost saving(in whatever means, license, TCO, hardware etc). Ubuntu in its current state just can't meet that need.

---

### Post by awaldram on 2006-05-31
I Love Linux

---

### Post by David Corrales on 2006-05-31
[QUOTE=aysiu]While your scenario's quite typical, it's not really fair if you're judging the software, not the sociological circumstances.

Let's say someone buys a laptop from System 76, and it comes with Ubuntu preinstalled. You install Windows and wireless doesn't work, suspend or shutdown either. You can't play videos or DVDs. Would you as a Ubuntu user switch to Windows?

Recognize that even though your scenario is more common, your faulting Ubuntu for something even Windows can't do--work on every single piece of hardware available.

Call me a *zealot* if it makes you feel superior, but you are giving unfair comparisons.[/QUOTE]

Unfair? I'm being realistic. Hardware usually works this way: 
if it works for Windows, it -might- work for linux.
And if it does, it -might- implement all the features.
And if it does, it -might- have a nice GUI like Windows usually does.

Let's do this... name me 5 pieces of hardware that work out of the box for linux, implement drivers with -full- features and have a nice GUI to control them BUT they don't work at all or need editing weird files, recompiling stuff in Windows. I dare you, 5.

It's high improbable that a laptop which had Ubuntu working out flawless, if you switch it to Windows loses DVD, Wireless, mp3's and videos. It happens -today- with Ubuntu laptops.

> As stated before, too, these "someones" who buy laptops have nothing to do with an operating system being "enterprise ready."
So enterprises don't buy and use laptops?

> To awaldram, thanks for the further explanation. It is tough for businesses trying to switch to Linux for workstations, and you're spelling out some real obstacles.
He gave a good example of what I've been trying to state in all my posts.

---

### Post by aysiu on 2006-05-31
[QUOTE=garyng]Except that the chance of such thing happen is very very very remote.[/quote] Why is it remote? I've installed Windows twice from scratch, and it wasn't pretty either time. I didn't deliberately go out and find hardware that wasn't compatible--it's just very difficult if you don't happen to have the drivers around for your hardware. > BTW, fair or not is not the issue here, reality is. People don't love/hate OS(well most people don't), they just want something that can help them. So for typical business, it is cost saving(in whatever means, license, TCO, hardware etc). Ubuntu in its current state just can't meet that need. If you're criticizing software, you should look at the software, not circumstances.

If you're criticizing circumstances, don't look at Ubuntu.

It makes about as much sense as saying Spanish won't catch on as the national language in the United States because it's not good enough. Well, clearly it has nothing to do with how "good" the language is--most people in the United States are used to speaking English. It would be very difficult to move them to Spanish, and it has nothing to do with the quality of the Spanish or English languages.

Likewise, criticizing Ubuntu for not working in a common situation that has nothing to do with the quality of the Ubuntu software is stupid.

---

### Post by aysiu on 2006-05-31
[QUOTE=David Corrales]
Let's do this... name me 5 pieces of hardware that work out of the box for linux, implement drivers with -full- features and have a nice GUI to control them BUT they don't work at all or need editing weird files, recompiling stuff in Windows. I dare you, 5.[/quote] [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

> 
It's high improbable that a laptop which had Ubuntu working out flawless, if you switch it to Windows loses DVD, Wireless, mp3's and videos. It happens -today- with Ubuntu laptops. I see you've never installed Windows from scratch. Go ahead, install Windows from scratch and see if you can play DVDs.

> 
So enterprises don't buy and use laptops? If a company were to decide "We're moving to Ubuntu," they would have a plan to get hardware that works with Ubuntu. They would not just get 1000 copies of Ubuntu and install them on the computers they already have. If they did that, they would be idiots, as much as a company deciding to buy 1000 licenses for Adobe Creative Suite for Mac and then trying to install them on Windows XP computers.

---

### Post by awaldram on 2006-05-31
David Corrales

Matrox Marvel G200 Mjpeg capture

Matrox dropped support for it with the release of windows XP so this fits you catagory works in linux doesn't in windows.

I'll keep thinking

---

### Post by garyng on 2006-05-31
[QUOTE=aysiu]If you're criticizing software, you should look at the software, not circumstances.

If you're criticizing circumstances, don't look at Ubuntu.

It makes about as much sense as saying Spanish won't catch on as the national language in the United States because it's not good enough. Well, clearly it has nothing to do with how "good" the language is--most people in the United States are used to speaking English. It would be very difficult to move them to Spanish, and it has nothing to do with the quality of the Spanish or English languages.

Likewise, criticizing Ubuntu for not working in a common situation that has nothing to do with the quality of the Ubuntu software is stupid.[/QUOTE]
Huh ? I lose you.

---

### Post by rcarring on 2006-05-31
DVDs require a decompression codec. 

On a Dell laptop I once owned, Dell refused to send me the codec and I had to buy it from intervideo instead -- that was just the dvdxpak that lets WMP play DVDs.

XP does not and will not natively support DVD playback without the codec installed.

---

### Post by Anthem on 2006-05-31
[QUOTE=awaldram]We do use Linux on the server side but wouldn't dream of using Ubuntu for the reason stated earlier[/QUOTE]
Right, I absolutely agree.  And that's not Ubuntu's target audience (right now, at least).

---

### Post by andrewabc on 2006-05-31
They should put this release on hold indefinitely until it works perfectly on every single computer in the world.

j/k
It's being released get over it. If there are bugs, I'm sure they will release patches.
Is it ready enough to be easily/perfectly deployed on a large network of say 500 computers? Probably not because every network of 500 computers is different. If you expect it to work perfectly on everything, stop dreaming.

I tried all of the flight and beta live cds, but my mouse would not work on any of them. Yet it worked fine on 5.10 live cd. It better work with the final release, although I'm guessing it won't.
[Here](http://www.ubuntuforums.org/showthread.php?p=885133#post885133) is my mouse problem, which didn't get any help.

---

### Post by Anthem on 2006-05-31
[QUOTE=andrewabc]It's being released get over it. If there are bugs, I'm sure they will release patches.[/QUOTE]
Yup, that's where I'm at too.

I was really hoping this thread would die when the Dapper forums were closed.

I'll stop if you guys do.

---

### Post by nix4me on 2006-05-31
The thread should die.

It's coming hell or high water.

nix4me

---

### Post by elamericano on 2006-05-31
After reading some of the ridiculous expectations of an Ubuntu install doing as well or better than Windows pre-install, I think people have the wrong perspective. If an OEM were to use Ubuntu, a similar pre-install could be expected to out-perform Windows. That's a fair comparison. Not reality you say?

The reality is that if you didn't have to fork out $200 for the boxed version of XP, then you're probably still happy. If you're an IT manager who stands to save millions in Total Cost of Ownership by avoiding Windows solutions to problems you didn't have until you bought Windows, then you're still happy. IT will check hardware compatibility before making their next purchases. This is simple and obvious planning. You can make a custom install CD for your company that gives you even more hardware options for devices that can work, but don't install well. So there are many scenarios where Ubuntu will perform like a star.

However, until now I am judging Ubuntu by Breezy, which was fantastic. I expect the Dapper CD to be high quality too. I don't think fixing problems with updates is the right solution. I am not heartened by my personal Dapper Beta experience, but we'll have to wait and see. Any moment now...

---

### Post by vayu on 2006-05-31
I don't know about enterprises but it's not ready for this human being.  I have issues on the only 2 of my computers that I've tried.  I dist-upgraded from Breezy on one the other day and I have so many problems I don't know where to start.  

Today I thought I'd try a fresh install on another computer.  After fighting with the partitioning of the extremely slow live CD installer I finally got Dapper installed after quitting the installer then using a live gparted CD.  The install went well after that, but after spending all morning, I don't have the network working.  

Both these computers have been running Breezy just fine.  

I had similar experiences with Breezy.  I kept trying and I just couldn't get it to work until about a week or so after the release.  I kept apt-get updating then eventually it started working very well.  I have a feeling that's what will happen here.

I knew I should have waited another 2 weeks.

Personally I'd rather a one year release cycle.  Before I ever tried Ubuntu I was a little leary of the 6 month release cycle.  I think six months for features and six months for debugging would yield a combo of latest and greatest software versions combined with speed and stability.

---

### Post by aysiu on 2006-05-31
[QUOTE=vayu]
Personally I'd rather a one year release cycle.  Before I ever tried Ubuntu I was a little leary of the 6 month release cycle.[/QUOTE] Have you ever tried Debian? It has several years (just like Windows) between releases, but those releases are extremely stable.

---

### Post by David Corrales on 2006-06-01
Ready or not is not the question now. Let's all test it out to help quicken the polish :mrgreen:

---

### Post by flyingbrass on 2006-06-01
[QUOTE=aysiu]Have you ever tried Debian? It has several years (just like Windows) between releases, but those releases are extremely stable.[/QUOTE]
You weren't asking me, but I have used Debian.  Stable is old, boring, and not fun on the desktop.  Testing and unstable are somewhat stable depending on the phase of the moon and when you happen to upgrade, but they aren't good for newbies or people wanting something more solid.

As I see it, Ubuntu fills this gap.  With each release we get a relatively recent snapshot of unstable/testing with most of the kinks smoothed out. Suits me.

---

### Post by kvonb on 2006-06-01
I have had problems (clean install of Dapper RC) with nVidia driver for legacy cards, missing and unavailable xlibs for cedega, no MP3 or MPEG codecs, and I really believe gdebi is a step back to RPM dependency hell (unable to resolve dependencies)!  Otherwise everything else is really nice.

---

### Post by GoA on 2006-06-01
[QUOTE=topgi]Guys, just look to what M$ does. They release buggy operative system and then fix overtime. Windows XP wasn't really stable until the service pack 2. 
I bought a IPAQ 1950rx with windows mobile 5, I have to reset 3-4 times a day and after 3 month after release M$ relased the first update.  But now no more update and I keep doing reset.
This never happen to me with Dapper since 1 month and I keep installing and playing with many software.

Let's the show begin.......

Good Luck DAPPER[/QUOTE]

In that case yoy have something wrong with your computer or programs. Because XP has always been stable for me, when hardware is working proberly and there are no spyware or viruses affecting the system.

---

### Post by blakamin on 2006-06-01
[QUOTE=GoA]In that case yoy have something wrong with your computer or programs. Because XP has always been stable for me, when hardware is working proberly and there are no spyware or viruses affecting the system.[/QUOTE]
SP2 killed my laptop... the reason I dual boot now... with Kubuntu and Auditor:p

---

### Post by 3rdalbum on 2006-06-01
[QUOTE=kvonb]I really believe gdebi is a step back to RPM dependency hell (unable to resolve dependencies)![/QUOTE]

Well, to be fair, it's better than dpkg, which is ALWAYS unable to resolve dependencies :-)

---

### Post by olterman on 2006-06-01
I upgraded three work machines with update manager from breezy to dapper with virtually no hiccups ..... From my end it's solid

---

### Post by vayu on 2006-06-02
[QUOTE=aysiu]Have you ever tried Debian? It has several years (just like Windows) between releases, but those releases are extremely stable.[/QUOTE]

I've been thinking about it, but what I really want is something in between.  If you took Dapper which is about 8 months at this point and gave it another two or three months of just performance and debugging then you'd have reasonably up to date versions of everything AND really great performance and stability.

---

### Post by aysiu on 2006-06-02
But, vayu, the main contributor to instability is the integration of new packages. Once you change KDE from 3.4 to 3.5.2, you have a lot more debugging to do.

---

### Post by SHodges on 2006-06-02
Dapper is absolutely ready.  It looks great, runs great, is *incredibly* easy to install and use, it's just perfect as far as I can tell.  It's the first linux that I could really recommend to friends that aren't really computer smart.  The look alone is far better than Breezy's.

---

### Post by mips on 2006-06-02
qtparted in the dapper installer is fooked. I hosed my FAT32 data partition with about 65gigs worth of data in it. And NO I did not format the wrong partition, qtparted did.

I could actually replicate the problem. Some people are gonna cry when this happens to them, fortunately I have a backup.

Where is Reiser4 support by the way, not an filesystem option ???

---

### Post by vayu on 2006-06-02
[QUOTE=aysiu]But, vayu, the main contributor to instability is the integration of new packages. Once you change KDE from 3.4 to 3.5.2, you have a lot more debugging to do.[/QUOTE]

I'm not sure I understand what you mean.   Dapper's slick right now with the versions it has of Gnome, KDE, OO, Firefox, XGL, Compiz etc.  If it were taken at the point it is right now and then still worked on for two or three months just for bug fixing and maybe some surface level performance enhancements, then it would be exactly what I want.  I'd have very up to date versions of everything and even greater stability.  I like Ubuntu now and have been using it since Hoary, but getting Hoary to work all the way for me took a lot of time, so did Breezy, and now Dapper has two of my computers needing hours of work that I don't have at the moment.  I won't have time to upgrade Breezy on my laptop for quite a while.  With a 10 - 12 month release cycle I think the upgrading would be less painful.  

There was a lot of effort made to make Ubuntu graphical and easy to use.  That's lost for me when the graphical installer won't partition my drives, when the only browser in Gnome that doesn't crash on websites with pictures is Konqueror, when my MySQL database is wiped clean, my screensaver doesn't work and I've taken two half days off of work and I'm still not anywhere near using my systems the way I could with Breezy.  Dapper looks excellent. If it were taken as is and then fixed a little bit more, I'd have the distro I'd really want.  I'm not saying there's another out there that does better, just that longer release cycles, a compromise between the long cycles of Debian and what Ubuntu does, would suit my tastes a little better.  Just a wish.

---

### Post by usernamed on 2006-06-02
[QUOTE=christian.convey]
Is Dapper generally unready for release, or am I just especially unlucky for some reason?  From my experiences with it, it still seems way below the quality goals that the community and Mark have for it.

Am I the only one with this experience?

- Christian[/QUOTE]


No you're not alone.  My attempt to upgrade from 5.10 to the Release Candidate on an HP nx6125 left me with a broken system.  If I hadn't had another PC available to me, I'd have been left without a working computer.  That is an acceptable level of risk for a private Alpha release, but not for a public Release Candidate.

My network worked prior to the upgrade, but for some reason ifrename must be uninstalled before GNOME 2.14 can be installed.  I find it difficult to believe that this is genuinely the case, but apt-get insisted upon it.  Because I didn't have ifrename, the script that brought up the wireless interface failed and for some reason the card wasn't interested in being manually configured.

My ATi graphics drivers worked pre-install but not post-install, and everything ran at about 20% of the pre-upgrade speed.  The icing on the cake was the fact that the cooling fan stopped running post-upgrade, and I didn't notice until I picked the machine up and it burnt me.

I downloaded an install CD for 5.10 (on my old desktop box), formatted all partitions but /home and re-installed 5.10.  After the usual messing about to get gfx drivers working and my internal Broadcom wireless working, I have a working system.

If it is the intention to offer an upgrade facility, that upgrade must leave the user with a system that offers as much functionality as they had pre-upgrade.  It must not break something that was already working.  I would much prefer that upgrading was not an option than have it bork my computer.  

When I can click on the Upgrade button, and know that it isn't going to mean an evening of Googling, asking for help here or spending my night desperately trying to salvage what I can from my computer, that's when Ubuntu is a true real-world alternative for the desktop.

Until then, I run it because I believe in free standards based software, and I'm (just) technically proficient enough to maintain it, but I couldn't recommend it to anyone who sees a computer as a tool and just wants to get things done.

Sorry, I've ranted.

---

### Post by carlosqueso on 2006-06-02
Just an outside-the-box partially irrelevant suggestion.  Wouldn't it be possible to have the same 3-tiered structure as Debian and still keep the 6-month release cycle.  For example edgy would be just like it's supposed to be, dapper would be the "testing" one, and they'd release a new breezy iso with all of the updates from the cycle, and only do essential fixes.  Then, every 6 months, each changes level. (i.e. breezy gone, dapper to "stable", edgy to "testing" and edgy+1 started).  That might solve everyone's problems.

---

### Post by RDo on 2006-06-03
Dapper ready.. well. Since dapper my scanner and tvtime won't work anymore. This did work in breezy. I'm finding more bugs in dapper.... it's getting frustrating..

---

### Post by s6dalane on 2006-06-04
None of my USB devices (camera and flash memory) work with Dapper, but they used to work flawlessly with Breezy...

---

### Post by Evoreth on 2006-06-04
I'm now switching back from Kubuntu to Ubuntu, because KDE became hardly useable after a crash. The session doesn't start correctly anymore, even if I delete any configuration files related to it or start an empty session. Kubuntu still needs some love, but I'm looking forward to use it as a stable system - once it's ready.

---

### Post by mips on 2006-06-04
I havent even installed it since the beta version as I'm having major issues with the desktop cd.

This is really bad imho.

---

### Post by RDo on 2006-06-04
I think dapper is rushed .. even with the delay. I'm now finding out that java is crashing with firefox, aahh.... I'm going back to breezy.... this SUCKS. Another install .... -pfff-

---

### Post by ddoctor on 2006-06-04
I have had a nightmare trying to get Dapper installed.
I tried installing on 7 different machines with no luck.
I've tried 3 different cdrom drives and 2 different burns of the CD. I also checked the checksum.
In the best cases, the installer freezes at about 75% of "starting linux kernel".
In the worst cases, the installer crashes when loading ISOLINUX.
In most cases, the installer displays the menu, I select "install or start ubuntu", then it displays small graphics glitches on the screen and freezes. Same happens when using the "test cd" option.

I then tried installing version 5.10 from a ShipIt CD - it installed fine.
I then tried the instructions on the wiki for upgrading. Upgrading via the live cd failed, using update manager and apt. 
I managed to get update manager to recognise that Dapper was available, but then I got some stupid error saying my base package was missing and "this is a serious error, you should report it as a bug."

I then tried getting synaptic to update everything, which took about 5 hours (Note: I have a 1.5k DSL line), with the only noticeable effect being the removal of openoffice. 

I just don't get it. I've now wasted a whole weekend simply trying to get an OS installed. 

Hardware:  PIII 650, 256MB ram, Asus P2b-n mobo, liteon ldw451s, seagate 80g

---

### Post by mejy on 2006-06-04
[QUOTE=ddoctor]I have had a nightmare trying to get Dapper installed.
I tried installing on 7 different machines with no luck.
I've tried 3 different cdrom drives and 2 different burns of the CD. I also checked the checksum.
In the best cases, the installer freezes at about 75% of "starting linux kernel".
In the worst cases, the installer crashes when loading ISOLINUX.
In most cases, the installer displays the menu, I select "install or start ubuntu", then it displays small graphics glitches on the screen and freezes. Same happens when using the "test cd" option.
[/QUOTE]
Have you tried using the install cd as opposed to the live cd with installer?  There's a chance this could be a bug with the live cd.

[QUOTE=ddoctor]
I then tried installing version 5.10 from a ShipIt CD - it installed fine.
I then tried the instructions on the wiki for upgrading. Upgrading via the live cd failed, using update manager and apt. 
[/QUOTE]
As far as I know you can't upgrade using the live cd, and again must use the install cd as a repositry.  Where's the wiki page that suggested doing this?

[QUOTE=ddoctor]
I managed to get update manager to recognise that Dapper was available, but then I got some stupid error saying my base package was missing and "this is a serious error, you should report it as a bug."
[/QUOTE]
This probably means that ubuntu-desktop was not installed.  To upgrade over the internet:

sudo apt-get install ubuntu-desktop
sudo gedit /etc/apt/sources.list
change all instances of 'breezy' to dapper
sudo apt-get update
sudo apt-get dist-upgrade

[QUOTE=ddoctor]
I then tried getting synaptic to update everything, which took about 5 hours (Note: I have a 1.5k DSL line), with the only noticeable effect being the removal of openoffice. 
[/QUOTE]
This was presumably removing openoffice to prepare for the installation of openoffice 2, but since ubuntu-desktop was not installed there was nothing to tell it to install that package.  It took 5 hours because the ubuntu servers are (obviously) going to be under heavy load around new releases and will operate signifficantly slower than they do usually.

---

### Post by _teo_ on 2006-06-04
[QUOTE=ddoctor]... In the best cases, the installer freezes at about 75% of "starting linux kernel".
...
Hardware:  PIII 650, 256MB ram, Asus P2b-n mobo, liteon ldw451s, seagate 80g[/QUOTE]
Last week I had a similar problem with Breeeze. It wasn't able to install on a x86 machine and failed on exactly the same point. The motherboard is ASUS and I thought that it is somehow too new for it. But it turned out that one of the hard drives is the problem - an IBM 60GB slave drive. After removing it from the system everything went good.

Next days I'm going to try Dapper on same machine, but with a new SATA drive. I don't expect any problems, because I already use it on other machines including its 64-bit version.

You may try to find any relation between the hardware on all these machines. Hope you'll figure it out.

---

