---
title: "Torrent question, terminology"
date: 2009-11-02
forum: General Help
---

### Post by MickS on 2009-11-02
I'm using Ktorrent to seed Karmic, when I have a look at it I see.
Seeders = 0(681) and Leechers = 12(166) what do the numbers in brackets mean? I would be grateful if some one could enlighten me.

Mick

---

### Post by scouser73 on 2009-11-02
> **MickS said:**
> I'm using Ktorrent to seed Karmic, when I have a look at it I see.
Seeders = 0(681) and Leechers = 12(166) what do the numbers in brackets mean? I would be grateful if some one could enlighten me.

Mick

Seeders means the amout of people that are hosting the torrent file & leechers are the people that are downloading.

---

### Post by NickJones on 2009-11-02
I believe the ones in the bracket are ones that are not connected to you.

---

### Post by sensay on 2009-11-02
The numbers in brackets are the size of the swarm. When downloading, ideally, you want to be connected to more seeds in the swarm than leechers, when uploading/seeding you want to be connected to many leechers in the swarm. It should also be possible to adjust your settings to allow for more (or less) connected peers. This is useful if you have a fast/slow connection and can adjust accordingly.

---

### Post by MickS on 2009-11-02
Thanks for the info, I was just curious I only ever use torrents for Ubuntu upgrades. I like to seed for a while as my little way of giving something back.


Mick

---

### Post by captain_conrad on 2009-12-25
hi there

I also seek clarity on this terminology please

Who is seeding who and who is downloading from who? I am very confused...

I have used Ktorrent (running ubuntu 9.04 jaunty) and its workin like a dream, I just have no idea what this seed and leech things are. I hope nobody is downloading or leeching anything off my computer. Or do I have the wrong end of the stick here?

Thank you, these forums are always very helpfull!

CC

---

### Post by lloyd_b on 2009-12-25
> **captain_conrad said:**
> hi there

I also seek clarity on this terminology please

Who is seeding who and who is downloading from who? I am very confused...

I have used Ktorrent (running ubuntu 9.04 jaunty) and its workin like a dream, I just have no idea what this seed and leech things are. I hope nobody is downloading or leeching anything off my computer. Or do I have the wrong end of the stick here?

Thank you, these forums are always very helpfull!

CC

With Bittorrent, you are potentially both downloading (receiving the file from others) and uploading (sending the file to others) at the same time.

A "seeder" is somebody who has the complete torrent, and is sending it to others (leechers) without receiving anything.

A "leecher" is somebody who does not have the complete torrent, is downloading from others (seeders and/or leechers), and may or may not be uploading to other leechers.


Lloyd B.

---

### Post by Ahadiel on 2009-12-25
> **captain_conrad said:**
> hi there

I also seek clarity on this terminology please

Who is seeding who and who is downloading from who? I am very confused...

I have used Ktorrent (running ubuntu 9.04 jaunty) and its workin like a dream, I just have no idea what this seed and leech things are. I hope nobody is downloading or leeching anything off my computer. Or do I have the wrong end of the stick here?

Thank you, these forums are always very helpfull!

CC
When you download using a torrent you are leeching from all the available seeders/leechers in the swarm (you are downloading from them).

When you finish downloading you are then seeding to whomever is trying to download the torrent (they are downloading from you).

You are not obligated to seed, but as you can see seeders are essential to the whole bittorrent process.

---

### Post by captain_conrad on 2009-12-26
ah thanks guys! like I said, these forums are always helpfull!

Well if leechers can download from me, will this impact my internet bandwidth?
I can see how this whole thing fits nicely into the ubuntu feeling of sharing, which is great! But I don´t want thousands of people downloading from me and eating large megabytes of bandwidth when all I have ever downloaded myself is a little 5mb file, i mean there shoud be some kind of balance. Am I thinking correctly or do I once again have the wrong end of the stick?

Thanks for all the help!

---

### Post by SuperSonic4 on 2009-12-26
> **captain_conrad said:**
> ah thanks guys! like I said, these forums are always helpfull!

Well if leechers can download from me, will this impact my internet bandwidth?
I can see how this whole thing fits nicely into the ubuntu feeling of sharing, which is great! But I don´t want thousands of people downloading from me and eating large megabytes of bandwidth when all I have ever downloaded myself is a little 5mb file, i mean there shoud be some kind of balance. Am I thinking correctly or do I once again have the wrong end of the stick?

Thanks for all the help!

By uploading it either as a seeder or a leecher you will be using some bandwidth but you can only upload what you've got already. If you are worried about bandwidth ktorrent has a cap on upload speed and a bandwidth scheduler for the day

