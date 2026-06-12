---
title: "Would you please check my PPA source list?"
date: 2010-04-18
forum: General Help
---

### Post by belnac on 2010-04-18
Hi,

I'm fairly new to Linux's and Ubuntu's PPA-based update/install mechanism and am beginning to wonder how safe these PPAs really are. In particular, I wonder how easy it'd be for a private PPA maintainer to include malicious code in their PPAs (I'm guessing it'd be fairly easy) and how likely I'd be to actually notice something was wrong.

My PPA source list has grown to quite a fairly large size since I ditched Windows and started using Ubuntu only. My request to you is if you could have a look at my PPAs and advise me on which to ditch, being that security is my number one concern. Also, I'd very much appreciate it if you could provide me with some pointers as to what considerations to make or steps to take when hunting for PPA sources (i.e. cross check launchpad username on some other site; etc.)

My PPA list:

[https://launchpad.net/~dreibh/+archive/ppa](https://launchpad.net/~dreibh/+archive/ppa)
Dia, the diagram creation tool.

[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)
smplayer

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)
mplayer

[https://launchpad.net/~ubuntu-x-swat/+archive/ppa](https://launchpad.net/~ubuntu-x-swat/+archive/ppa)
I believe this PPA is included in the default installation.

[https://launchpad.net/~liferea/+archive/ppa](https://launchpad.net/~liferea/+archive/ppa)
liferea RSS reader

[https://launchpad.net/~webkit-team/+archive/ppa](https://launchpad.net/~webkit-team/+archive/ppa)
WebKit PPA required by liferea

[https://launchpad.net/~freshgames/+archive/ppa](https://launchpad.net/~freshgames/+archive/ppa)
To keep openttd up to date.

[https://launchpad.net/~jhs.schmid/+archive/ppa](https://launchpad.net/~jhs.schmid/+archive/ppa)
Anjuta

[https://launchpad.net/~pasgui/+archive/ppa](https://launchpad.net/~pasgui/+archive/ppa)
Codeblocks (unsure whether to use Anjuta, Codeblocks or just keep using emacs + command line)

[https://launchpad.net/~ubuntu-toolchain/+archive/ppa](https://launchpad.net/~ubuntu-toolchain/+archive/ppa)
GCC along with several other Linux utilities kept updated.

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)
WINE

[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
Chromium browser

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)
Pidgin

[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)
Deluge (BitTorrent client)

---

### Post by Bucky Ball on 2010-04-18
Who would be writing the malicious code and what would it do? To do any real damage you would be asked to enter your password and you might notice that coming up for no reason.

But no, unlikely insecure. Might crash your system for other reasons!

---

### Post by wojox on 2010-04-18
A majority of those apps are in the repositories. Any reason you don't download from there?

I've downloaded ppa's from Launchpad and have yet to have problems.

---

### Post by Bucky Ball on 2010-04-18
Agree with wojox. Unless you have a specific reason, ALWAYS check the repos for the app you are after before adding the PPA.

---

### Post by Linuxforall on 2010-04-18
Unless you need cutting edge, there is no sense in going for ppa, I only add Open Office, Transmission, Pidgin and Handbrake PPA as I know they are from the developers themselves.

---

### Post by snowpine on 2010-04-18
I avoid PPA's for stability, not security, reasons. The application versions in the Ubuntu repositories are tested and known to be stable together. I only add newer versions of specific apps from 3rd party sources in the rare instance I need it for work (for example a new OpenOffice to open a document someone sent me).

---

### Post by belnac on 2010-04-18
First off, thanks to all for your answers!

[quote=wojox]A majority of those apps are in the repositories. Any reason you don't download from there?[/quote]

The reason is often the versions in the repositories are not up to date with the latest stable releases. For instance, I have GCC 4.4.1 in my Ubuntu 9.10 install but it seems v4.5.0 is already out. I don't really need the latest cutting edge releases but I guess keeping software up to date is something I enjoyed doing when I was a Windows user. Hence why I went ahead and added PPAs for my favourite apps.

[quote=snowpine]**I avoid PPA's for stability, _not security_, reasons**. The application versions in the Ubuntu repositories are tested and known to be stable together. I only add newer versions of specific apps from 3rd party sources in the rare instance I need it for work.[/quote]

I guess that's a valid enough reason but why exactly isn't security a concern for you?

[quote=LinuxForAll]**Unless you need cutting edge, there is no sense in going for ppa**, I only add Open Office, Transmission, Pidgin and Handbrake PPA as I know **they are from the developers themselves**.[/quote]

Interesting, you say you only add PPAs from developers themselves, any particular reason why? As I said in my original post my idea of a PPA maintained by a user not related to the actual software development team is that it can be potentially dangerous since the user has full control over the source code and build.

As an example of my concerns, consider a scenario where a keylogger is introduced into a PPA apparently looking like the latest release of a fairly popular Linux app. What isn't clear to me is if that rigged app would trigger any alarm bells when I ran it such as request for clearance to perform administrative tasks (access to root, etc)? This is just one of the concerns I have since I do online banking and being a Linux user I don't run anti-virus or firewall Sw (have a firewalled router anyway.)


PS: Emphasis on some of the quotes above is mine.

---

### Post by snowpine on 2010-04-18
> **belnac said:**
> The reason is often the versions in the repositories are not up to date with the latest stable releases. For instance, I have GCC 4.4.1 in my Ubuntu 9.10 install but it seems v4.5.0 is already out. I don't really need the latest cutting edge releases but I guess keeping software up to date is something I enjoyed doing when I was a Windows user. Hence why I went ahead and added PPAs for my favourite apps.

Fair enough, but I would encourage you to consider trying it the "Ubuntu Way" for at least one development cycle. The idea is that major upgrades are "lumped" together, so you get one big upgrade every 6 months (a new Ubuntu release) rather than worrying about daily/weekly system maintenance. All the packages in the Ubuntu repositories are tested together as a working whole that is "frozen" at a particular moment in time (October 2009 for Karmic, April 2010 for Lucid, etc.).

It would be a different story if you were upgrading *everything* at the same time (called a "rolling release" distro), but with PPAs, you end up with a situation where you're running a mix of old and new applications that were never tested/intended to work together. It just bugs me aesthetically to have a mix of old and new software; the versions "drift" apart over time and I'm concerned this may cause stability problems. 

GCC is a good example; version 4.5 has been released for a whopping *4 days* and won't be included in this month's 10.04 release. It isn't even in Arch Linux yet (one of the most "bleeding edge" rolling release distros). It will be 10.10 at least until GCC 4.5 is tested as stable to be included in Ubuntu. I would encourage you to be cautious and trust Ubuntu's conservative timeframe with major changes.

But that's just my 2 cents, do what you please. :)

> **belnac said:**
> I guess that's a valid enough reason but why exactly isn't security a concern for you?

As I mentioned above, I use third party software sources *very* sparingly, only end-user applications from sources I trust (Firefox and OpenOffice are really the only two I care about).

---

### Post by belnac on 2010-04-19
Awesome post snowpine! Guess I hadn't yet understood what the Linux philosophy is regarding software releases and upgrading/maintenance. Your post has shown me the light. ;-)

Thanks man!

---

