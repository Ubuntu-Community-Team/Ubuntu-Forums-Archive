---
title: "avi to dvd???"
date: 2006-02-14
forum: General Help
---

### Post by neoroses on 2006-02-14
Hi guys - can some one please tell me if theres a not so hard way of encoding avi/divx/xvid files to dvd and burning them so they will play on my dvd player? 

im not a compleat n00b so a lil bit of technical mubo jumbo i can cope with but i would just like to know the simplest way. thanks 

neorses :)

---

### Post by niviche on 2006-02-14
I don't know if it is in the repositories, but this apps seems to be what you are looking for:
[http://www.kde-apps.org/content/show.php?content=27528](http://www.kde-apps.org/content/show.php?content=27528)

---

### Post by neoroses on 2006-02-14
thank you very much but will this enable me to convert form avi to dvd as it says it can do it with compatable MPEG files? 

thanks for the speedy repliy :D

---

### Post by taurus on 2006-02-14
What you are looking for is called tovid...  ;)

---

### Post by neoroses on 2006-02-14
thank you :D

---

### Post by siucdude on 2006-03-05
or you can try this program its easy and new DeVeDe

thanks

---

### Post by sjoseph on 2006-03-05
thanks for this post, i am trying the same thing. i've tried to install tovid, but it asks for root password and it's not accepting my admin password to install.

---

### Post by Didjit on 2006-03-05
[quote=siucdude]or you can try this program its easy and new DeVeDe

thanks[/quote]

What repo is this located in? I cannot seem to find package with devede

---

### Post by taurus on 2006-03-05
[QUOTE=Didjit]What repo is this located in? I cannot seem to find package with devede[/QUOTE]
You have to download it and install it yourself.  Fire up firefox and type this URL in, [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html).  Scroll down to the bottom and lick Download.  After downloading it, type (from a terminal),

```

tar xvjf devede13.tar.bz2
cd devede
sudo ./install.sh
/usr/bin/devede.py &

```

Or you can access it from Applications -> Sound & Video -> DeVeDe.

---

### Post by Didjit on 2006-03-05
Cool, thanks.

---

### Post by jackwhite on 2006-03-05
anyone know of a program which will allow you to convert avi to dvd and add in a subtitles file too?

---

### Post by siucdude on 2006-03-05
you need avidemux for subtitles and it does convert avi to dvd.  its also a nice pro.

---

### Post by siucdude on 2006-03-05
its also in this repo.  I don't know if you guys ever heard of this [http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

just add the repos and you should have a uptodate avidemux and ffmpeg and devede

thanks

ok sorry i need to edit this post.  

go to download then debian and then you will see the repos in there.  pick the one you want.  i have placed all of them in mine but its your call.  stable unstable.....and so on.

thanks

---

### Post by jtpratt on 2006-03-16
I have tried DeVeDe and it locks up every time I try to add a video.  I've had many problems and some successes converting video.

Try my Ubuntu guide for converting video:
[http://smorgasbord.net/convert_video_linux]("http://smorgasbord.net/convert_video_linux")

It's a work in progress, but I've been updating and adding new information every day for any new fixes or easier ways I've found.

Hope that helps.

---

### Post by vector on 2006-03-26
ok jtpratt i tied your link and almost got it to work.
i converted the avi to mpg using ffmpeg
i then
$ dvdauthor -o dvd_ready movie1.mpg
$ dvdauthor -o dvd_ready movie2.mpg
$ dvdauthor -o dvd_ready -T
#-dvd-video is the format, -o is name of output file, dvd_ready is source dir
$ mkisofs -dvd-video -o dvd.iso dvd_ready
then used gnomebaker to make the dvd from iso
the first movie ran on my dvd player
but i had no menu and no way to get to the second movie
the dvd player seem to indicate there are two titles on the disc but I cant get to the other one
in dvd_ready i can cetainly see both movies

---

### Post by bionnaki on 2006-03-26
tovid is what you want
install tovid-gui as well

---

### Post by vector on 2006-03-26
hmm ok ill give it a go and dont read me wrong, Im trying to give linux a good go here but as a beginner Im really getting a little tired of this try this try this try this flavour. I would prefer someone at the top of the linux/ubuntu tree would assemble a known working/best way to do things .
](*,)  cause my head is beginning to hurt :) 
I followed the instructions to the letter , it couldnt be any simpler, I dont mind the cli stuff in a lot of ways its easier, but you do exactly what it says and then nup it dont work :???: 
I feel better now .. sorry :rolleyes:

---

### Post by vector on 2006-03-26
ooh BTW i took the dvd to my mums and guess what it played the second movie and not the first. which was a savoiur cause at least she got to see the one of her grandkid riding her first bicycle. So both movies are on the dvd and both can be got at.. but we just cant seem to work out how or why we cant menu the titles or whatever.

this could probably be another post but here goes.
I read tha tyou can use xine to test 
"""Test the new menus in xine before burning:
xine dvd:/full/path/to/DVD/VIDEO_TS/
"""
i looked everywhere to try and work out how to apt-get install xine???

I have totem, I have mplayer please someone sort me out......

I tried to get mplayer and totem to play the video_TS but all it wanted to do was go one level more and play each vob individually. at least if I could test the menu system b4 burnign id save on coasters.. but i can t figure out how to install xine.

---

### Post by vector on 2006-03-26
ok I just looked at a comercial dvd and its structure looks very similar
in the video_ts dir it has sets of three files which look associated. the nn number just increments
vts_nn.ifo vts_??.bup and vts_nn.vob just like mine
however it also has 
video_ts.bup video_ts.ifo and video_ts.vob
where mine has these except video_ts.vob...tell me thats all thats missing?
Q how do i create a video_ts.vob and what is it and why didnt dvdauthor do it for me..as per the link above said.:-k

---

### Post by vector on 2006-03-26
this is not a full solution but it wors in case any one else follows this thread.
I found this link helpfull
[http://mightylegends.zapto.org/dvd/dvdauthor_howto.php](http://mightylegends.zapto.org/dvd/dvdauthor_howto.php)
i jumped down to down to 
Authoring with no menus 
cut na pasted the xml script as its shown then modified the .mpg files to match mine.
and followed the dvdauthor -x dvdauthor.xml

i have no menus but it looks like the dvd will at least play the movies one after the other

bed time

---

### Post by halitech on 2006-03-26
I've used jtpratts method on numerous movies since I installed Ubuntu a week or so ago and other then being slow on this system (HP cel 1.0 with 256meg RAM) it works great as long as you do every step in order. Even if the movie is in mpg format, will still need to do step 1 and convert it.

---

### Post by vector on 2006-03-26
great halitech and thats why I post. In the hope someone will look at what Ive done, ask me some questions and things to check and let me and thus the world know where and what and why Mine went wrong. :D

---

### Post by halitech on 2006-03-26
I'm still new to this so this may or not work. I usually just go 1 movie per dvd but there is a way of joining them using the cat command. check this thread for more info

[http://ubuntuforums.org/showthread.php?t=85718&highlight=join+movie]("http://ubuntuforums.org/showthread.php?t=85718&highlight=join+movie")

---

### Post by terranz on 2006-03-26
[QUOTE=sjoseph]thanks for this post, i am trying the same thing. i've tried to install tovid, but it asks for root password and it's not accepting my admin password to install.[/QUOTE]

If you search the forums for enable root password then you'll have one soon that works.

I've been looking for something like this.

---

### Post by jeremy on 2006-03-31
[QUOTE=taurus]..and lick Download...[/QUOTE]
Tried it and all I got was a wet screen!

---

