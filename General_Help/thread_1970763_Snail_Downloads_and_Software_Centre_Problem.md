---
title: "Snail Downloads and Software Centre Problem"
date: 2012-05-01
forum: General Help
---

### Post by ken38 on 2012-05-01
I have two problems which occurred about the same time - I don't know if they're connected. I'm running Ubuntu 11.10 on desktop.

1] Downloading programs eg via Software Centre or on regular ubuntu security updates has been a dawdle till the end of last week. Downloading has been at about 1mb per 10 secs. Suddenly last week it dropped to 15kb per sec, and even 7kb. An Update Manager download took over an hour for 29mb. I've tried changing the mirror, but no good. I can't see a reason for the sudden drop. My computer innards are pretty well up to date having been put together during 2011.

2] Using Software Centre I've always been able to see details of every program available. Now, when selected to view, most of them say "Available from the 'universe' source. I've tried the ***use this source*** button and have been asked to authenticate "to change software repository settings". Authenticating results in the button greying out and nothing else. When I check in Software Sources, Main, Universe, Restricted and Mutliverse boxes are all ticked.

Any advice out there? Anyone else met these two problems? Thanks in advance.

Ken

---

### Post by cortman on 2012-05-01
1) That immediately makes me think mirrors, but you mention that you've tried changing them. Is the rest of your internet connection no good as well? Try a [speedtest.]("http://www.speedtest.net/")

2) Run

```
cat /etc/apt/sources.list
```

in a terminal, and post back the full results. It could be you simply need to run

```
sudo apt-get update
```

---

### Post by ken38 on 2012-05-01
Thanks for replying Cortman.

Info as follows:  Speedtest:   download 0.96Mbps     upload 0.61Mbps
Normal internet works fine.

                        Did apt-get update. All OK with Software Centre; took 40 mins, though. But thanks for that.

Here's what I get on the other terminal input:
                    cat etc/apt/sources.list
                    cat: etc/apt/sources.list  no such file or directory

This is the second time I input. The first time there was a whole list, but I came out of the terminal so that I could do the other things before pasting the sources.list stuff to you.
Not sure what's happened.

Download speed still slow. I tried a 2,446Kb program and it took about 1.5 minutes.
Any more ideas. Thanks so far.

---

### Post by cortman on 2012-05-01
You typed the cat command wrong, forgot the first forward slash. But if apt-get update ran fine, there's really no point in running the cat command.
The only thing  I can suggest is play around with switching mirrors some more.

---

### Post by grahammechanical on 2012-05-01
Since the announcement of the release of 12.04 downloads even to update the software package lists were at a snail's pace up until just now when things got a bit faster.

I found this link from one of the stickies interesting.

[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")

Regards.

---

### Post by ken38 on 2012-05-02
Just to say thanks, especially to you Cortman. The Software Centre is all in order now, and when I tried downloading this morning, all was back to normal. As I haven't spotted any little green - or other colour- aliens hovering round the happy home, I suppose I'll never know what happened for a week.

Anyway consider this problem solved and closed.

---

### Post by jerrrys on 2012-05-02
[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mark+thread+solved&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mark+thread+solved&sa=Search&cof=FORID:9)

hay cortman :)

---

### Post by cortman on 2012-05-02
> **ken38 said:**
> Just to say thanks, especially to you Cortman. The Software Centre is all in order now, and when I tried downloading this morning, all was back to normal. As I haven't spotted any little green - or other colour- aliens hovering round the happy home, I suppose I'll never know what happened for a week.

Anyway consider this problem solved and closed.

Your quite welcome Ken38. Always glad to help. :)

> **jerrrys said:**
> [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mark+thread+solved&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=mark+thread+solved&sa=Search&cof=FORID:9)

hay cortman :)

jerrrys- behave. :)

---

