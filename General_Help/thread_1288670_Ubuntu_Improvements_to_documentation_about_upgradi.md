---
title: "Ubuntu Improvements to documentation about upgrading"
date: 2009-10-11
forum: General Help
---

### Post by AlanRick on 2009-10-11
Hi,

This post is in response to some bug reports and forum threads relating to Ubuntu versioning and packaging. The idea is that some of the misconceptions relating to which version to install and how to maintain it could be avoided by firming up documentation and tightening some of the definitions.

In particular I hope that concrete suggestions will come out of this and make their way to the community help wiki. This would be especially useful to newbies like myself.

Here goes with the first 2 suggestions...

**Issue 1. Clarifying the content and life-cycle of a release.**


_Background:_
> The Ubuntu promise - Ubuntu will always be free of charge, including enterprise releases and security updates. ([www.ubuntu.com](www.ubuntu.com))

That's a great digestible statement. But it would mean more if I could  navigate to a page where the terms are explained unambiguously without relying too heavily on different readers' interpretation based on their different intentions and different software heritage? What is an “enterprise release” and what is a “security update”?

_Concrete suggestion:_

Add a page on the community help wiki explaining this statement. in more detail than the statement itself (but less detail than  the official Ubuntu book). 

How's this for starters ?

A “*Release*” is a Ubuntu distribution of a set of software packages, including operating system packages and application packages, in one simultaneous burst. There is a lifespan for each release, which is well-defined, public and predictable. During this lifetime security updates are delivered on a continuous basis without the need to unexpectedly upgrade to a newer release. The goal of security updates is to fortify Ubuntu, (including the user's data), against malicious or criminal attacks. It is expected that a responsible enterprise or individual will upgrade to a newer release before the current release lifespan expires. 

**Issue 2. Clarifying maintenance coverage.**

_Background:_

On the main download page:
> Ubuntu 8.04 LTS Desktop: Release April 2008 and maintained until April 2011 – ideal for large deployments. ( [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download))

Contrast this with this statement on the main documentation page:
> This site is where you can find the official documentation developed and maintained by the Ubuntu Documentation Project. ([https://help.ubuntu.com/](https://help.ubuntu.com/))


The term "*maintained *" is ambiguous here. What is maintained? Security, Defects, Deficits? I believe the first usage only refers to security and fixable defects whereas the second usage also includes deficits. I.e. The documentation will improve over time offering more content and filling in gaps (deficit) maintenance) but features will not be added to the LTS release (no deficit maintenance).

I'm not splitting hairs here – this distinction has real repercussions on which software an enterprise or individual decides to deploy.

So this word *maintenance *is too ambiguous to use without qualifying it further.

_Concrete suggestion:_

Change the statement to:

1. > Ubuntu 8.04 LTS Desktop: Released April 2008 with security maintenance until April 2011 – ideal for large deployments.

2. And add page on Ubuntu help or community help could add more detail about what type of defect maintenance can be expected and what cannot.


@Admin, Apologies if this is not the correct process or forum - as I said the purpose is to suggest documentation changes to avoid misconceptions. E.g. bugs 283137 and 389322)

If there's support for these improvements I'll see if they can be added to the community documentation. If this is the wrong medium, please let me know.

Alan

---

### Post by cariboo on 2009-10-11
You can join the documentation team [here]("https://wiki.ubuntu.com/DocumentationTeam").

---

