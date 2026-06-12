---
title: "Third party repos"
date: 2009-09-14
forum: General Help
---

### Post by Stuart O'mahony on 2009-09-14
New to Ubuntu (not Linux), and not having much joy in finding some packages (Songbird, Opera, Elltube...). I have Main, Restricted, Universe and Multiverse enabled, and am wondering if there are any major third party sources I should add.

I could go to the respective home pages of course, but don't want to do all that if it's just a case of adding another repo or two.


p.s. I have run sudo apt-get update already.

---

### Post by P4man on 2009-09-14
None of the apps listed are supported by canonical, hence they are not in the repo's, and maybe not even in the universe repo's.

opera have their own repository though:

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

not sure about singbird.. ive got this ppa in my software sources:

edit: scratch that, no longer maintained

---

### Post by NoaHall on 2009-09-14
Try downloading Ubuntu Tweak - as a beginner, it will help you, and it have Opera and Songbird in it ( i think)

---

### Post by Pirolocito on 2009-09-14
I sure recomend wine repositorie.

---

### Post by steveneddy on 2009-09-14
> **Pirolocito said:**
> I sure recomend wine repositorie.

That repo has nothing to do with the OP's original question.

Opera instructions:

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

Songbird can be had here:

[http://www.getdeb.net/app/Songbird](http://www.getdeb.net/app/Songbird)

here:

[http://www.getsongbird.com/](http://www.getsongbird.com/)

or add the ppa: (which is the best way IMHO)

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

And Elltube:

[http://elltube.sourceforge.net/download](http://elltube.sourceforge.net/download)

Good luck.

For software not in any repos either DL from the source web site, from the developer or type in [COLOR=Blue]**<name of application> ppa**[/COLOR] in Google and you will be surprised what is available for you there.

---

### Post by P4man on 2009-09-14
> **steveneddy said:**
> 

or add the ppa: (which is the best way IMHO)

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa) 

Not sure id use a repo that automatically does a daily built without any checking. Use a "human" controlled PPA, or just manually download it from mozilla.

---

### Post by steveneddy on 2009-09-14
> **P4man said:**
> Not sure id use a repo that automatically does a daily built without any checking. Use a "human" controlled PPA, or just manually download it from mozilla.

It's not automatic - it is a daily build - the developer's version. the very definition of a **daily build** is a dev or group of devs are **building** the software **daily** then updating it to a ppa.

Software doesn't build itself.

There are other option there is the OP doesn't want the ppa.

I use the Firefox 3.5 ppa and so far so issues.

As long as you know what you are getting, it's OK to run a daily built ppa.

---

### Post by P4man on 2009-09-15
> **steveneddy said:**
> It's not automatic - it is a daily build - the developer's version. the very definition of a **daily build** is a dev or group of devs are **building** the software **daily** then updating it to a ppa.


Yet the PPA itself states:

> The PPA is maintained by a bot, so it contains completely untested builds, mostly useful to track regressions or if you are curious, or just brave.

Im not sure, but it sounds like it could be compiling from source automatically, in which case, no human is testing it before its put up there.

---

### Post by mike67114 on 2009-09-15
[http://www.getdeb.net/](http://www.getdeb.net/) has Ubuntu software

---

### Post by Stuart O'mahony on 2009-09-18
Thankyou for all the replies.

The best option for me might be to add launchpad as a repo, but what's the url for that? I've been looking around the site, but not sure what it might be.

I'm used to Mandriva, where there's a heck of a lot rpms available in the repos, and not so keen to start on all this site-hopping: are there a greater number of packages maintained in Universe and Mulitverse repos for the later versions of Ubuntu? Given i'm a Hardy Heron user.

---

### Post by Vaphell on 2009-09-18
you go to the System->Administration->App sources (or whatever it's called)
3rd party tab, Add
paste something like this (you should choose proper ubuntu version)
```
deb http://ppa.launchpad.net/songbird-daily/ppa/ubuntu jaunty main
```
into the window

from now on packages are visible in your package manager

---

### Post by Stuart O'mahony on 2009-09-18
That's only for Songbird though, can I add just launchpad? So I can search all its available Ubuntu packages in Synaptic? Given the way the path is formed, (i.e.the package name comes before /ppa/ubuntu) i'm less sure.

I hope i'm wrong. Ultimately i'd like to search packages along the cli.

---

### Post by michy99 on 2009-09-18
Launchpad is not a repository itself. It is a site that allows people to have a lot of different repositories specializing in different apps.

---

### Post by oldos2er on 2009-09-18
There are thousands of PPAs at the launchpad site. Go here [https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas) and you can search for a particular package.

---