---

### Post by chewearn on 2009-12-26
> **captain_conrad said:**
> ah thanks guys! like I said, these forums are always helpfull!

Well if leechers can download from me, will this impact my internet bandwidth?
I can see how this whole thing fits nicely into the ubuntu feeling of sharing, which is great! But I don´t want thousands of people downloading from me and eating large megabytes of bandwidth when all I have ever downloaded myself is a little 5mb file, i mean there shoud be some kind of balance. Am I thinking correctly or do I once again have the wrong end of the stick?

Thanks for all the help!

There are two parts to this question.

1. bandwidth consumption, as in speed of upload/download.
Most torrent clients allow you to specify how much of your bandwidth to consume for all torrents, or individual torrents.  This will prevent the torrent traffic from overwhelming your entire connection.  For instance, if your internet connection is 1Mbps/256kbps download/upload, you could specify 800kbps/200kbps limit.  Therefore, there is a slight "gap" in the pipe you could use for other things (http, mail, IM, etc).

2. total consumption size
The seeding ratio is the total amount you download vs upload.  For instance, you are downloading a 5MB file.  Upon completion, you continue to leave the file in the torrent client and it seed to 10MB.  Therefore, your seeding ratio is 10MB/5MB = 2.  While downloading the file (1 copy), you have effectively give back two copies of the file into the torrent swarm.

Both parts (how much network speed is consumed, and how much size is used) can be specified in the torrent clients.

---

### Post by lloyd_b on 2009-12-26
> **chewearn said:**
> There are two parts to this question.

1. bandwidth consumption, as in speed of upload/download.
Most torrent clients allow you to specify how much of your bandwidth to consume for all torrents, or individual torrents.  This will prevent the torrent traffic from overwhelming your entire connection.  For instance, if your internet connection is 1Mbps/256kbps download/upload, you could specify 800kbps/200kbps limit.  Therefore, there is a slight "gap" in the pipe you could use for other things (http, mail, IM, etc).


One point to be aware of - due to the design of the TCP protocol, if you max out your bandwidth in one direction, it will tend to throttle your bandwidth in the other direction as well.

While downloading/uploading heavily, it's best to restrict your bandwidth to 90% in both directions, to prevent this problem.

