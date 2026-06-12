---
title: "How do I start contributing to Ubuntu?"
date: 2012-07-06
forum: General Help
---

### Post by harisund on 2012-07-06
I am trying to understand how I can contribute to Ubuntu from a technical point of view, and am basically lost. 

As I understand it, most Google results simply say to "scratch your own itch". Pick a program you use a lot, report your bugs. Problem, I use programs that are very popular, so if I do encounter a bug, it's already reported, and in most cases already fixed or someone's already fixing it. That, and I really don't have any "scratches" per se. 

Second, there seem to be no tutorials / guidelines / helpful wiki pages that show me where to start, what to download, how to look for bugs, how to start fixing them. 

I would like to help package / maintain softwares, but again, it appears everything's already being maintained by someone. Where can I see a list of packages that are up for adoption, and guidelines on how to pick one up? 

The wiki pages all take me in circles. There doesn't seem to be a definitive "start here if you want to .... " page. 

Any help / advice on how I can get started? 

For reference, I am extremely comfortable on the command line, much more so than the GUI. I can code.

---

### Post by MG&amp;TL on 2012-07-06
We don't really 'adopt' packages in Ubuntu-that's what Debian does. 

If you want to get a bug report that hasn't been dealt with, go to the project bugs home in launchpad:

```
bugs.launchpad.net/<name>

```

or

```
bugs.launchpad.net/ubuntu/<name>
```

for packages released in Ubuntu (i.e. stable).

Then click 'Advanced search' and select the relevant boxes. You probably want 'new' or 'triaged' not 'Invalid' or 'Fix commited'.

I found it hard to get started as well. I tended to drift for a while before finding something I liked doing.

---

### Post by QIII on 2012-07-06
You might become a contributor to a [MOTU](https://wiki.ubuntu.com/MOTU/) and work your way into [becoming one](https://wiki.ubuntu.com/MOTU/GettingStarted).

MOTUs package and maintain the stuff in the Universe and Multiverse repos.

---

### Post by Cheesehead on 2012-07-06
> **harisund said:**
> there seem to be no tutorials / guidelines / helpful wiki pages that show me where to start, what to download, how to look for bugs, how to start fixing them.

Have you seen [https://wiki.ubuntu.com/BugSquad/GettingInvolved](https://wiki.ubuntu.com/BugSquad/GettingInvolved) ?
One way to get started with bugs is to help classify them by package: 

1) Add youself to the Bug Squad team: [https://launchpad.net/~bugsquad](https://launchpad.net/~bugsquad)

2) Join the #ubuntu-bugs chat on irc.freenode.net. You can ask bug-related questions there and get good advice.

3) Pick a bug without a package. Any from [https://bugs.launchpad.net/ubuntu/+bugs?field.status%3Alist=NEW&field.importance%3Alist=UNDECIDED&assignee_option=none&field.has_no_package=on](https://bugs.launchpad.net/ubuntu/+bugs?field.status%3Alist=NEW&field.importance%3Alist=UNDECIDED&assignee_option=none&field.has_no_package=on)

4) Use your critical thinking skills. Is it really a bug? Or is it a complaint or a help request or a hardware problem or something else? Does it belong to a package? or do you need more information. As you run into questions, ask the gurus in #ubuntu-bugs or ask the original submitter for more information. Subscribe to the bug, and follow it through the process.

After following a couple bugs through the process, you will have a better idea of how you can best help.

> **harisund said:**
> Where can I see a list of packages that are up for adoption, and guidelines on how to pick one up?

Automated tools handle most building and packaging. Many maintainers I know deal with other people more than code. Often three communities (upstream, Debian, Ubuntu) may not communicate well, or share bug information properly. Bugs, patches, and releases may languish instead of getting pushed to the other communities. Help get all three communities aligned, help coordinate efforts, help facilitate communication. As new volunteers appear, help coordinate their efforts for best benefit to all three communities. Help share tools and processes. Most Debian maintainers I know prefer working with bugs and patches, and *love* getting help with the people end of the business.

If any package you look at has a lot of bugs that are not Triaged (or Confirmed or Upstreamed), then the maintainer needs help. Jump in.

If any package is well-maintained, contact the maintainer and offer to assist. Maintainers change jobs or interests like everyone else; an assistant ready to step up to primary is wonderful. 


> **harisund said:**
> The wiki pages all take me in circles. There doesn't seem to be a definitive "start here if you want to .... " page.
Right. The straightforward, linear Problem A -> Process B -> Result C issues have (mostly) already been automated. And every new volunteer has different interests. Generally, best advice is to try a few bugs - that will expose you to how the community works, and much of the workflow of the many teams and projects. After a few bugs, you are likely to have a preference of what you want to try, and then we can give you better advice.

---

### Post by harisund on 2012-07-07
Thanks for the advise ! 

Also,
 > **Cheesehead said:**
> Most Debian maintainers I know prefer working with bugs and patches, and *love* getting help with the people end of the business.

If I was good at dealing with people, I wouldn't be an engineer, I would be in marketing or HR or something making more money and having less time to bother contributing to Ubuntu  :P 

I particularly don't want to deal with people. I am not good at it. That's why I am not keen on contributing to Ubuntu through IRC or Forums or writing documentation or anything along those lines. 

But yeah, the rest of your suggestion I will follow through and see how I can actually break through the seemingly tall entry barrier.

---

