---
title: "kile's symbols toolbox doesnt work."
date: 2011-03-16
forum: General Help
---

### Post by yzarc on 2011-03-16
Hi everybody,
First of all, sorry if this is a repeated topic. I've made my research with no  success. Sorry for the poor English too.

I have ubuntu (gnome) but I prefer to use Kile as tex editor. Since maverick, the side symbols tool box stopped working.

I click, double-click ou press return but the symbol code (e.g. \cup ) is not inserted in the text. 

Does any one have the same problem? How can I fix it?

---

### Post by laurentg on 2011-04-04
Hi,

Same problem for me (Ubuntu 11.O4 + Kile): impossible to use the symbol library. Does not work with click, double click, CTRL+click, MAJ+click. It seems that there is no command associated with the symbols. 

Sorry, no solution for me till now...

lg

---

### Post by cosine352 on 2011-05-02
same problem here. Does anyone find any fix?

---

### Post by AimOn on 2011-05-03
I have this exact problem with Kile 2.0.85 on Kubuntu 11.04 (fresh install). Hover over the symbol I want to enter shows 'Command:' (followed by and empty line)...

Did anyone find a solution or maybe a hint on what might be the problem?

Cheers

---

### Post by Saladin1 on 2011-05-04
so I'm the fifth,
the problem started suddenly
reinstalling it didn't fix the problem :(

---

### Post by djdisc on 2011-05-07
... exactly the same Problem. - Ubuntu 11.04

---

### Post by joquito on 2011-05-10
I try this solution.

[https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+sourcepub/1718390/+listing-archive-extra](https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+sourcepub/1718390/+listing-archive-extra)

hope it works for you too ;)

---

### Post by NunoR on 2011-05-10
Thanks, Joquito.

It worked perfectly for me.

---

### Post by megatron3030 on 2011-05-11
Works great for me as well in 11.04.  Thanks!

---

### Post by karim.rahim on 2011-05-16
Thanks!

---

### Post by Saladin1 on 2011-05-18
Worked well  with Kile amd64 after installing the .deb file,
Thank you..

---

### Post by alexander1 on 2011-05-19
I had the same problem, and the deb didn't solve it.

But now I can hover over the symbols now and see the command. But clicking doesn't insert anything.

---

### Post by iclestu on 2011-06-02
This is a known bug guys:

[https://bugs.launchpad.net/ubuntu/+source/kile/+bug/772631](https://bugs.launchpad.net/ubuntu/+source/kile/+bug/772631)

---

### Post by mavenuparker on 2011-06-17
For i386
_[https://launchpad.net/~yofel/+archiv...+build/2489577]("https://launchpad.net/%7Eyofel/+archive/backports/+build/2489577")_

For AMD
[https://launchpad.net/~yofel/+archiv...+build/2489576]("https://launchpad.net/%7Eyofel/+archive/backports/+build/2489576")

Hope this works

---

### Post by Nandi on 2011-06-20
Try upgrading  your Kile

---

### Post by iclestu on 2011-06-20
> **Nandi said:**
> Try upgrading  your Kile

Im not sure how this is intended to help.... The issue applies to the most recent versions supplied with ubuntu. It is a known bug. A simple update/upgrade isn't going to fix it unless or until a fix is released.

mavenuparker has kindly posted links to another version not yet in the repo's. 

Simply saying 'try upgrading' isnt really of assistance. Did you read the thread before you posted?

---

### Post by rafaszola on 2011-08-03
[U]
[/U][RIGHT][LEFT]__[FONT=Book Antiqua]Joquito's solution work just fine. Try it! I am also running 11.04.[/FONT]
[/LEFT]
__[/RIGHT]

---

### Post by edantes on 2011-08-23
> **megatron3030 said:**
> Works great for me as well in 11.04.  Thanks!

Maybe I didn't look hard enough, but the symbol panel disappeared completely after I installed the launchpad patch indicated above.

I had better luck with the official sid debian release, which is no longer marked as beta:

[http://packages.debian.org/sid/amd64/kile/download](http://packages.debian.org/sid/amd64/kile/download)

(Luckily all dependencies are OK with Ubuntu 11.04 with all recommended upgrades)

Inserting the symbol into the document is working fine. I still have a problem with the tool tip you should get when placing the pointer on the symbol.  It show an almost all black rectangle, with dark gray text.  Something to do with with KDE appearance settings, I guess.

---

### Post by yzarc on 2011-08-23
> **joquito said:**
> I try this solution.

[https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+sourcepub/1718390/+listing-archive-extra](https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+sourcepub/1718390/+listing-archive-extra)

hope it works for you too ;)

it works for me too. many thanks!!

---

### Post by hypnojelly on 2011-09-20
Also did the trick for me, thanks!

---

### Post by marianob on 2011-11-30
Hello 
I don't know how to work the solution out. Could anyone give me some instructions to follow?

I'm thinking of this:
 [https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+sourcepub/1718390/+listing-archive-extra]("https://launchpad.net/~ubuntu-backports-testers/+archive/ppa/+sourcepub/1718390/+listing-archive-extra")


Thanks!

---

### Post by marianob on 2011-12-01
> **yzarc said:**
> it works for me too. many thanks!!
Could you give me some instructions to fix the Kile bug, I don' t know how to manage the information at [https://launchpad.net/~yofel/+archive/backports/+build/2489577](https://launchpad.net/~yofel/+archive/backports/+build/2489577) .
 
Thanks a lot in advance.

---

### Post by fivir on 2011-12-02
just download the last file [kile_2.1.0~svn2010122beta5-1ubuntu1~natty1~ppa1_i386.deb]("https://launchpad.net/%7Eyofel/+archive/backports/+build/2489577/+files/kile_2.1.0%7Esvn2010122beta5-1ubuntu1%7Enatty1%7Eppa1_i386.deb")         (1.4 MiB) and install it (remove the old kile version and run the downloaded file to install)

---

### Post by marianob on 2011-12-03
Thank you, I've overestimated the problem.

=)

---

