---
title: "File hosting and versioning"
date: 2010-01-18
forum: General Help
---

### Post by youoneah on 2010-01-18
Hi,

Isn't it great, using online servers to store data? This gives you a simple (not robust) backup solution for data files, and when you work on two or more computers, you usually have quick access to your files without having to transfer them via external media.

This is great when working with, say, images and office documents, but what about when you have lots of little files and directories, or you want or need to work on local versions? No problem, you just sync the files between local use and the server. (Although now you've got to make sure the sync software is supported.)

And what if you want to share a file or project with someone else? And what if you want the ability to track changes to your project, or even simultaneously work on parallel versions? Now we're talking about revision control.

A number of hosting services are available for distributing and tracking development projects -- even for free. All of these that I've found, however, are specifically intended for *software* development projects: Launchpad, gna.org, BerliOS, Google, etc. I'm not much of a programmer, but I find version-control tools quite neat for managing *authoring* projects across 2+ computers that are based on text and binary files, such as LaTeX and LilyPond.

So what I'm looking for is suggestions for a preferably free online service that provides hosting with revision-control access for private, whatever-purpose projects. It seems there are solutions for paid hosting, but I prefer to avoid that hassle. I have experience mostly with Subversion, but wouldn't mind something else, so long as it's fairly easy to learn. Has anyone else found solutions for similar needs?


P.S. -- I've given up on the idea of setting up my own server. I like the idea of the learning experience, but haven't given it priority and it's just an inefficient solution for my needs.

---

### Post by J V on 2010-01-18
if both PCs are connected by lan, gome server is the way to go, linux is easy to maintain that way :)

Only other option is paid hosting or insecure hosting, either of which is very very bad...

---

### Post by john newbuntu on 2010-01-18
I would vote on CVS or subversion on a local box with regular automated backups. Once installed, it has minimal maintenance, is obviously free and is local rather than letting others see the data.  As JV mentioned, how secure or reliable is your host who depend on ad revenues?  I have seen this done in a major corporation that I once worked for.

---

### Post by youoneah on 2010-01-18
As I mentioned, a local server is inefficient, even if it would be a fun project. There is the cost of the machine, and the scrap machine I have has an as-yet-to-be-isolated faulty hardware component and is based on pentium-RAM-IDE technology that is increasingly rare. So a pain to fix and probably a hundred bucks or more -- plus it's loud. This would have the advantage of lots of file space, but I neither want to leave a noisy machine constantly running nor turn it on when needed. (Need my files... trip to the cellar, !)

Major corporations have considerably more resources and greater needs than I...

Bottom line, right now I'd rather spend my time authoring than administrating, which I'm not really great at anyway.

I currently am looking at book and music projects, so security is not such a big issue. SSL connection would be a plus, but only password encryption is really necessary. But the statement about hosting being either paid or insecure does open an interesting question: are services like Launchpad, gna.org, BerliOS, Google, and so on insecure?

---

### Post by t0p on 2010-01-18
> **youoneah said:**
> 
are services like Launchpad, gna.org, BerliOS, Google, and so on insecure?

Unfortunately I don't have links to hand - Google would be your friend here - but Dropbox seems to be pretty secure according to Dropbox.  And Google claim they're secure too.  As for the other providers you mention... Google is, again, your friend.

If you distrust third-party storage solutions as much as your posts indicate: don't use them.  I know you say you can't be bothered with all that; but you need to decide what's more important to you: security or convenience.  Anyway, running a server doesn't have to be such a PITA.

---

### Post by youoneah on 2010-01-18
Thanks for the reply, t0p. I must not have written clearly, although I did mention that security is not a big issue for such projects. Me wondering about the security of 3rd-party sites:
> **youoneah said:**
> But the statement about hosting being either paid or insecure does open an interesting question: are services like Launchpad, gna.org, BerliOS, Google, and so on insecure?
... is directly in response to J V: "Only other option is paid hosting or insecure hosting, either of which is very very bad..."

But those sites are not intended for non-software development projects.

Does anyone have experience using (free) revision-control hosting?

---

