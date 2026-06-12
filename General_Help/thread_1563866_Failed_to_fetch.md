---
title: "Failed to fetch?"
date: 2010-08-29
forum: General Help
---

### Post by JSeymour on 2010-08-29
Tried searching for an answer.  No luck.  As of mid last week or so, I'm getting this from the update manager:

Failed to fetch [http://ppa.launchpad.net/sevenmachines/nvidia/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/sevenmachines/nvidia/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Running Ubuntu 9.10

What's up?  What, if anything, can I do to fix it?

Thanks,
Jim

---

### Post by howefield on 2010-08-29
Looks like that particular ppa has been taken down for some reason.

You can remove it from your software sources, temporarily if you like.

Go to System > Administration > Software Sources > Other Software tab and uncheck the relevant repository.

Then close and reload your sources, should now be error free.

---

### Post by JSeymour on 2010-08-29
> **howefield said:**
> Looks like that particular ppa has been taken down for some reason.Yeah.  It looks like it was just up and removed--as if it had never existed.  Still a boat-load of Google hits that point to that PPA.  Near as I can tell: No notification, announcement, etc. that it had been removed, or why.

> **howefield said:**
> You can remove it from your software sources, temporarily if you like.Thanks for the guidance, but I knew that :).  I should've been more clear: As in: Anybody know what happened to it and if it's been moved elsewhere, or what?

Thanks,
Jim

---

### Post by WorMzy on 2010-08-29
Well, looks like the entire nvidia branch of that launchpad archive has gone, so you're best off asking at #SevenMachines on [Freenode]("irc://irc.freenode.net") about it.

---

### Post by JSeymour on 2010-08-29
> **WorMzy said:**
> Well, looks like the entire nvidia branch of that launchpad archive has gone, ...Yup.

> **WorMzy said:**
> ...so you're best off asking at #SevenMachines on [Freenode]("irc://irc.freenode.net") about it.Tried that already.  Nobody there.  Completely empty channel.  Which is no surprise, because...

/chanserv info #SevenMachines
-ChanServ- Channel #SevenMachines is not registered.

Impressive.

Jim

---

### Post by WorMzy on 2010-08-30
Oh dear.

Well, you could leave a message for him/her here: [https://launchpad.net/~sevenmachines/+contactuser](https://launchpad.net/~sevenmachines/+contactuser)

---

### Post by JSeymour on 2010-08-30
> **WorMzy said:**
> Oh dear.

Well, you could leave a message for him/her here: [https://launchpad.net/~sevenmachines/+contactuser]("https://launchpad.net/%7Esevenmachines/+contactuser")Thanks.  I looked for a "contact user" link on SevenMachine's main launchpad page.  Found nothing--other than what looks like an email address under "SSH Keys."  If I click on the link you gave, I simply end up back at [https://launchpad.net/~sevenmachines]("https://launchpad.net/%7Esevenmachines")

Pretty weird.  I don't know who "SevenMachines" is, but all this doesn't inspire confidence, that's for sure!

Jim

---

### Post by WorMzy on 2010-08-30
Hmm, you probably need to be logged in to launchpad to view the contact page, and I'm guessing that you weren't/don't have a launchpad account?

Try the email address instead.

Can I ask why you were using this repository? The nvidia driver in the main repos should be as up-to-date as necessary.

---

### Post by JSeymour on 2010-08-30
> **WorMzy said:**
> Hmm, you probably need to be logged in to launchpad to view the contact page, and I'm guessing that you weren't/don't have a launchpad account?My guess is you're correct and, no, I don't have a launchpad account.

> **WorMzy said:**
> Try the email address instead.Perhaps I will.

The whole thing strikes me as kind of odd.  Like I said: The repos just disappeared, with no mention of it anywhere, as if it had never existed.  He's got a blog/Wiki, I believe.  I would've expected to see something there, at least.  Nada.

> **WorMzy said:**
> Can I ask why you were using this repository? The nvidia driver in the main repos should be as up-to-date as necessary.I really couldn't say, now.  That was... eight months ago I added that?  If you search on installing the Nvidia drivers, it's SevenMachine's PPA that comes up.

Y'know... it just occurred to me...  you guys are going to laugh and laugh... I hope.  The NVidia  card I tried to use wouldn't work with my Dell 1600SC.  Some kind of odd BIOS incompatibility.  I've been using an  ATI Radeon 2400 Pro              card all this time.

I didn't need that repos *at all*, all this time! :p

Sorry to have wasted everybody's time :(

Sometimes I'm  such an id10t.

Jim

---

### Post by WorMzy on 2010-08-30
Haha, never mind. We've all spent time trying to fix a non-problem before.

My advice to anyone who finds this topic after receiving the same update manager/synaptic error is to either email the guy, or create a launchpad account and contact him through that. If you don't need the repo, then just remove it from your software sources like Howefield suggested in post #2.

---