(For the curious - the problem lies with the fact that you are required to send an ACK or acknowledgement packet for every packet you receive, and receive one for every packet you send.  If you've maxed out your upstream or downstream, then these ACK packets get caught in a "traffic jam" on your network connection.  Systems use these ACK packets to determine when to send the next packet, so any bottlenecking of these packets will act to restrict traffic in the other direction).

Lloyd B.

---

### Post by captain_conrad on 2010-02-08
Very kewl, Thank you!, I am learning! :popcorn:

Ok now I have a few torrents I downloaded and there is just 0(0) seeders and 0(0) leechers. So the thing just sits in my ktorrent and its status is ¨stalled¨. What does this mean? Must I just patiently wait forever, or must I delete it and go download another torrent of the same file untill I find one that has active seeders and leechers?

Another question. If there is a big ¨swarm¨ e.g 75(100) of seeders, will I be able to download/access the file quicker/better than a small ¨swarm¨ e.g 1(2) ?

And if you are seeding, what will be the difference between there being eg. 75 leechers and e.g 2 leechers?
Will 75 leechers ¨leech¨ more bandwidth from you the seeder because there are more leechers, or will one leecher leech more as there is only you seeding. Or does it depend on the amount of seeders seeding the same file with you?

And what does the number in the bracket and the number outside the bracket mean?

Thanks for the help guys, Im digging this torrent thing :D

---

### Post by lloyd_b on 2010-02-08
> **captain_conrad said:**
> Very kewl, Thank you!, I am learning! :popcorn:

Ok now I have a few torrents I downloaded and there is just 0(0) seeders and 0(0) leechers. So the thing just sits in my ktorrent and its status is ¨stalled¨. What does this mean? Must I just patiently wait forever, or must I delete it and go download another torrent of the same file untill I find one that has active seeders and leechers?

Another question. If there is a big ¨swarm¨ e.g 75(100) of seeders, will I be able to download/access the file quicker/better than a small ¨swarm¨ e.g 1(2) ?

And if you are seeding, what will be the difference between there being eg. 75 leechers and e.g 2 leechers?
Will 75 leechers ¨leech¨ more bandwidth from you the seeder because there are more leechers, or will one leecher leech more as there is only you seeding. Or does it depend on the amount of seeders seeding the same file with you?

And what does the number in the bracket and the number outside the bracket mean?

Thanks for the help guys, Im digging this torrent thing :D

1.  0(0) for seeders/leechers means it's a dead torrent.  You can wait forever, but unless someone connects to provide the file, you'll never receive anything.  So in that case you need to look for another torrent (or another tracker for the same torrent, with active sources).

2.  Yes.  The more sources for the torrent, the better the chance that you'll be able to download at the maximum speed your network connection supports.  But note that a large number of leeches may also help increase the speed you receive the file, as leeches are sending parts of the file to others while receiving other parts.  You only need to get from the seeders those portions of the file that haven't already been downloaded by other leeches.

  For example, say there is one seeder, and two other leeches.  Leech one has downloaded piece 1 from the seeder already, while leech 2 has downloaded piece 2.  You can then download piece 1 from leech 1, piece 2 from leech 2, and piece 3 from the seeder, all at the same time.  Once you have completely downloaded a piece, then you can start providing it to others as well. A "seeder" is just someone who has *all* of the pieces.

3.  Most torrent programs split the bandwidth between all recipients.  So if you're seeding to 2 leechers, each will get 50% of your available "upstream" bandwidth, while with 10 leechers, each will get 10%.  There are modifiers on this, though - for instance, if the leecher has a very slow connection, then he'll only get as much bandwidth as his connection supports, which frees up more bandwidth for the others.  Note that most torrent programs also allow you to set the maximum bandwidth that the program is allowed to use, so the max available to the torrent may be less than the maximum of your network connection.

4.  The number in parentheses is the number of sources (seeders or leechers) in the swarm.  The number outside is the number of sources to which you are actually connected.  So "5(10)" means there are 10 possible sources, and you are connected to 5 of them.

Lloyd B.

---

### Post by captain_conrad on 2010-02-09
very helpfull thank you!\\:D/

> 4. The number in parentheses is the number of sources (seeders or leechers) in the swarm. The number outside is the number of sources to which you are actually connected. So "5(10)" means there are 10 possible sources, and you are connected to 5 of them.


Does the same count for leechers? in other words 5(10) means there are 10 leeches and 5 of them are connected to me?

In the ktorrent program, what are the buttons ¨Manual Announce¨ and ¨Scrape¨ for?

You suggested looking for another tracker for the same torrent, how do I go about doing this?
Im downloading this torrent and I have already completed 144Mb out of 700Mb, but it is showing 0(0) seeders and 3(14) leechers, and a status of ¨stalled¨. Now i don´t want that 144mb already downloaded to just be a waste.
The torrent consistes of 6 folders totalling 7.3Gb, 4 being movies and 2 folders being two series´. I am only downloading one of the movies within this torrent file.
Your advice? Cut my losses and find another torrent? Or stick it out another week or two hoping somebody will seed, whilst everybody leeches from me?

once again thank you, this thread is very helpfull!

---

### Post by lloyd_b on 2010-02-09
Yes - Leeches 5(10) means there are 10 leeches in the swarm, and 5 of them are currently connected to you (either sending you pieces, receiving pieces from you, or both).

"Announcing" is a process where you contact the tracker, and tell it to add you to the swarm (if you aren't already in it).  This is done periodically, I assume because the tracker prunes its list of peers after a while.

"Scraping" means contacting the tracker, and getting information about the swarm (number of seeders, number of leeches, etc), but NOT adding you to the swarm.

As for that dead torrent, you can go to any torrent search engine (Google for "Torrent search") and see how many other listings you can find for that same thing.  Though it may or may not be the *same* torrent you find - it's hard to tell whether a given torrent file is for the same torrent as another without actually starting it.  I'm not familiar with Ktorrent, but most torrent software will just merge the tracker lists if you open another torrent file for the same content.

In a case of 4 movies and 2 series, I would cut my losses, and search for *just* the thing I wanted to download.  Large "everyting about this subject" torrents are less likely to be active than smaller "just this particular thing" torrents (unless you're dealing with unusual, hard-to-find content). 

Lloyd B.

---

### Post by captain_conrad on 2010-02-10
FANTASTIC:D

With regards to the large 7Gb ¨Everything on this subject file¨ that is a dead torrent, you are quite correct. I have found the file specifically only that file I am looking for, and that file has a seeder swarm of 15(34), whereas the large file containing 4 movies and 2 series has 0(0) seeders and 4(9) leeches. So I cut my losses and ditched the already downloaded 144mb, and the specific file torrent itself is downloading very nicely.

Thank you for all your help!=D>

---

