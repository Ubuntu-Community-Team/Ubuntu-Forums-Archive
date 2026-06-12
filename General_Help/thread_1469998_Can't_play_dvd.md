---
title: "Can't play dvd"
date: 2010-05-02
forum: General Help
---

### Post by Smart Viking on 2010-05-02
Hi all, i just rented a movie, and i can't play it.

I get to the menu, but when i press "play moves" the media player say "Could not read from resource."

And when i try vlc, it doesn't do anything, it just doesn't play(after i press"play movie".

EDIT: And in Mplayer it says "seek failed", even before i get to the menus.

---

### Post by coffeecat on 2010-05-02
To play encrypted commercial DVDs, you need the library libdvdcss2. Go to...

[http://www.medibuntu.org/](http://www.medibuntu.org/)

... and follow the instructions to enable the Medibuntu repository and then install libdvdcss2. Then you should be OK. Check, also, that you've got libdvdread4 installed as well.

---

### Post by Guitar John on 2010-05-02
Could be a bad disc.  Do you have another player that it will play on?

---

### Post by Revolutionary101 on 2010-05-02
Try downloading the libdvdcss2 package by going to this page.

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

Select your version of Ubuntu and then find the libdvdcss2 package. Once you have found it just click on the type of processor you have and download it. After downloading it just install it and your DVDs should play fine.

---

### Post by Smart Viking on 2010-05-02
Hi everyone, thank you for the replies!

And you was right, i just did this:

[http://www.zolved.com/synapse/view_content/28220/How_to_play_DVDs_on_Ubuntu](http://www.zolved.com/synapse/view_content/28220/How_to_play_DVDs_on_Ubuntu)

And i diddn't think it worked since it diddnt. but i restarted the machine and then it worked! Assum, i have pizza too i'm glad i can watch movies now. :):popcorn:

---

### Post by coffeecat on 2010-05-02
> **Smart Viking said:**
> And you was right, i just did this:

[http://www.zolved.com/synapse/view_content/28220/How_to_play_DVDs_on_Ubuntu](http://www.zolved.com/synapse/view_content/28220/How_to_play_DVDs_on_Ubuntu)


To anyone coming across this thread, **do not use that link.** It is hopelessly out of date. Purging totem-gstreamer and installing totem-xine had its advantages around the Feisty Fawn era, but is unnecessary now.

Just be aware that there is a lot of obsolete and dubious advice to be found on the internet.

---

### Post by Smart Viking on 2010-05-02
Ur maybe right about that too, i could only play one of the dvd's, the other one still said "Could not read from resource."

I'm going to bed now and i can watch the other movie tomorrow, but it doesn't really solv this thread. Also, it seemed like i had to boot up, with the dvd in the player, and after i booted up it would work, but only for one of them.

---

### Post by Algus on 2010-05-02
Hey I was browsing the forums for an unrelated problem and realized this was something I needed to fix as well.  Thanks to everyone who provided help on this matter as it worked for me as well!

---

### Post by juliomeza on 2010-05-03
There is a problem with the server right now, I will try later on..
I just bought Avatar and I can not watched :(
Thanks for all your effort :)

---

