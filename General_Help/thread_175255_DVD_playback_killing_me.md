---
title: "DVD playback killing me"
date: 2006-05-13
forum: General Help
---

### Post by lorenzo111 on 2006-05-13
I have to say im new to ubuntu but not new to to linux have tried over 20 distros over the years and I must say by far this one is the best and I plan on sticking with it ok but now to my problem.

I installed ubuntu on my gateway 450SX4 labtop
P4 2.0 GHZ
512 Ram
ATI Radeon 7500 video card
DVD Rom

I have been following all the guides I have read to the tee

I did a fresh install and used the automax very nice I seleceted libdvdcss2 and all the other goodies but when I try to play a DVD on totem it opens it for a sec and then I get the popup I'm playing a encrypted movie and that i need libdvdcss but its installed already.

So I follow another guide and install Mplayer but all it does is locksup and doesnt do anything

So I installed ogle it trys to play a dvd but crashes in 10 seconds

I even downloaded libdvdcss seperately as source and installed it but still get the same error

couldnt think of anything else to do so I thought I would post and maybe get some help

after all that did another fresh install with the easy ubuntu and still get the same error

Please people help a new user stay with ubuntu I even got my wireless nic working this is my last hiccupp

---

### Post by encompass on 2006-05-13
Mine seems to do that on some dvd's.
I would try to let the disc just wait for a moment.  It takes a little to get the disc decrypted.
My wife seems to have found her own solution... just just ski9ps from totem to xine and plays it there.  I was suprised, but it worked for her.
:-D Hope that helps.

---

### Post by lorenzo111 on 2006-05-13
none of my players are recognizing my libdvdcss so should i use the automax or ubuntu the easy way?

what player are u using?

can u tell me what steps u did for your dvd playback to work I really want to get this to work

---

### Post by lorenzo111 on 2006-05-13
Update

reformatted my labtop and reinstalled it and followed the guide ubuntu official customization guide to the letter and received no errors but when trying to play a DVD with totem i get a dvd nav error saying it cant goto next block. When I use xine it says i dont have the right to play encrypted DVDS even though I installed libdvdcss just like the guide said to do. When I use Mplayer screen goes black and just hangs there. VLC wont even open my cdrom tried typing all kinds of paths to it but wont work on any of them. Now I'm at a brickwall on getting my Dvds to play any help would be appreciated because this is a major deal breaker for me if I cant watch DVDs on my labtop.

---

### Post by encompass on 2006-05-14
You got me..
can you play some dvd's and not others... have you tried un protected dvds like ones burned of your family reunion or something?
My system, ever once in a while tells me it can't play the dvd because it can't decrypt it.  I simply try again and it either works or doesn't.  At most I have tried three times.
Sorry I can't help you any further, you may want to give the output when you run xine from console and try to run the movie.

---

### Post by lorenzo111 on 2006-05-14
Update

Cant believe it thats what it was wouldnt play Bring It but plays others just fine. Thanks for the help have one more slight problem left

Mplayer wont play .asx or .mov files. What codecs do i need to download to play them?

Thanks again for all the help

---

### Post by encompass on 2006-05-14
Don't know if you tried, but automatix should get you the codecs pretty easy.  worked for me.
And great to hear we fixed your problem, sorta.

---

### Post by lorenzo111 on 2006-05-14
scared to use automax again did it this time by hand and have it up and running very well now just need to figure out what codecs i need to download for that and im set ubuntu FTW

---

### Post by lorenzo111 on 2006-05-16
/bump

---

### Post by Keith_Beef on 2006-05-20
Lorenzo, you don't mention what version of the library you have; maybe this is the problem.

I had a little bit of a problem last night, wanting to watch a DVD borrowed from the town library.

I installed Ubuntu on this computer a couple of days ago, after quite a few years of Mandr[ake|iva]. I was surprised when I got a message from Xine, something about "your government thinks you shouldn't be allowed to play a DVD that you have paid for"... ](*,) 

Just for the evening, I got round this by playing in a normal Pioneer DVD player, hooked up to my Broktree TV Tuner card, displaying through TVTime. I have this set up anyway, because some dirty and scratched DVDs I borrow just won't play on my computer, but the Pioneer player plays them (with some degradation and pixellisation of the image, or with skips). Also, I don't have a television set :D

I expected libDeCSS or similar to be there already, with the player. But after reading a bit, I get the impression that Ubuntu (and Debian generally) shies away from bundling 'controversial' or 'borderline' stuff, for fear of falling foul of the DMCA.

Anyway, I found a Debian package on the main Ogle site, at Chalmers University in Sweden; downloaded and installed both the regular and the development versions of the library and now both Ogle and Xine play fine.

sudo dpkg -i DVD_utilities/libdvdcss2_1.2.9-1_i386.deb
sudo dpkg -i DVD_utilities/libdvdcss2-dev_1.2.9-1_i386.deb


Beef.

---

