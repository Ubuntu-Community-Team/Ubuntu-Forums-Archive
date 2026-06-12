---
title: "Ok so I have no idea what I just did..."
date: 2010-07-11
forum: General Help
---

### Post by mortalapeman on 2010-07-11
This should be a good one for all the linux gurus. This is what I rememeber doing right before things went wrong.

I have been trying to write a bash script that will automatically install all the things I normally reinstall on my machine and some things I have recently wanted to install. One package in particular called vavoom. Ok so the dependecies of vavoom include cmake zlib and Allegro. zlib I downloaded and compiled from source. I was also looking at sudo -i at around the same time and tried it out. I was somehow able to login is root without using my password and thats when  I noticed something was wrong. I didn't really know how to log out as root (turns out I just needed to type logout zzz) so I just closed the terminal killing that process. At some point shortly after that I tried to open synaptic and it asked me for my password. I entered it, and it just never loaded up the gui.

I thought it might have something to do with that terminal I closed earlier so I decided to reboot my machine to clear out ant processes that weren't suppose to be running. Apparently that was a bad idea. When I logged back in I got the error message that the indicator applet has falied to start up do you want to delete? or not delete?

Also, AWN was not displaying properly, it had a gray box around all my icons and I could not load up firefox to get to the web.

I am currently on a live CD of knoppix so I should be able to fix the problem from here. I've got a external hardrive I can backup all my data to so I'm not really worried about that. I just want to figure out what I did wrong so I can fix it or atleast not repeat my mistake.

so, anyone got any ideas?

---

### Post by Ocxic on 2010-07-11
post the script that you ran.

---

### Post by mortalapeman on 2010-07-11
> **Ocxic said:**
> post the script that you ran.

I didn't run any scripts other than what was included in the tar ball for zlib. The only things I did before it got messed up were:

(after unzipping the zlib tar ball and going inside that directory)

```
./configure

sudo make install
```and

```

sudo -i
```If you want the site i got the zlib tar ball from it's [www.zlib.net]("http://www.zlib.net")

After running sudo -i and not being asked for my pass word i cosed the terminal. Before all this i also installed cmake and allegro-dev from the ubuntu repositories.

---

