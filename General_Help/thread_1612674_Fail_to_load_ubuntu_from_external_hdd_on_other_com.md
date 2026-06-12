---
title: "Fail to load ubuntu from external hdd on other computer"
date: 2010-11-03
forum: General Help
---

### Post by Floven de Sorezé Stockeir on 2010-11-03
Hello everyone,

thank you for opening my thread, I hope someone here can offer a solution to my problem.

First off I would like to stress the fact that I'm totally new to Ubuntu and thus very possibly am overlooking some very obvious solutions.

Secondly I would like to apologize for possible spelling/grammar errors since english isn't my native language.

_Situation Sketch:_
Today I installed ubuntu (10.10) on my external HDD. I did this so I can keep Vista on my internal disk but also so I can take my external HDD with me wherever I want to go, plug it in any computer and boot ubuntu from there.

This setup works fine on my laptop which I used to install ubuntu on my external HDD. When I start my laptop I choose to boot from my external disk, after which I succesfully log on in Ubuntu. If I don't want to boot in Ubuntu I don't enter bios and go straight to vista.

_Problem:_
My problem is that when I unplug my external HDD and plug it onto another computer different from the one I used to set this all up, I can set boot order to boot from external HDD, and bootloader appears, but I don't get into Ubuntu. On the 2 different computers I have 2 different problematic results:
1) after grub bootloader my screen remains black for as long as I've yet tried (+- 15 minutes)

or

2) after grub bootloader I don't get the usual log on window but instead a command line asking me for username and password. When I give those I remain in command line interface, nothing much changes. 

EDIT: I found a youtube video where pretty much the same happens as for me in 2)
[http://www.youtube.com/watch?v=OADFZ1mocCY](http://www.youtube.com/watch?v=OADFZ1mocCY)

[U]Possible causes:
[/U]As I said I have virtually no experience with Ubuntu, nor am I really technically skilled. My 'possible causes' are thus nothing more than wild guesses. 

- I fear I might have misplaced the grub bootloader. Instead of installing it on my external HDD I might have placed it on my laptop's internal HDD, thus explaining why I can only succesfully log on on the laptop I used for the installation. 

I'm not very sure this really is the cause since Grub Bootloader *does *appear on the other computers

(if grub bootloader indeed looks like this - **image from google, not from my setup**): [IMG]http://kyleabaker.com/wp-content/uploads/2010/07/grub-boot-loader.jpg[/IMG]


- Maybe Ubuntu doesn't recognise the hardware on the other computers? Though this seems very unlikely. Indeed, yesterday I already installed Ubuntu on my external HDD *with another, desktop (not laptop) computer*. This version of Ubuntu worked on the other computers when booted from my external HDD. Though this time I remember I put the bootloader correctly.
(I removed this installation since I was not happy with the allocated partition space)




I hope I have given all needed information. If not I would be glad to add.

Thank you very much,

Floven de Sorezé Stockeir

---

### Post by alphaamanitin on 2010-11-03
> **Floven de Sorezé Stockeir said:**
> with me wherever I want to go, plug it in any computer and boot ubuntu from there.

Floven de Sorezé Stockeir


That right there is your problem.  The thing is your install of ubuntu on that external hard drive has all the settings of it, like drivers for the wireless card, cd/dvd drive, monitor, etc, are ALL the drivers for the computer it was originally installed on.  If you took it to a computer with the exact same hardware it *might* work.  I would say what you are looking for is more of a liveCD with permanance.  I am not sure how to set this up, hopefully more people will reply to your thread.  

Also, I have heard about versions that scan the computer before the OS boots up and applies generic drivers so that it can boot from multiple computers.  Not sure how true that is, or how difficult to set up it would be.  

Bottom line, it will be extremely hard for you to do what you want to do, sorry.

AlphaA

---

### Post by Floven de Sorezé Stockeir on 2010-11-03
Thank you very much alphaamanitin, 

indeed your explanation seems to fit what I experience. Just a question though: how did it manage to work yesterday then, when I installed ubuntu on my external HDD and afterwards managed to boot without problems on other computers?

I guess the answer will be that yesterday I didn't yet upgrade drivers & installed so much extra software before trying on other computers. Today I did...

Well, I think I will google these generic drivers and see if those work then.

Thank you very much.

---

