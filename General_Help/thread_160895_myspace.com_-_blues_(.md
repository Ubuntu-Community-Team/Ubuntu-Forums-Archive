---
title: "myspace.com - blues :("
date: 2006-04-15
forum: General Help
---

### Post by gibson on 2006-04-15
Well i have finally jumped the bandwagon and made a myspace page, but when under linux i can not hear any of the music.

for example goto [http://www.myspace.com/amar_superstar](http://www.myspace.com/amar_superstar) and i cant get the sound from the little flash palyer thingy.

Now i understand it is the flash plugin playing the sound... i have flash player 7 and i have tried the site under FF and ephiphany (which i am in now... wow its is fast!) and im kinda stumped for ideas. is everyone else having a problem with it?

ps. if you have a profile add me.... i want to look really popular :-)

thanks in advance

---

### Post by Harold P on 2006-04-15
[QUOTE=gibson]Well i have finally jumped the bandwagon and made a myspace page, but when under linux i can not hear any of the music.

for example goto [http://www.myspace.com/amar_superstar](http://www.myspace.com/amar_superstar) and i cant get the sound from the little flash palyer thingy.

Now i understand it is the flash plugin playing the sound... i have flash player 7 and i have tried the site under FF and ephiphany (which i am in now... wow its is fast!) and im kinda stumped for ideas. is everyone else having a problem with it?

ps. if you have a profile add me.... i want to look really popular :-)

thanks in advance[/QUOTE]

I think you need w32 codecs, not sure though. It works for me, though. I installed anything having to do with audio/video codecs, plugins, and firefox from automatix.

Here's my myspace.

[http://myspace.com/haroldxcore](http://myspace.com/haroldxcore)

Edit: I just noticed you're the guy that helped me with my port opening topic!

---

### Post by gibson on 2006-04-15
> amar@pingu~$ dpkg -l | grep w32
ii  w32codecs                         20050412-1plf4      All binary propriatary w32 codecs

hmmm - i got all that installed though.

Just to be sure i closed my amarok etc to free up all the sound stuff, im using alsa too if that helps

---

### Post by Sef on 2006-04-15
To get it work, try this:

sudo apt-get update

sudo apt-get install alsa-oss

---

### Post by gibson on 2006-04-15
[QUOTE=Sef]To get it work, try this:

sudo apt-get update

sudo apt-get install alsa-oss[/QUOTE]


Awesome.... that got it working. Thanks a lot dude. 

Just to clarify i assume that the macromedia flash player uses oss libraries and this package just lets me use them in alsa?

Thanks again :D

hope to see some of you on myspace :)

---

### Post by Harold P on 2006-04-15
[QUOTE=gibson]Awesome.... that got it working. Thanks a lot dude. 

Just to clarify i assume that the macromedia flash player uses oss libraries and this package just lets me use them in alsa?

Thanks again :D

hope to see some of you on myspace :)[/QUOTE]


Is amar superstar you?

---

### Post by gibson on 2006-04-15
[QUOTE=Harold P]Is amar superstar you?[/QUOTE]

indeed it is :)

---

### Post by Harold P on 2006-04-15
[QUOTE=gibson]indeed it is :)[/QUOTE]

Added. Yes, I'm that 14 year old.. haha.

---

### Post by gibson on 2006-04-15
[QUOTE=Harold P]Added. Yes, I'm that 14 year old.. haha.[/QUOTE]

and accepted!! btw cool music, i saw from autumn to ashes last year.... awsome!!


In response to Saf, again thanks for your help, but i think i have discovered something else... if i load amarok, then close it, then load FF and try my page i get nothing. However, if i load konqurer then it works. Then i can close konquerer and load FF adn it will work.

I assume that amarok is not letting go of alsa until konqurer tells it to and it is not listening to FF/Epiphany.

Any ways around this?

Thanks again

---

### Post by N8MAN1068 on 2006-04-15
heh...you'd be better off off of it.
Serisouly.
Nothing like killing bandwidth waiting for some poorly formed page with tons of animated gifs, lame layout/font/background, mp3+videos, etc, then having it all crash your system.

---

### Post by pr0-t31n on 2006-04-15
sent you a friend request; im the dude with the abs!

---

### Post by Harold P on 2006-04-15
[QUOTE=N8MAN1068]heh...you'd be better off off of it.
Serisouly.
Nothing like killing bandwidth waiting for some poorly formed page with tons of animated gifs, lame layout/font/background, mp3+videos, etc, then having it all crash your system.[/QUOTE]

It hasn't done that to me. I use the greasemonkey extension for Firefox to remove custom styles on others profiles so they don't lock up my browser. Very useful.

[http://userscripts.org/scripts/show/997](http://userscripts.org/scripts/show/997)

Main reason I use it is because all the girls that attend my school use it. More comments for me! :)

---

### Post by gibson on 2006-04-15
[QUOTE=pr0-t31n]sent you a friend request; im the dude with the abs![/QUOTE]

somebody loves themself :)

I agree that myspace can be really slow and shitty, and their technology seems pretty dated, i just love it for the music though... wither that or purevolume.com

EDIT: Was just wondering what all the americans are doing up, then i looked at my clock.... 4.am!!! too much ubuntu! im off to bed.

---

