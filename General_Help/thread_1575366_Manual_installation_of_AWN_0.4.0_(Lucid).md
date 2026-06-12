---
title: "Manual installation of AWN 0.4.0 (Lucid)"
date: 2010-09-15
forum: General Help
---

### Post by FullMetalManiac on 2010-09-15
Okay.  Here's my problem.  I'm installing Avant Window Navigator manually on 10.04 (Lucid) from packages.  I get to the point where I have 6 packages left, which are the AWN itself, the c and python cores, the AWN settings, fortunes-min, and fortune-mod.

When I try to install fortunes-min, which is the next dependency, it tells me that there are 2 packages that need installing; fortunes-min and fortune-mod, and it won't let me continue any further.  Now the thing of it is is that all 4 of the other depends require both fortunes-min and fortune-mod.  Is there any way I can work around this, or figure out how to get fortunes-min to install from package?  I don't have an internet connection, which is why I'm installing manually.  Please help!!!

---

### Post by spjackson on 2010-09-15
When you say that you are manually installing the packages, I take it that you have the .deb files from somewhere. What tool are you using to install them?

As these packages are mutually dependent, you need to install them together, e.g.
```

sudo dpkg --install fortunes-min.deb fortune-mod.deb

```I think that should do it.

---

### Post by FullMetalManiac on 2010-09-15
Yeah, I ran it through the Software Center, waited for the download error, copy-pasted the dependencies and went to my local library to get the packages.  And, I'm using Synaptic Package Manager, which came with ubuntu.  I'm not too familiar with Linux anymore, as it's been like 7 years since I used it last (RHEL 3)


But, :D thank you, thank you, thank you! :D  I was about pulling my hair out!

Now, when I do the sudo dpkg thing, I have to put the path to each .deb, right?

---

### Post by spjackson on 2010-09-16
> **FullMetalManiac said:**
> Now, when I do the sudo dpkg thing, I have to put the path to each .deb, right?Yes.

---

### Post by FullMetalManiac on 2010-09-18
Yeah, sorry.  Like I said, it's been years since I've even touched Linux, well, for any great length of time, anyway....had Gutsy for a couple of days, but my laptop went kaflooey after that...

It worked like a charm, though!  I've got it installed now, and it works wonderfully!

So, Thank you much, sir.

---

### Post by kerry_s on 2010-09-18
in ubuntu, it's better to use ppa's, that way it stays up to date.
here's the search page:
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

here's the latest version:
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by FullMetalManiac on 2010-09-19
Um, thanks for the tip, but, I'd have to manually update it, anyhow, as I don't have net...That's why I installed manually to begin with.  If I had net, this ****'d be a lot easier lol

---

### Post by kerry_s on 2010-09-19
> **FullMetalManiac said:**
> Um, thanks for the tip, but, I'd have to manually update it, anyhow, as I don't have net...That's why I installed manually to begin with.  If I had net, this ****'d be a lot easier lol

sorry, missed the part where you didn't have internet. :oops:

---

