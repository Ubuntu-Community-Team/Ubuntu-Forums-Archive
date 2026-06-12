---
title: "Version error with AcvtivInspire"
date: 2012-08-30
forum: General Help
---

### Post by Robing Goodfellow on 2012-08-30
Right, not really an Ubuntu problem, I know, but the people that SHOULD know, don't know or don't care.   I could use some help and this is the place with the best brain power, so here we go.

I'm running Precise on a 64 bit HP G62.  My district finally decided to bring us out of the stone age, they bought a few Promethean Boards.  No computers, just the boards.  

The software to run the board is activinspire [http://www.prometheanplanet.com/en-us/Support/ProductPage.aspx?product=22]("http://www.prometheanplanet.com/en-us/Support/ProductPage.aspx?product=22")

They only support up to Karmic, but their software hasn't changed, ours has.  It's installed through synaptic from their repositories.  I went through their install procedure, everything's okey doke, except the drivers, and here's the errors I get from synaptic:
```
E: /var/cache/apt/archives/activaid_2.0.1-8~ubuntu%5f910_amd64.deb: parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'activaid':  error in Version string '2.0.1-8~ubuntu_910'
E: /var/cache/apt/archives/activdriver_5.7.22-11~ubuntu%5f910_amd64.deb: parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'activdriver':  error in Version string '5.7.22-11~ubuntu_910'
E: /var/cache/apt/archives/activtools_5.7.22-11~ubuntu%5f910_amd64.deb: parsing file '/var/lib/dpkg/tmp.ci/control' near line 2 package 'activtools':  error in Version string '5.7.22-11~ubuntu_910'


```

Okay, so Precise doesn't like that I'm using a package designed for Jaunty.

My IT department is helpless, the trainer that's teaching us how to use this tool glazed over as soon as I said Linux, their help forums are less than helpful.

I really need to get this going.  I'm in an urban school district that, before now, thought the height of bleeding edge tech was a blackboard (yes, chalk) and, occassionaly, an overhead projector.

Can anybody give me a hand or make some suggestions on a workaround for this?

regards, Richard

---

