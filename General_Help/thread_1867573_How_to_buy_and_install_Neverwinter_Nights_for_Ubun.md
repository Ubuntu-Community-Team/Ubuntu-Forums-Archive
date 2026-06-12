---
title: "How to buy and install Neverwinter Nights for Ubuntu"
date: 2011-10-23
forum: General Help
---

### Post by horusofoz on 2011-10-23
I love Ubuntu. Right now I'm trying to build a demo laptop out of of my HP Pavilion DV5-1108AX. I've upgraded it to 4GB RAM being a couple years old and have Ubuntu 11.10 stock installed.

One of the things I know I will need to being able to demonstrate for my IT Support colleagues is some good games. I've installed a couple games from the Ubuntu Software Centre but also want to demonstrate that it does offer compatibility for games that they'll recognise.

The one I decided on, partially because I want to play it, is Neverwinter Nights as investigation shows it has excellent native support for Ubuntu. However I haven't been able to find a way to purchase the Linux version of the game nor simple to understand instructions on how to install (It's a Windows based environment that we support so yes we need simple instructions :p).

Can anyone please provide advice? :popcorn:

---

### Post by cozumel on 2011-10-23
Hi,

I was actually thinking about installing on Ubunutu as I have two copies of the game (lost the original key then found it lol).  I'd drop one of them to you but I'm thousands of miles away in the UK lol :P

Just checked online and you can still by boxed set of Neverwinter Nights from large reputable resellers including [GOG.com]("http://www.gog.com/en/catalogue#all_genres/search/neverwinter nights/")

Bioware actually made a linux client :) so that it runs natively on Linux.  Unfortunately their Neverwinter forums were hacked (earlier this year I think) so I can't find a way of getting the Bioware Linux installation guide. :(

However, someone made [this blogpost]("http://robotbutler.org/article/13") last year.  It appears contains the working download links to Bioware for their linux client resources and binaries.  The blog also includes vague instructions for installation.

All the other posts I found via google using search terms "neverwinter nights linux" are ancient or link you to the now dead Bioware installation guide.

If you are successful, please could you let me know back here.  I am noob you see and would be good if you could post a kind of walk-through install guide for the ignorant :D

---

### Post by horusofoz on 2011-10-25
Thank you for the info.

I just bought a copy of Neverwinter Nights Deluxe Edition which includes the expansions. 

Once received I'll have a try and report back my progress.

---

### Post by madshib on 2011-12-20
Well, this is my first post in the forums so I hope it's helpful.

I was scrounging the linux gamer sites and came across this video on youtube 
[http://www.youtube.com/watch?v=YQp8VFK8nAU](http://www.youtube.com/watch?v=YQp8VFK8nAU)

In the description it directs you to a page with downloads for installers with updates in several languages. Found here...

[http://liflg.org/?catid=6&gameid=65](http://liflg.org/?catid=6&gameid=65)

Now, I just purchased the game from amazon for 20 bucks(Diamond Edition) and it it doesn't say anywhere on the box or in the documentation that it is linux compatible. However, as soon as I popped the dvd into my minty laptop(Katya 11) and opened the file manager, VOILA!!! Datalinux.zip file right there.

So I'm going to give this a shot and see if it works. I'll report back if I have any success. If anyone else uses these tools and has any luck, please let us know!

Fingers crossed!

---

### Post by madshib on 2011-12-22
I feel foolish now....

Go here---->[http://********************/forum/Neverwinter-Nights-1/NwN-1-Technical-Support-Self-help-for-all-versions-and-expansions/Linux-Install-Diamond-Edition--169-Update--NWMovies-4643217-1.html](http://********************/forum/Neverwinter-Nights-1/NwN-1-Technical-Support-Self-help-for-all-versions-and-expansions/Linux-Install-Diamond-Edition--169-Update--NWMovies-4643217-1.html)

(http:// social . bioware . com /forum/Neverwinter-Nights-1/NwN-1-Technical-Support-Self-help-for-all-versions-and-expansions/Linux-Install-Diamond-Edition--169-Update--NWMovies-4643217-1.html)

It works, but I'm still having issues getting the movies to work...

It's giving me the error

sed: -e expression #1, char 1: unknown command: `?'

upon entering

sed -i~nwmovies '?|?./nwmain|iexport LD_PRELOAD=./nwmovies.so' nwn

for the startup file edit to access the movies.
Yeah, total noob here.

---

